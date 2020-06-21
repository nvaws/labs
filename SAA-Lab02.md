This lab helps you create a web application for your company that specialises in Drone delivery of Food. the customer place an order over the appliction which is stored in DynamoDB table in AWS. An email notification is sent to you as well as the order is put in the queue for further processing.



AWS services used:  
- IAM
- Elastic Beanstalk
- Cloudformation
- DynamoDB
- Simple Queue Service
- Simple Notification Service

Create a Custom Policy "FoW_EC2_Instance_Policy" with below mentioned permissions

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action":   [ "dynamodb:PutItem" ],
      "Resource": [ "*" ]
    },
    {
      "Effect": "Allow",
      "Action":   [ "sns:Publish" ],
      "Resource": [ "*" ]
    }
  ]
}
```

Create an IAM Role:  
- Trusted Entity: EC2
- Permissions: "FoW_EC2_Instance_Policy"
- Name: "FoW_EC2_Instance_Role"

Go to Elastic Beanstalk service under Compute  

- Click on "Create Application"
- Application name: FoodOnWings
- Platform: Node.js
- Platform branch: Node.js running on 64bit Amazon Linux (ensure you do not select Amazon Linux 2)
- Platform version: 4.14.3
- Node.js version: 12.16.2

In the Source Code Origin section, click on Local File and upload the zip that you downloaded from [this link](https://github.com/ashydv/FoodOnWings/raw/master/FoodOnWings.zip).

Click on 'Configure more options'

Find the Security Box and click on Edit
- Service role: Leavve Default
- EC2 key pair: Select any existing key, leave blank if not present
- IAM instance profile: FoW_EC2_Instance_Role
- Click Save
- Click Create Application

You get to see the deployment logs while the Elastic Beanstack deploys your application. You will see the application URL once the deployment is completed.  

You can browse the application now.

Open DynamoDB, SNS, SQS in three different browser tabs and notice the resources that have been created by this application on your behalf.

Go to SNS and click on the topic name that starts with 'awseb'
- Click on Create Subscription
- Protocol: Email
- Endpoint: Type your own email ID
- Click on Create subscription

Now check your eamil, you would have got a notification, Click on confirm subscription.

You are all set now to recieve orders from your customers on this website.

Go ahead and place an order by clicking on "Call a drone" button.

The order will be saved in the DynamoDB table, an email notifiction email will sent to your earlier subscribed email ID and the same will also be put in the SQS queue for further processing.

Clean Up
- Go to the home page of Elastic Beanstalk
- Click on Application on the left panel
- Select your application and go to Action drop down
- Click on Delete application


Lab completed.
