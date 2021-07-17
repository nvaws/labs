# Serverless thumbnail generation using AWS Lambda and Amazon S3

**Introduction**: In this lab we will create a sample Lambda function that creates thumbnails of
the pictures (.jpg and .png) uploaded in an S3 bucket and saves them in another S3 bucket.

The following diagram illustrates the application flow:

![](https://github.com/ashydv/aws-labs/blob/master/images/lambda.PNG)

1. An end user uploads a picture (.png or .jpg) on the application. The application stores that image to an S3 bucket.
2. Amazon S3 detects the object-created event.
3. Amazon S3 publishes the s3:ObjectCreated event to AWS Lambda, invoking the Lambda function and passing event data as a function parameter.
4. AWS Lambda executes the Lambda function by assuming the execution role that you specified at the time you created the Lambda function.
5. The Lambda function knows the source bucket name and object key name from the event data that it received.
6. The Lambda function reads the object and creates a thumbnail using graphics libraries and saves it to the target bucket.

**AWS Resources Required:** - You will have to create the following Amazon S3, Lambda, and IAM
    resources in your account to accomplish this lab.

- IAM role
- Two S3 buckets (one for holding original picture and anther to hold the thumbnails)
- Lambda function.

**Please ensure to use us-west-2 (Oregon) region to do this lab.**

We will complete the scenario in below steps

**Step 1:** Creating a Role that will allow your Lambda function to talk to S3 buckets.  
**Step 2**: Creating one bucket to host the original pictures and another to hold the thumbnails.  
**Step 3**: Creating a Lambda function.  
**Step 4**: Verifying the function.  
**Step 5**: Cleaning up post lab completion.

Let us get started.

**Step 1** – Creating a Role that will allow your Lambda function to talk to s3 buckets

Go to IAM and create a Role as below.

- Select type of trusted entity – Lambda
- Attach permissions policies - AmazonS3FullAccess
- Role name – lambda-execution-role (or any name you want)

**Step 2** – Creating a bucket to host the original pictures and another to hold the thumbnails

:key: Ensure both buckets are created in **Oregon** region and with default options.

- Create a bucket with any name you want i.e. “_xyz_”.
- Create another bucket with name “_xyz_-resized”.

**Step 3** – Creating a Lambda function in **Oregon** region and configuring the trigger.

**Step 3.1** – Go to Lambda under Compute services, check the Region name on top Right corner.

Create a function > Author from scratch

- Name: “my-lambda-function” (or any name)
- Runtime: Python 3.6
- Permissions > Change default execution role > Use an existing role: Choose the one you created in Step 01)

Click on create function, you should see a success message on the next screen.

We have just created a name/placeholder for our function and selected desired platform, now let us supply the code.

Download the code zip from [here](https://github.com/ashydv/ThumbnailCreation/raw/master/CreateThumbnail.zip)  

- Scroll to the Function Code section.
- Click the Action dropdown and click on Upload a zip file.
- Select the zip file you just downloaded and click on Save.
- Wait till the file is uploaded. The next screen comes automatically.
- Ignore the message _The deployment package of your Lambda function "anyname" is too large to enable inline code editing. However, you can still invoke your function_
- Scroll down to the **Runtime settings** section > Edit > edit the handler info as mentioned below.
- :key: Handler: `CreateThumbnail.handler`
- Click on Save

**Step 3.2** – Creating a trigger

On the left side of the Designer section you will see the Add Triggers option, click on Add Triggers.

Now in the Trigger configuration dropdown, select S3

- Bucket – select your firstbucket (not the one with resized in the name)
- Event type – All object create events

Leave other fields as default and click on Add at the bottom right of the screen.

**Step 4** – Verifying the function.

- Upload a .jpg or .png picture to the source bucket using the Amazon S3 console.
- Check if the thumbnail got created in the “_bucketname_-resized” bucket.
- Check the size difference between the original and resized object.

Congratulations, you have just created, a serverless lambda function that gets triggered by an event in an S3 bucket.

You may now go to the monitoring tab and try to understand the various graphs shown on the console page.

**Step 5** – Clean up post lab completion.

- Delete both the buckets along with their objects.
- Delete the role you created.
- Delete the lambda function.

✔️ Lab Complete!

**Note:** This lab document is a simplified version of a tutorial published by AWS on their portal. You are encouraged to visit the following link to know more in details when you get time.

<https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html?shortFooter=true>
