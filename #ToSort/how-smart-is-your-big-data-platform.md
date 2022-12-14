# How Smart Is Your Big Data Platform?

_Captured: 2017-04-28 at 22:03 from [dzone.com](https://dzone.com/articles/how-smart-is-your-big-data-platform?oid=bigdata17social&utm_content=buffer19df3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

_[This article is featured in the new DZone Guide to Big Data: Data Science & Advanced Analytics. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/big-data-data-science-and-advanced-analytics)_

Big Data, business analytics platforms, and IoT have upended the business and IT worlds. Organizations have realized the significant financial benefits to be gained by analyzing the massive amounts of data their systems generate to see what improvements or changes can be made to their product or processes. While the benefits of data analysis are compelling, the exponential growth in the amount of data generated by connected systems makes handling that data a complex proposition.

With organizations generating terabytes of data every day, the time required to upload, categorize, clean, and analyze that data to gain any insight from it can be significant. In light of this, organizations have implemented batch data processing schedules in which new data from client devices is uploaded to the data center for analysis at scheduled intervals rather than continuously. The data is then analyzed, the appropriate action identified, and instructions to implement that action are sent back to the device. Batch data processing can take anywhere from a few hours to a few days to complete. In applications requiring faster performance, real-time scoring of data based on identifying a few attributes and uploading them for immediate analysis can shorten the time required between data analysis and action, but accelerating the process is not without cost. Data scoring is typically limited to attributes gathered in a single transaction, so it can't incorporate any findings from previous transactions.

While batch processing and real-time scoring are sufficient for applications that don't require real-time performance adjustments or machine learning to automate those adjustments, there are vertical markets (healthcare, for example) where decisions need to be made and implemented in seconds to avoid potentially catastrophic problems. Additionally, after the data is analyzed and the analytics platform recommends a change to a client device or process, if that change requires a human to implement it, the time between collecting data and taking action based on that data can grow even longer.

![Image title](https://dzone.com/storage/temp/5069214-screen-shot-2017-04-24-at-42440-pm.png)

_In this IoT-enabled insulin pump example, (1) data is uploaded from the device via a Bluetooth connection to a smartphone which then (2) sends the data via WiFi or cellular connection to the data center for analysis. After analysis, the data center sends new instructions back to the device (3). If the data center receives data indicating a health emergency requiring immediate assistance, it can then call 911 (4) and/or instruct the user's phone to also call 911 (5)._

## Delivering Analytics in Real-Time

The need to deliver real-time analytics becomes more challenging when the connected nature of IoT is added to the mix. Specifically, endpoint devices in an IoT network are not always guaranteed to be connected to the Internet. Imagine a combination blood sugar monitor/personal insulin pump with a built-in cellular or WiFi modem to provide connectivity. Throughout the day, the device measures the user's blood sugar and uploads the data to a healthcare service provider's data center for analysis. When data from the device is analyzed, if blood sugar levels are too high, the healthcare provider's analytics platform can instruct the pump to administer the correct injection dosage. But what if the insulin pump is unable to connect? What if the user is traveling and can't get the pump online due to poor signal quality or technical issues? The insulin pump wouldn't be able to provide real-time blood sugar updates to the data center or receive instructions about the dosage and time until the next injection. It's easy to see the significant health risks such a scenario presents to patients, as well as the potential liability exposure the device OEM and/or healthcare provider could face.

In the world of real-time Big Data analytics, changes to devices and processes need to happen quickly, locally, and automatically. Furthermore, automation can't simply be a pre-defined list of rules that instructs an endpoint device to take action when a condition is met. Trying to anticipate any potential problem and developing a rule to handle it locally requires too much time and effort. So what's an organization to do?

## Smart Data Empowers the Endpoint

The solution to the problem is smart data. The "smart" adjective has been used to describe a host of connected devices and services, but what does it mean when applied to data? Let's define smart data as digital information that is formatted so it can be acted upon at the endpoint before being sent to a downstream analytics platform for further consolidation and analytics. Furthermore, the action taken is not merely a pre-defined list of instructions already in place that is implemented automatically when certain parameters are met. Rather, the data analysis (artificial intelligence) that determines what action to take is performed by the endpoint itself, using its own processing resources and machine learning to identify the proper course of action. Another way to look at smart data is to see how similar it behaves in comparison to the human brain. The human brain is constantly learning from the data it receives over time and can determine the proper course of action when it sees a familiar pattern.

Let's apply smart data to our hypothetical insulin pump to see how it could enable the pump to self-correct without the need to access a centralized data pool for analysis and action. The pump detects elevated blood sugar levels in the patient and recognizes that this is a critical situation. In addition to contacting the data center, the device immediately contacts the patient's doctor using the patient's cell phone and notifies the patient and people around him.

![Image title](https://dzone.com/storage/temp/5069252-screen-shot-2017-04-24-at-43628-pm.png)

_With Smart Data (1), if the medical device is unable to connect to the datacenter (2), the endpoint can conduct analysis on the smart data independently (3) to determine if action is required (in this case, calling 911). Additionally, the data center can also call for help to notify the patient or 911 if it detects an abnormal reading or a lost connection (4)._

In addition, the device would recommend the right course of action. For example, upon determining the patient's blood sugar is too high, the pump could determine on its own that a dose of insulin should be injected and extra blood sugar tests conducted over the next few hours to confirm that levels return to normal. This analysis and decision-making process would run in the background and require no involvement from the patient, device OEM, or healthcare provider. Over time, if blood sugar levels continue to fluctuate, it could be an indicator of a more serious health problem. The device could then alert the patient and advise them to seek immediate medical attention.

So, while Big Data, business analytics, and IoT have revolutionized our relationship with data, the benefits they provide will remain beyond the reach of organizations requiring real-time analytics until analysis and decisions can happen at the endpoint. Smart data makes that possible.

_[This article is featured in the new DZone Guide to Big Data: Data Science & Advanced Analytics. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/big-data-data-science-and-advanced-analytics)_

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
