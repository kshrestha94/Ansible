
# Monitoring and Alert Management with Amazon Web Services (AWS)

```
Services offered by AWS that enables monitoring of resources and the generation of alerts or notifications based on user defined conditions.
```

# Simple Architecture

![Alt text](<cloudwatch and SNS.png>)

# Application of Monitoring CPU Utilization

```
I created a virtual machine resource which is called an EC2 instance on AWS.

I utilized the AWS Cloudwatch service to create a infrastructure monitor for CPU Utiliztion.

I created an alert alarm to notify me on my personal email using AWS System Notification Service SNS. In the process i was able to define the threshold condition (10%?) and only alert me if it exceeds the value.

```

![Alt text](<CPU monitor added to dashboard.png>)

```
I added this monitor to my dashboard and can easily assess the fluctuation of the data point for the selected time period.

When i loaded my vitual machine with any amounts of stress for example, running my database script. It produced a spike on the CPU therefore triggering the SNS to push a alert notification to my email. 

A common day to day example of this may be a simple text message notification received to the user when their account balance is below a certain limit.
```
# What have I learnt? 

- `connectivity of services: cloudwatch to my VM`

- `Powerful tool for monitoring different metrics. (detailed monitoring? - higher cost for almost realtime monitoring)`

- `Sending timely notifications without human input.`

- `setting the threshold; 10% for my VM but 70% when in production`

- `service can allow me to trigger a secondary responce of a EC2 action or autoscaling which will promote high avaiability and scaleability` 
  
# Blockers?

```
A blocker that i faced was not recieving notification when manually loading stress on my virtual machine. 

The approach i took to resolve this issue was reviewed my steps and checked my documentation and noticed that i did not verify the topic subscription.

once verified i was able to recieve notifications.

```
![Alt text](<sns topic subcription confirmation 2.1.1.png>)
```
when seting the user defined threshold:

- too low, you might receive too many notification or false alarms.

- too high you might not trigger the alarm.  
```

# What i Benefited and how can i help businesses ?

```
Monitoring and Alerting: CloudWatch provides comprehensive monitoring for AWS resources, applications, and custom metrics. You can set up alarms to trigger notifications via SNS when specific thresholds or conditions are met, enabling proactive alerting and issue resolution.

Real-Time Event Processing: CloudWatch Events can capture and respond to events from various AWS services in real-time. By integrating with SNS, you can instantly notify relevant parties about critical events, such as instance terminations or API calls.

Scalability and Auto-Scaling: CloudWatch can automatically monitor your resources and trigger auto-scaling actions based on predefined metrics. SNS can be used to inform administrators or teams when auto-scaling events occur.
```

