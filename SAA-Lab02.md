# Food On Wings

In this lab excersise you deploy a web application for your company that specialises in Drone delivery of Food. The customer place an order over your appliction, customer's information is stored in a DynamoDB table.  An email notification with order information is sent to the owner (you) as well as the order is put in the queue for further processing.

## AWS services used

- IAM
- Elastic Beanstalk
- Cloudformation
- DynamoDB
- Simple Queue Service
- Simple Notification Service

### :white_check_mark: Creating a custom policy

Visit IAM and create a Custom Policy "FoW_EC2_Instance_Policy" with below mentioned permissions

```json
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

### :white_check_mark: Creating an IAM Role

Visit IAM and create an IAM Role as stated below

- Trusted Entity: EC2
- Permissions: "FoW_EC2_Instance_Policy"
- Name: "FoW_EC2_Instance_Role"

### :white_check_mark: Deploying the application using Elastic Beanstalk

Go to Elastic Beanstalk service under Compute  

- Click on "Create Application"
- Application name: FoodOnWings
- Platform: Node.js
- Platform branch: Node.js running on 64bit Amazon Linux (ensure you do not select Amazon Linux 2)
- Platform version: 4.14.3
- Node.js version: 12.16.2

In the Application code section, Upload your code and **upload the zip file** that you downloaded from [this link](https://github.com/ashydv/FoodOnWings/raw/master/FoodOnWings.zip).

Click on 'Configure more options'

Find the Security Box and click on Edit

- Service role: Leave Default
- EC2 key pair: Select any existing key, leave blank if not present
- IAM instance profile: FoW_EC2_Instance_Role
- Click Save
- Click Create Application

You get to see the deployment logs while the Elastic Beanstalk deploys your application. You will see the application URL once the deployment is completed.  

You can browse the application now.

Open DynamoDB, SNS, SQS in three different browser tabs and notice the resources that have been created by this application on your behalf.

### :white_check_mark: Adding owner's (your) email ID for notifications

Go to SNS and click on the topic name that starts with 'awseb'

- Click on Create Subscription
- Protocol: Email
- Endpoint: Type your own email ID
- Click on Create subscription

Now check your eamil, you would have got a notification, Click on confirm subscription.

You are all set now to recieve orders from your customers on this website.

### :white_check_mark: Testing the application

Go to your website and place an order by clicking on "Call a drone" button.

The order data will be saved in the DynamoDB table, an email notification email will be sent to owner's (your) email ID and the order will also be put in the SQS queue for further processing.

#### :bulb: Our objective for this lab is achived, feel free to explore a few things further on your own

- How can you make this application highly available!
- How can you have a custom domin name fot this website!
- How can you deploy the upgraded version of code!
- How can you achieve BlueGreen deployment with this application!
- How can you add authentication layer to your webapp! 

### Clean Up

- Go to the home page of Elastic Beanstalk
- Click on Application on the left panel
- Select your application and go to Action drop down
- Click on Delete application
- Release the Elastic IP

✔️ Lab completed.
