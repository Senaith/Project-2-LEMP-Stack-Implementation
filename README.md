# Project-2-LEMP-Stack-Implementation
This project will demonstrate the implementation of LEMP stack on AWS virtual server.

## What is LEMP Stack?

LEMP refers to a collection of open-source software that is commonly used together to serve web applications. The term LEMP is an acronym that represents the configuration of a Linux operating system with an nginx (pronounced engine-x, hence the E in the acronym) web server, with site data stored in a MySQL database and dynamic content processed by PHP. 

This project will give you a better understanding of what the LEMP stack is and how to implement it on Amazon Web Services (AWS). AWS is the biggest Cloud service provider, and it offers a free tier account that we will be able to utilize for our project. For the purpose of this project, we will be employing EC2 (Elastic Compute Cloud) service.

## Setting up our Virtual Environment

In order to complete this project, we need to begin by setting up an AWS account and a virtual server with Ubuntu Server OS.

Step 1:
Create free AWS account. Instructions for this can be found here. Once you have created your AWS account, navigate to the login page and type in your credentials.


Step 2: After signing-in to your AWS account, navigate to the top-right corner of your screen and select your preferred region. This should be the closest region to your physical location.


Step 3: Proceed to the search bar and type in EC2. Select the EC2 service that appears on top.



Step 4: Click on the orange 'Launch Instances' button that appeears on the top right side of your screen.

Step 5: Choose the Ubuntu Server 20.04 LTS (HVM) as the Amazon Machine Image (AMI) from the list of AMIs provided.

Step 6: Select t2.micro as the instance type and click REVIEW AND LAUNCH.
Step 7: and then on the next page choose LAUNCH.

Step 8: There will be a window asking you to create a key pair. Select the 'Create a new key pair' option from the drop down menu and then select "Download". Make sure you know the location the file was downloaded to and don't lose the .pem file. You will need this file in order to connect into your server from your local PC. After you downloaded the key pair, check the box for the acknowledgement, and then click on "Launch Instances".

Step 9: Woohoo!!! You've successfully launched an EC2 instance!

Click on 'View Instances' to see your EC2 instance.





