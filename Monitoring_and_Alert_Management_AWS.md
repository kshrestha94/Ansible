
# Monitoring and Alert Management with Amazon Web Services (AWS)

```
Services offered by AWS that enables monitoring of resources and the generation of alerts or notifications based on user defined conditions.
```

# Simple Architecture

![Alt text](<cloudwatch and SNS.png>)

```
I created virtual computer resource on AWS which is referred as a EC2 instance.

AWS CloudWatch service is a monitoring system that collects and track metrics from a virtual machine. This service allows monitoring resource utilization, and performance metrics.

Amazon (SNS) Simple Notification Service is a messaging service which enables sending notification to a variety of different endpoint including, email, SMS, and mobile push endpoints.

The SNS message distributor allows to publish messages or alerts to multiple subscribers simultaneously.
```

# Application Demo of Monitoring CPU Utilization

```
I created a virtual machine, utilised these services by creating an infrastructure monitor on CloudWatch and setting up an alert SNS directly to my personal email. 

I chose to monitor the CPU performance of my virtual machine and configured it to alert me only if the threshold exceeds my input condition.

The monitor on my dashboard shows fluctuations of the CPU below the threshold (1.5). Once the instance is loaded with stress, for example, running a simple ’sudo apt upgrade’ command.

The monitoring data line produces a spike for the given period hence triggering the SNS and pushing a notification to my personal email.

A common day to day example of this may be a simple text message notification received to the user when their account balance is below a certain limit.


```

# What have I learnt? 

 - `Powerful tool for monitoring different metrics.`

 - `Sending timely notifications without human intervention.`



Integration of both services 
detecting anomalies


manage and respond to performance issues in AWS environment. 

trigger a secondary response of an EC2 action 
Autoscaling  promoting high availability and scalability. 

level of integration AWS has to offer.


# Blockers?

```

seting the user defined threshold. 

too low, you might receive too many notification or false alarms.

too high you might not trigger the alarm.  


```
# Benefits I gained  and how it can help businesses ?

```

gain visibility on their infrastructure, applications, and business operations.

using the services 
proactively merge incidents, 
optimize resources, 
ensure security and compliance. 

data driven decisions driving efficiency,  resulting in performance improvements.


```


