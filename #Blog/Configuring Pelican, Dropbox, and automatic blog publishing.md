# Configuring Pelican, Dropbox, and automatic blog publishing

_Captured: 2015-11-02 at 15:26 from [code.zoia.org](http://code.zoia.org/2014/02/25/pelican-dropbox-automatic-blog-regeneration/)_

In this post I will explain how I set up [Pelican](http:docs.getpelican.com) on a Linux (Ubuntu) server to mantain multiple blogs, using Dropbox for file synchronization, `watcher` to detect changes in the blog's content and regenerate it , and Apache to serve the resulting files.

  * The blogs's content will reside in a shared Dropbox folder. This is where posts are written in Markdown format (or .rst if you prefer).
  * Pelican template (themes) files will also reside in this Dropbox folder, so you can modifiy your blog's theme if needed without logging into your web server.
  * Pelican will run on your webserver, not on your local machine. (Don't need to call Pelican from your command line anymore.) This way, you can publish content from wherever you have access to your Dropbox account and a text editor. Pelican will only launch when there is new content to be published, thus minimizing your server's load.
  * Each blog will have custom its own `pelicanconf.py` and `publishconf.py` files. 
  * A simple bash script for each blog will call `pelican` with the appropiate configuration files, input and output directories.
  * `watcher`, a Python utility which uses the `inotify` interface, will monitor this shared folder for changes. (The difference between `watcher` and other similar utilities like `incron` is that `watcher` can detect changes in subdirectories, a trick `incron` cannot do directly.)

### Install Pelican

(I assume you have `virtualenv` and `virtualenvwrapper` installed. If not, you can find information on how to do it [here](http://stackoverflow.com/questions/4324558/whats-the-proper-way-to-install-pip-virtualenv-and-distribute-for-python) and [here](http://www.virtualenv.org/en/latest/virtualenv.html).)

Create a new virtual environment on your server.
    
    
    $ mkvirtualenv pelican
    

Install Pelican in your virutalenv using `pip`:
    
    
    (pelican) $ pip install pelican
    (pelican) $ pip install markdown
    (pelican) $ pip install typogrify
    

### Install Dropbox CLI on your web server

For security reasons, it is better to create a new Dropbox account for your blogs and share a folder in that account with your main Dropbox account. This way you don't have to sync your whole Dropbox folder to your web server.

Logout from your Dropbox account on your browser and create the new Dropbox account. Using Dropbox's web interface, create a folder for your blogs (let's call it `blog`). Share this folder with your main Dropbox account.

Install the Linux [Dropbox command line client](https://www.dropbox.com/install?os=linux). Then run the Dropbox daemon from your Linux's server command line.
    
    
    (pelican) $ ~/.dropbox-dist/dropboxd
    

The first time you run the daemon, it will ask you to visit a link on your browser so that Dropbox links your web server to your new account:
    
    
    This client is not linked to any account...
    Please visit https://www.dropbox.com/cli_link?host_id=xxxxxxxxxxx
    

Copy the link and paste it on your browser. (You must be logged to Dropbox with your newly created account for this to work.) Once this is done, Dropbox will take care of syncing your shared folder on your server.

### Configure Pelican

Create a new pelican blog using `pelican-quickstart`, as explained in the [Pelican documentation](http://docs.getpelican.com/en/3.3.0/getting_started.html#kickstart-your-site). (I won't cover how to configure Pelican here.)

Once finished, you will have a directory named `pelican` with the necessary files to run your blog.

Optional: download a bunch of Pelican themes from github to your blog's directory in Dropbox. (We will assume that your themes reside in `~/Dropbox/blog/pelican-themes/`.)

Copy the newly created `pelicanconf.py` and `publishconf.py` to create a custom version for your blog. (`example.com` for our purposes.)

Configure your Pelican blog as usual by modifying these new files.

We need to tell Pelican where to find your theme. Add your theme's path to your `examplecom_conf.py` file.

As generated by `pelican-quickstart`, `publishconf.py` will work as is if you run Pelican from your `/home/user/pelican` directory. But if you run Pelican from other directory, it will fail to import the `pelicanconf.py` settings because it won't find the file in the Python path.

To fix this, change `publish_examplecom.py` so that pelican modules are imported correctly when `watcher` runs the pelican script. Also, change the `from pelicanconf import *` statement to reflect your configuration's file name.

Create a `bash` script in your `/home/user/pelican` directory that calls Pelican to regenerate the blog. Name it something like `update_examplecom.sh`. (Use `which` to determine where the `pelican` executable resides.)

Make the script executable:

To create additional blogs, there is no need to run `pelican-quickstart` again. Just create new copies of `pelicanconf.py` and `publishconf.py`, and an appropriate bash script.

### Apache

The blog will be served as by Apache using virtual hosting.

Create the directory that will host your website. (I prefer to have my websites in my user's home directory, instead of under `/var/www`.)

Create the Apache's virtual host configuration file for your blog in `/etc/apache2/sites-available`. (For this example, `examplecom`).

Enable your new virtual domain:

### Some testing

Take a moment to test your configuration. Create a sample post in `~/Dropbox/blog/example.com/content/posts` using your favorite editor in your laptop (not directly on your server), and run`update_examplecom.sh` on your server. If everything goes right, you should be able to access your virtualhost at your domain.

### Using watcher to regenerate the blog automatically

`Watcher` is a nifty utility written in Python that monitors a directory and its subdirectories for change using the `inotify` interface. It can be configured to execute a command when a change is detected, which is just what we need to regenerate our blog.

We will use a [forked Watcher](https://github.com/splitbrain/Watcher) version that reads its configuration file from a Python-like .ini file instead of watcher's original YAML file.

Install `watcher`'s dependencies. Get `watcher` from [Github](http://github.com/splitbrain/Watcher), unzip the archive and copy `watcher.py` and `watcher.ini` to `/home/user/pelican`.

Next, create a new job for your blog in `watcher.ini`.

Start watcher:

Monitor `watcher`'s output to see if everything is working fine:

Create or modify another sample post on your blog. When you hit 'save' on your editor, it will take a few seconds for Dropbox to syncronize your post with your web server. `watcher` should notice the change and launch `update_examplecom.sh`. You should see something like this:

### Configuring additional blogs

You can configure Pelican to maintain aditional blogs easily:

  * create new Pelican configuration files and a regeneration script for each blog.
  * add a virtual host for the domain.
  * add a new job to `watcher`'s .ini file and restart `watcher`.

### Conclusion

Pelican is fast, even if it regenerates the whole blog every time. This setup enables you to blog from anywhere you can access your Dropbox account and a text editor. (In fact, most of this article was written using _Editorial_ on my iPad.)

Tags: pelican, dropbox, apache, watcher, python, blogging, baked blogs, static blogs
