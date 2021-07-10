# Designing Network and Compute architecture for a Highly Available Web Application.

## Lab 01 – Part 01 of 03

Private networks in AWS are created by the service called Amazon Virtual Private Cloud (VPC). We can create a VPC within any AWS region of our choice and within that VPC we define subnets to manage related sets of servers or other AWS resources. VPC service lets us define rules for how network traffic from our subnets is routed. We can also decide whether our private network (VPC) should be connected to the Internet, to corporate networks or to keep the network completely private.

In this lab we are going to design the network for a highly available two tier web application. The load balancer will be deployed in two public subnets across two availability zones having Internet connectivity via Internet Gateway. Rest all web/app/db servers will be deployed in two private subnets across two availability zones having outbound only internet connectivity via network address translation (NAT) service. The incoming and outgoing traffic will be filtered by virtual firewalls; by NACL at Subnet level and by Security Groups at instance/resource level.

The network after building, will look similer to the picture below

![](https://github.com/ashydv/aws-labs/blob/master/images/NetworkDiagram.png)

### Activity 01 – Creating a VPC

Login to your AWS account and find VPC under Networking & Content Delivery category.  
Click on Your VPCs in the side bar and then click on Create VPC.  

_Did you notice that a VPC (default VPC) was already created? Find out what other resources were automatically created for you in VPC and why._

Now you need to give a name to your VPC and select a CIDR notation.

* Name tag: MyVPC
* IPv4 CIDR block: 10.0.0.0/16
* IPv4 CIDR block: No IPv6 CIDR Block
* Tenancy: default
* Click on Yes Create.

Select MyVPC and click on Action drop-down.

* Select Edit DNS hostnames and click Enable.

### Activity 02 - Creating Subnets

We would now create one public and one private subnet in both availability zones for high availability of our resources.
Click on Subnets in the sidebar of the VPC Dashboard, click on Create Subnet

* Name tag: MyPrivateSubnet01
  * VPC: MyVPC
  * Availability Zone: _choose the first AZ from dropdown_
  * IPv4 CIDR block: 10.0.1.0/24
  
Click on Yes, Create. Your new subnet should have been created now and show up on the screen.  
Repeat the same steps to create 3 more Subnets with below configuration.

* Name tag: MyPrivateSubnet02
  * VPC: MyVPC
  * Availability Zone: _choose the second AZ from dropdown_
  * IPv4 CIDR block: 10.0.2.0/24
* Name tag: MyPublicSubnet01
  * VPC: MyVPC
  * Availability Zone: _choose the first AZ from dropdown_
  * IPv4 CIDR block: 10.0.3.0/24
* Name tag: MyPublicSubnet02
  * VPC: MyVPC
  * Availability Zone: _choose the second AZ from dropdown_
  * IPv4 CIDR block: 10.0.4.0/24
  
:key: Once all the subnets are created, select MyPublicSubnet01 and click on the Subnet Actions dropdown; go to Modify auto-assign IP settings and check Enable auto-assign public IPv4 address box.  Click on Save. 

Repeat the same step for MyPublicsubnet02 as well but do not enable this setting for Private Subnets.

_Why is the available number of IPs showing as 251, where are the rest 5 IPs used?_  
_Why have we created two private and public in different subnets? Should we not create both Public subnets in one AZ and both Private in another AZ?_

### Activity 03 - Create Internet gateway

As you might have noticed, there were similar steps taken in creating the Public and Private subnets, what differentiates them?
A public subnet is the one that has a route to Internet Gateway in its routing table whereas Private Subnets don't. So now let's create an Internet Gateway.
Click on Internet Gateways in the sidebar of VPC Dashboard and then click on Create Internet Gateway.

* Name tag: MyIGW
* Click on Yes, Create.

You will see the state of MyIGW as detached as it is not yet attached to a VPC.  
Select the MyIGW and click on Attach to VPC, select MyVPC from the drop-down in next pop up and click
on Yes, Attach.

_Why was the default VPC not showing in the dropdown._

### Activity 04 - Create Route table (public) and assign to relevant Subnets

Click on Route tables in the side bar, you should see a Route Table already created for you, assigned to MyVPC.

* Click on Create Route Table
  * Name tag: MyPublicRoute
  * VPC: MyVPC
* Click on Yes, Create.

A new route table would have come up now.

While the MyPublicRoute selected, click on Routes tab in the lower half of the screen. You would see that it already has an entry for local traffic. We now should add the route entry meant for non local traffic (Internet).
Click on Edit and then on Add route. Fill in the below details in the new blank route table entry.

* Destination: 0.0.0.0/0
* Target: Internet Gateway (you would see the Internet gateway name in the drop down)

Click on Save routes.

This way we have added an entry to Internet in our public route table, now is the time to assign the route table to our public subnets.

* Click on the Subnet Associations tab right next to the Routes tab.

_You would see that all four subnets that you created are associated with the main route table, why?_

* Click on Edit subnet associations and select the two Public Subnets that you created. Save.

:key: Repeat the above two activities (3 and 4) for creating a NAT Gateway, a Private Route Table, attaching NAT Gateway to Private route table for Internet bound traffic and then assigning this route table to the TWO private subnets.

### Activity 05 - Creating Security Groups

Let us now create different 'Security Groups' for App server, database and load balancer. We would leverage them in coming steps.
In the navigation pane find and click on 'Security Groups'

* Click on 'Create Security Group'
  * Security group name: My-App-SG
  * Description: This SG is to be used for web application servers.
  * VPC: MyVPC
* Click on Create

Similarly create security groups for your DB and Loadbalancer layer.

Select either of the Security Group now and click on 'Inbound Rules' tab.
Click on 'Edit Rules' and add rules for incoming traffic on the security groups like mentioned below.

#### My-App-SG

| Type  | Protocol | Port Range | Source |           |
| :---: | :------: | :--------: | :----: | :-------: |
| HTTP  |   TCP    |     80     | Custom | 0.0.0.0/0 |
| HTTPS |   TCP    |    443     | Custom | 0.0.0.0/0 |
|  SSH  |   TCP    |     22     | Custom | 0.0.0.0/0 |

#### My-DB-SG

|     Type     | Protocol | Port Range | Source |           |
| :----------: | :------: | :--------: | :----: | :-------: |
| MYSQL/Aurora |   TCP    |    3306    | Custom | My-App-SG |
|     SSH      |   TCP    |     22     | Custom | 0.0.0.0/0 |

#### My-ALB-SG

| Type  | Protocol | Port Range | Source |           |
| :---: | :------: | :--------: | :----: | :-------: |
| HTTP  |   TCP    |     80     | Custom | 0.0.0.0/0 |
| HTTPS |   TCP    |    443     | Custom | 0.0.0.0/0 |

For now, our VPC configuration is complete. The instances launched in our public subnets should have outbound access to Internet and the instances in our private subnet should not. We would verify the same in the next section.

## Lab 01 – Part 02 of 03

### Activity 06 - Creating EC2 instances

We are now going to create an EC2 instance as MyAppServer. Let us switch to EC2 Dashboard now and click on Launch Instance.

Creating the App Server

* Amazon Machine Image: "Amazon Linux 2" (free tier eligible)
* Instance Type: t2.micro
* Configure Instance Details: Select the below mentioned points and leave everything else as default.
  * Network: MyVPC
  * Subnet: MyPublicSubnet01

**Expand the Advance Details section and paste the following script in the user data section.**

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
cd /var/www/html
wget https://raw.githubusercontent.com/ashydv/aws-labs/master/index.txt
INSTANCEID=`curl http://169.254.169.254/latest/meta-data/instance-id`
INSTANCETYPE=`curl http://169.254.169.254/latest/meta-data/instance-type`
PRIVATEIP=`curl http://169.254.169.254/latest/meta-data/local-ipv4`
sed -e "s/INSTANCEID/$INSTANCEID/" -e "s/INSTANCETYPE/$INSTANCETYPE/" -e "s/PRIVATEIP/$PRIVATEIP/" index.txt > index.html
```

This script will –

1 - Install an Apache web server and create a Hello World! page.  
2 - Activate the Web server and configure it to automatically start on reboots.  
3 - Read some EC2 instance related data from EC2 metadata and show it on the webpage.  

* Add Storage: Leave defaults
* Add Tags
  * Key: Name
  * Value: MyAppServer
* Configure Security Group: Select existing -> My-App-SG
* Click on Review and Launch.

On the next page check that your AMI is free tier eligible and Instance Type is showing as t2.micro.

* Click on Launch.

On the next window, create a new Key Pair, Key pair name: mykey and then Download Key pair.

Finally click on Launch Instance

We have just launched an EC2 instance in our public subnet as MyAppServer. 

Try browsing the public DNS of the web server, does it open? Yes, because your MyAppServer is in a public subnet, has a public IP and the firewall allows the traffic on port 80 from anywhere. In an ideal scenario, only the Load Balancer should be in public subnet and the app servers should be in Private Subnets. The firewall of EC2 should allow traffic coming from the load balancer and not from anywhere, we will do that in next section. The instance details you see on the webpage is presented by reading the meta-data of the EC2 instance.

Go through the various options under Action drop down. 

After an instance is configured, we can build an image from it for our future usage so we dont have to start from scrach if we want to launch multiple EC2 instances. It can be done going to the Action dropdown, save your Image and create image. You don't have to do it right now.

Terminate the instance.

## Lab 01 – Part 03 of 03

You will now be launching this application using a Launch Configuration into an Auto Scaling Group, the ASG will automatically grow and shrink the number of your servers based on the user defined threshold. The requests to your application will be distributed by Application Load Balancer.

### Activity 07 - Creating an Auto Scaling Group

Go to the Auto Scaling section in your EC2 dashboard and click on Launch Configurations. In the next scree, click on Create launch configuration.

- Launch configuration name: MyAppServer_V01_LC
- Amazon machine image (AMI): Find the AMI ID of Amazon Linux 2 from EC2 launch page and paste here.  
- Instance Type: t2.micro

- In the Additional configuration section, expand the Advance details and paste the User data.
- On the Security groups section, Select an existing security group and choose My-App-SG.
- Click on Create launch configuration
- In the Key pair (login) section, select the existing 'mykey'.
- Acknowledge and click on Create launch configuration.

Your Launch Configuration is created, let us now use this Launch Configuration to create the auto scaling group. Select your newly created Launch Configuration and click on action dropdown, click on Create Auto scaling group.

- Name: MyApp_ASG
- Launch configuration: it is already selected. Click Next.
- Network: Select MyVPC from the dropdown and then selct both of the private subnets from the Subnets dropdown. Click Next.
- Load balancing - optional: ignore everything on this page and click Next.
- Group size: Desired capacity 2, Minimum capacity 2 and Maximum capacity 4.
- Scaling policies: Select Target tracking scaling policy. Click Next.
- Click on Add notification
- Add Notification: Create Topic
- Send a notification to: MyASG_Topic
- With these recipients: 'your email ID'. Click Next. 
- Next Create a Tag with 'Key: Name' and 'Value: MyAppServer'
- Review: Create Auto Scaling group

Click on Close, you would be directed to the Auto Scaling Groups Dashboard. Explore the Activity History and other tabs.

Also check if you received an email from SNS topic, you need to confirm the subscription.

You have just launched our highly available web application in an Auto Scaling Group. You can not browse the application yet as the instances do not have public IPs.

Let us create a Load balancer in public subnets, that will divert the traffic to both these instances in round robin method.

### Activity 08 - Creating an Application Load Balancer

Go to the Load Balancing section of EC2 dashboard and click on Target Group

- Create Target Group
- Target group name: MyTG
- VPC: MyVPC
- Leave rest defaults and click Next.
- Leave everything om this page unchanged and click Create target group.

Let us register our instances in ASG with the MyTG target group. Go to Auto Scaling Groups, select your ASG and click on Edit button on top. Scroll down to find the Load balancing section, click on the first check box and select the target group you created from the dropdown. Go to the bottom of the page and click on Update.

Go to the Load Balancers page and click on Create Load Balancers.

From next screen, create an Application Load Balancer

- Name: MyALB
- Scroll down to the Availability Zones Section
- Select the VPC in which you have launched the ASG
- Select Public Subnets from both AZs. This is a critical step, reconfirm before going forward.
- Next - Configure Security Settings – Ignore the warning, it is recommending to have SSL certificate.
- Next - Configure Security Groups. Select My_ALB_SG from existing ones.
- Next Configure Routing –
- Target group – Existing Target Group
- Name: MyTG
- Leave rest defaults - Register Targets – Review – Create

Click on close and it will take you to the load balancer dashboard, you should see the DNS endpoint (A record) of your load balancer in Description Tab. ALB takes a little time to come up. Refresh till you see the state as active.

Open the DNS address of your ALB in a browser and notice what it shows. It is now diverting the traffic to both your instances. You can see the behavior of load balancer while you refresh the page and notice the instance ID/IP.


### Activity 09 – Modify the Security Groups to ensure security on incoming traffic

Update the **My_App_SG** security group settings as shown below.

#### My_App_SG

| Type  | Protocol | Port Range | Source |           |
| :---: | :------: | :--------: | :----: | :-------: |
| HTTP  |   TCP    |     80     | Custom | My_ALB_SG |
| HTTPS |   TCP    |    443     | Custom | My_ALB_SG |
|  SSH  |   TCP    |     22     | Custom | 0.0.0.0/0 |


You can now try deleting one/more server in order to verify whether the auto scaling feature is able to spin up instances in response.

### Clean up steps –

Delete the resources in the below order

 1: ALB  
 2: Auto Scaling Group (takes a little time to delete, find out why)  
 3: Target Group  
 4: Launch Configuration  
 5: NAT Gateway (takes little time to delete)  
 6: Release Elastice IP


***Apart from NAT Gateway which is charged $0.01 per hour, all the other services used in this lab are eligible and covered within the free tier account. There should be only NAT Gateway charged to you if you delete all the resources within free tier monthly limits.***

✔️ Lab Complete!
