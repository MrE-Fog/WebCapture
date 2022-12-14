# Understanding Machine Learning

_Captured: 2017-05-04 at 11:14 from [dzone.com](https://dzone.com/articles/understanding-machine-learning?oid=twitter&utm_content=buffera0aa3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Effortlessly power IoT, predictive analytics, and machine learning applications with an [elastic, resilient data infrastructure](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101). Learn how with [Mesosphere DC/OS](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101).

What exactly is machine learning?

The simplest definition I came across:

> _Machine learning is "[…] the branch of AI that explores ways to get computers to improve their performance based on experience".   
  
Source: [Berkeley](http://bit.ly/2iuqg44)_

Let's break that down to set some foundations on which to build our machine learning knowledge.

**Branch of AI: **Artificial intelligence is the study and development by which a computer and its systems are given the ability to successfully accomplish tasks that would typically require a human's intelligent behavior. Machine learning is a part of that process. It's the technology and process by which we train the computer to accomplish the said task.

**Explores ways:** Machine learning techniques are still emerging. Some models for training a computer are already recognized and used (as we will see below), but it is expected that more will be developed with time. The idea to be remembered here is that different models can be used when training a computer. Different business problems require different models.

**Get computers to improve their performance: **For a computer to accomplish a task with AI, it needs practice and adaptation. A machine learning model needs to be trained using data and in most cases, a little human help.

**Based on experience: **providing an AI with experience is another way of saying - to provide it with data. As more data is fed into the system, the more accurately the computer can respond to it and to future data that it will encounter. More accuracy in understanding the data means a better chance to successfully accomplish its given task or to increase its degree of confidence when providing predictive insight.

**Quick example:**

  1. Entry data is chosen and prepared along with input conditions (e.g. credit card transactions).
  2. The machine learning algorithm is built and trained to accomplish a specific task (e.g.detect fraudulent transactions).
  3. The training data is augmented with the desired output information (e.g. these transactions appear fraudulent, these do not).![2-Layers \(2\)](http://blog.arcbees.com/wp-content/uploads/2-Layers-2.png)

## **How Does Machine Learning Work?**

Machine learning is often referred to as magical or a black box:

Insert data -> magic black box-> Mission accomplished.

Let's take a look at the training process itself to better understand how machine learning can create value with data.

  * **Collect**: Machine learning is dependent on data. The first step is to make sure you have the right data as dictated by the problem you are trying to solve. Consider your ability to collect it, its source, the required format, and so on.
  * **Clean:** Data can be generated by different sources, contained in different file formats, and expressed in different languages. It might be required to add or remove information from your data set, as some instances might be missing information while others might contain undesired or irrelevant entries. Its preparation will impact its usability and the reliability of the outcome. 
  * **Split:** Depending on the size of your data set, only a portion might be required. This is usually referred to as sampling. From the chosen sample, your data should be split into two groups: one to train the algorithm and the other to evaluate it.
  * **Train:** This stage essentially aims at finding the mathematical function that will accurately accomplish the chosen goal. Training takes on different forms depending on the type of model used. Fitting a line in a simple linear regression model can be seen as training; generating the decision trees for a Random Forest Algorithm is also training; changing the questions in a decision tree is effectively adjusting the parameters of the model.To keep things simple, let's focus on neural networks. Basically, using a portion of your data set, the algorithm will attempt to process the data, measure its own performance and auto-adjust its parameters (also called [backpropagation](http://bit.ly/2iuF0A0)) until it can consistently produce the desired outcome with sufficient reliability.  

  * **Evaluate: **Once the algorithm performs well on the training data, its performance is measured again with data that it has not yet seen. Additional adjustments are made when needed. This process allows you to prevent overfitting, which happens when the learning algorithm performs well but only with your training data.
  * **Optimize: **The model is optimized for integration within the destined application to ensure it is as lightweight and as fast as possible.

## **Are There Different Types of Machine Learning?**

There are many different models that can be used in machine learning but they are typically grouped into three different types of learning: supervised, unsupervised, and reinforcement. Depending on the task to complete, some models are more appropriate and better performing than others.

**Supervised learning: **in this type of learning, the correct outcome for each data point is explicitly labeled when training the model. This means the learning algorithm is already given the answer when reading the data. Rather than finding the answer, it aims to find the relationship so that when unassigned data points are introduced, it can correctly classify or predict them.

![3-Data](http://blog.arcbees.com/wp-content/uploads/3-Data.png)

In a classification context, the learning algorithm could be, for example, fed with historic credit card transactions each labeled as _safe_ or _suspicious_. It would learn the relationship between these two classifications and could then label new transactions appropriately, according to the classification parameters (e.g. purchase location, time between transactions, etc.).

![4-Classification](http://blog.arcbees.com/wp-content/uploads/4-Classification.png)

In a context where data points are continuous in relation to one another, like a stock's price through time, a regression learning algorithm can be used to predict the following data point.

![6-Regression](http://blog.arcbees.com/wp-content/uploads/6-Regression.png)

**Unsupervised learning: **In this case, the learning algorithm is not given the answer during training. Its objective is to find meaningful relationships between the data points. Its value lies in discovering patterns and correlations. For example, clustering is a common use of unsupervised learning in recommender systems (e.g. people who liked this bottle of wine, also enjoyed this one).

![5-Clustering](http://blog.arcbees.com/wp-content/uploads/5-Clustering.png)

**Reinforcement learning:** this type of learning is a blend between supervised and unsupervised learning. It is usually used to solve more complex problems and requires interaction with an environment. Data is provided by the environment and allows the agent to respond and learn. In practice, this ranges from controlling robotic arms to find the most efficient motor combination, to robot navigation where collision avoidance behavior can be learned by negative feedback from bumping into obstacles. Logic games are also well-suited to reinforcement learning, as they are traditionally defined as a sequence of decisions: games such as poker, backgammon and more recently Go with the success of [AlphaGo from Google.](http://bit.ly/2iJ701Y) Other applications of reinforcement learning are common in logistics, scheduling, and tactical planning of tasks.

## What Can Machine Learning Be Used For?

Three stages of machine learning development and their application within a business are to be considered: descriptive, predictive, and prescriptive.

The descriptive stage refers to the recording and analysis of historical data for increased business intelligence. Managers are provided with descriptive information and a better understanding of the results and consequences of past actions and decisions. This process is now routine for most large businesses around the world- for example, reviewing sales records and matching promotional efforts to understand their impact and ROI.

The second stage of applied machine learning is prediction. Gathering data and using it to predict a specific outcome allows for increased reactivity and to make decisions faster and with more accuracy. For example, predicting churn can allow for its prevention. This stage of application is currently being embraced by most businesses.

Yet, the third and most advanced stage of machine learning is already being adopted by existing businesses and pushed forward by newly founded endeavors. Predicting a behavior or outcome is not sufficient when aiming for effective and efficient business practices. Understanding the cause, motive, and context is a prerequisite to optimal decision-making. Concretely, this stage is possible when human and machine combine efforts. Machine learning is used to find meaningful relations and to predict outcomes while data experts serve as translators to make sense of why the relation exists. As such, it becomes possible to prescribe actions with greater precision.

Furthermore, I would add another application of machine learning other than predictive insight: process automation. I've provided a more detailed overview and comparison these two concepts [here](http://bit.ly/2hEiB55).

Here are some examples of what problems machine learning can solve.

**Logistics and production**

  * [Rethink Robotics](http://www.rethinkrobotics.com/) uses machine learning to train their robotic arms and improve production speeds;
  * [JaybridgeRobotics](http://www.jaybridge.com/) automates industrial grade vehicles for more efficient operations;
  * [Nanotronics](http://www.nanotronics.co/) automates optical microscopes for improved inspections;
  * [Netflix](http://netflix.com) and [Amazon](https://www.amazon.com) optimize resource distribution according to user demand;
  * Other examples include: predicting ERP/ERM needs; predicting asset failure & maintenance, improving quality assurance, and increasing production line performance.

**Sales and marketing**

  * [6sense](https://6sense.com/) predicts which lead is more susceptible to buy and at what time;
  * [Salesforce Einstein](https://www.salesforce.com/products/einstein/overview/) helps anticipate sales opportunities and automate tasks;
  * [Retention Science](http://retentionscience.com/) suggests cross-channel actions to drive engagement;
  * Other examples include: predicting a customer's lifetime value, increasing customer segmentation accuracy, detecting customer shopping patterns, and optimizing a user's in-app experience.

**Human resources**

  * [Entelo](https://www.entelo.com/) helps recruiters identify and qualify candidates;
  * [hiQ](https://www.hiqlabs.com/) assists managers with talent management.

**Finance**

  * [Cerebellum Capital](http://www.cerebellumcapital.com/) and [Sentient](http://www.sentient.ai/sentient-investment-management/) augment investment management decisions with machine learning powered software;
  * [Dataminr](https://www.dataminr.com/) can assist with real-time financial decisions by providing early alerts on social trends and breaking news;
  * Other examples include: detecting fraudulent behavior and predicting stock prices.

**Healthcare**

  * [Atomwise](https://www.atomwise.com/) uses predictive models to reduce medicine production time;
  * [Deep6 Analytics](https://deep6analytics.com/) identifies eligible patients for clinical trials
  * Other examples include: diagnosing diseases more accurately, improving personalized care, and assessing health risks.

You can find even more examples of machine learning and artificial intelligence and other related resources in an awesome [list](http://bit.ly/2hRlqwY) put together by [Sam DeBrule](http://bit.ly/2hwGVph).

# **Before you go.**

Remember that collaboration is key. AI and machine learning are fascinating but can be tricky at times. If you are dabbling in AI, you should talk to your local AI expert. If there is one thing I learned about the AI field, is that its members are strongly passionate and are more than willing to help out. You can also comment or ask questions below, it would be my pleasure to help if I can.

Learn to design and build better data-rich applications with this [free eBook from O'Reilly](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fresources%2Fdesigning-data-intensive-applications%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202). Brought to you by [Mesosphere DC/OS](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202).

### Like This Article? Read More From DZone
