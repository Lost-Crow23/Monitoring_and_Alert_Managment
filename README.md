<h1>Setting Alarm using Cloudwatch</h1>

![cloudwatch diagram](https://user-images.githubusercontent.com/126012715/235471175-ccb6017a-bc36-430c-a9f5-5ec96f23648b.png)

![image](https://user-images.githubusercontent.com/126012715/235475367-81d0d2e4-b370-4d36-bf00-90c59cbe20e3.png)


<h3>Step 1</h3>

- Create an instance, we used our `s3boto3` from our previous classes, to which I started launching / running. 

<h3>Create a SNS Topic</h3>

<h3>Step 1</h3>

- Search and click the `SNS` service by Amazon and create a topic.
- Convent a name name-tech221-sns-topic.
- Create topic

<h3>Create a Subscription</h3>

- Select SNS topic and create sub.
- Select `email` as a protocol for the endpoint for notifications to be sent.
- Enter email address name@spartaglobal.com.
- Create and check email for confirmation of subscription through the steps of authorisation.

<h3>Alarm Setup</h3>

- Cloudwatch search and click create alarm
- Copy the `s3boto3` instance's ID and use this as the basis of the endpoint alarm
- Paste it under the metrics, on cloudwatch
- Find the CPU utilisation metric under the `s3boto3` instance 
- Desired threshold is set, `50%` for this test, and 5 minutes for the period of notification of the alarm if it goes above the thresold - you may use a 
lower thresold and lower period if it doesn't meet criteria.
- Send notification to SNS topic under the Actions tab, and click SNS topic
- Create Alarm

<h3>Create Dashboard </h3>

- Create Dashboard under the dashboard tab
- Provide name e.g name-tech221-CPU-utilisation
- Add widget as prompted with the preffered default visual tabs available, We select our `alarm` and `line graphs`
- Copy `s3boto3` instance ID and paste it under the metric
- Create widget

<h3>Final Setup</h3>

- SSH our instance onto our git bash terminal by following the `connect` method
- Create a python file by making `nano folder` e.g `sudo nano cpu_load.py` to test out the CPU utilisation and if the desired thresold is reached thus sending us an email due to the alarm.
- Within the python file, a `while loop` must be in effect to disrupt the CPU and go above the thresold. And excute file `python cpu_load.py`.

      import time
      import random
      
      while True:     
        x = random.random()     
        y = random.random()     
        z = x * y

- It should be on standby which means it is working, go onto Dashboard within Cloudwatch
- If above thresold, it would be seen in the graph created.
- Wait the desired period of 5 minutes, then check email to see the notif of the alarm.
- An example can be seen as below:

<img width="792" alt="SNS Topic Alarm email" src="https://user-images.githubusercontent.com/126012715/235470995-3787aaef-64ac-414b-b1af-af4b3ed039e7.png">
