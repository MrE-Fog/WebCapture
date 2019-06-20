# Docker Tutorial: Play With Containers (Simple Examples)

_Captured: 2018-08-15 at 10:25 from [dzone.com](https://dzone.com/articles/docker-tutorial-play-with-containers-simple-exampl?edition=387209&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-14)_

Docker has had a huge impact on the software development lifecycle, making the deployment of software at scale easy and secure. This Docker tutorial will cover the basics of running, starting, stopping, and removing Docker containers.

Docker makes it so easy to work with different programming languages with different versions on different operating systems all this on the same host.

Deploying your software becomes a lot easier after Docker where you don't have to worry about missing a system configuration or a prerequisite.

## Docker vs. Virtual Machine

If you are using any kind of virtual machines to run your work inside it, why you would need Docker to run your work inside it instead? Well...

The main difference between them is that Docker is an isolated process that runs in your native OS while the virtual machine is a complete isolated OS that runs on top of your host OS which takes more time to load. So Docker has benefits over virtual machines such as:

  * Loading speed
  * Small hardware resources required, unlike virtual machines.
  * Running multiple Docker containers at the same time on the same OS.
  * You can modify your container and deploy it or give the Docker file definition to a friend to start working on the same environment.

Actually, Docker is not a replacement for virtual machines, it comes to solve specific problems.

Suppose that your application needs 3 or more services which run on different operating systems so instead of running 3 virtual machines on the same host, you can run 3 containers smoothly on the same host. Sounds great!!

## Run Your Container

Before starting, ensure that Docker is installed correctly and is ready to accept your commands. Type the following command in a new Terminal window:

The above command outputs the version of Docker installed on your PC:

Time to start running the container:

When you run the above command for the first time, you should see an output in your Terminal window similar to this:

That was easy, wasn't it? Try running the same command again:

The second, third, or nth time you run the above command, you should see only this output in your Terminal:

Now that you have successfully run a container, it's time to analyze what exactly happened. Look at the following command:

This command contains multiple parts. First and foremost, you have the word docker. This is the name of the Docker command-line interface (CLI), used to interact with the Docker engine responsible for running containers.

Next, you have the word container, which indicates the context you are working with.

Next is the actual command you want to execute in the given context, which is `run`.

Now, you'd also need to tell Docker which container to run. In this case, this is the so-called alpine container.

Finally, you need to define what kind of a process or a task shall be executed inside the container when it is running. This is the last part of the command, `echo "Hello World"`.

## Run a Process Inside a Container

Now that you have understood the various parts of a command to run a container, try running another container with a different process running inside it:

This is the output:

In the previous example, the container image you've used is centos and the process you're executing inside the centos container is ping -c 5 127.0.0.1, which pings the loopback address five times until it stops.

  * The first line is as follows:

This tells you that Docker didn't find an image named `centos:latest` in the local cache of the system. So, Docker knows that it has to pull the image from some registry where the container images are stored.

By default, your Docker environment is configured such that images are pulled from the Docker Hub at hub.docker.com. This is expressed by the second line, as follows:

  * The next three lines of output are as follows:

This tells you that Docker has successfully pulled the image, `centos:latest`, from the Docker Hub.

All the subsequent lines of the output are generated by the process you ran inside the container, which is the ping tool in this case.

You may also have noticed the latest keyword occurring a few times. Each image has a version (also called a tag), and if you don't specify a version explicitly, then Docker automatically assumes it as the latest version.

If you run the preceding container again on your system, the first five lines of the output will be missing since Docker will find the container image cached locally and so it won't have to download it first. Try it out and verify.

## Running a Random Quotes Container

For the purpose of running a random quotes container, you'll need an algorithm that produces random quotes. The API that produces those free random quotes can be found [here.](https://talaikis.com/random_quotes_api/)

Now the goal is to have a process running inside a container that produces a new random quote every five seconds and outputs the quote to [STDOUT](https://likegeeks.com/shell-scripting-awesome-guide-part4/#STDOUT):

Stop the script by pressing Ctrl+ C. Here's the output:

Each response is a JSON-formatted string with the quote, its author, and its category.

Now, run this in an alpine container as a daemon in the background. For this, you'll need to compact the preceding script into a one-liner and execute it using the `/bin/sh-c "..."` syntax. The Docker expression will look as follows :

In the above expression, you used two new command-line parameters, `-d` and `-name.` The `-d` tells Docker to run the process running in the container as a [Linux daemon](https://likegeeks.com/linux-process-management/#Process-Types). The `-name` parameter can be used to give the container an explicit name.

If you don't specify an explicit container name, Docker will automatically assign the container a random but unique name. This name will be composed of the name of a famous scientist and an adjective.

Such names could be "boring_borg" or "angry_goldberg." Quite humorous, isn't it?

One important takeaway is that the container name must be unique. Ensure that the quotes container is up and running:

The important part of the preceding output is the STATUS column, which, in this case, is Up 16 seconds. This means that the container has been up and running for **16 seconds** now.

## Listing Containers

As you continue to run containers over time, you'd eventually get a lot of them in your system. To find out what is currently running on your host, you can use the `container ls` command as follows:

This will list all currently-running containers.

By default, Docker outputs seven columns with the following meanings:

**Column**
**Description**

Container ID
The unique ID of the container. It is a SHA-256.

Image
The name of the container image from which this container is instantiated.

Status
The status of the container (created, restarting, running, removing, paused, exited, or dead).

Ports
The list of container ports that have been mapped to the host.

Names

The name assigned to this container (multiple names are possible).

This will list containers in any state, be it created, running, or exited.

Sometimes, you may want to just list the IDs of all the containers. For this, you have the -q parameter:

You might wonder where this is useful. Here's an example:

The above command deletes all the containers currently defined on the system, including the stopped ones. The `rm` command stands for remove, and it will be explained further down in the tutorial.

In the previous section, you used the `-l` parameter in the list command. Try to use Docker help to find out what the `-l` parameter stands for. You can invoke help for the list command as follows:

## Stopping and Starting Containers

Sometimes, you may need to temporarily stop a running container. Try it out with the quotes container with this command:

Now, you can stop this container with the following command:

When you try to stop the quotes container, you will probably note that it takes a while (about 10 seconds) until it's executed. Why is this the case? Docker sends a [Linux SIGTERM signal](https://likegeeks.com/linux-bash-scripting-awesome-guide-part5/#Linux-Signals) to the main process running inside the container.

If the process still doesn't terminate itself, Docker waits for 10 seconds before sending SIGKILL, which kills the process forcefully and terminates the container.

In the above command, the name of the container is used to specify the container to be stopped. The container ID can also be used instead.

## How Do You Get the Container ID?

There are several ways of doing so. The manual approach is to list all the running containers and find the one that you're looking for in the list. Just copy its ID from there.

A more automated way is to use shell scripting and [environment variables](https://likegeeks.com/linux-environment-variables/). For example, if you want to get the ID of the quotes container, here's an example:

Here we used [AWK](https://likegeeks.com/awk-command/) to get the first field which is the container ID. Now, instead of using the container name, you can use the` $CONTAINER_ID` variable in your expression:

Once you stop the container, its status changes to Exited.

You can restart a stopped container with the `docker container start` command.

## Removing Containers

When you run the `docker container ls -a` command, you can see quite a few containers that are in the Exited status.

If you don't need these containers anymore, it's better to remove them from memory; otherwise, they unnecessarily occupy precious resources. The command to remove a container is as follows:

Alternately, you can also use this command:

Sometimes, removing a running container will not work; if you want to force the removal, you can use the command-line parameter `-f` or `-force` .

Containerization has changed the way the industry used to operate by mitigating maintenance costs by over 50% and time-to-market by around 90%. Further, containers make applications more secure as opposed to running them outside containers.

If you found this tutorial helpful and want to learn more about Docker containers, you can read more from [Learn Docker - Fundamentals of Docker 18.x](https://amzn.to/2LgQZmN), which explain all the critical concepts, related to containerization and orchestration.