# Project-2-LEMP-Stack-Implementation
This project will demonstrate the implementation of LEMP stack on AWS virtual server.

## What is LEMP Stack?

LEMP refers to a collection of open-source software that is commonly used together to serve web applications. The term LEMP is an acronym that represents the configuration of a Linux operating system with an nginx (pronounced engine-x, hence the E in the acronym) web server, with site data stored in a MySQL database and dynamic content processed by PHP. 

This project will give you a better understanding of what the LEMP stack is and how to implement it on Amazon Web Services (AWS). AWS is the biggest Cloud service provider, and it offers a free tier account that we will be able to utilize for our project. For the purpose of this project, we will be employing EC2 (Elastic Compute Cloud) service.

## Setting up our Virtual Environment

In order to complete this project, we need to begin by setting up an AWS account and a virtual server with Ubuntu Server OS.

Step 1:
Create free AWS account. Instructions for this can be found here. Once you have created your AWS account, navigate to the login page and type in your credentials.

![step1](https://user-images.githubusercontent.com/91766546/155834553-450930ad-5f7e-4bdd-943d-f4db1b92bfba.png)


Step 2: After signing-in to your AWS account, navigate to the top-right corner of your screen and select your preferred region. This should be the closest region to your physical location.

![step2](https://user-images.githubusercontent.com/91766546/155834557-142107f5-955e-4d04-a516-51bf2392018f.png)

Step 3: Proceed to the search bar and type in EC2. Select the EC2 service that appears on top.

![step3](https://user-images.githubusercontent.com/91766546/155834559-4a3089bf-65f3-4f38-8635-19184710dc3c.png)

Step 4: Click on the orange 'Launch Instances' button that appeears on the top right side of your screen.

![step4](https://user-images.githubusercontent.com/91766546/155834574-b3e54074-a173-4beb-a175-ad8917a2b60e.png)

Step 5: Choose the Ubuntu Server 20.04 LTS (HVM) as the Amazon Machine Image (AMI) from the list of AMIs provided.

![step5](https://user-images.githubusercontent.com/91766546/155834580-e1b74153-512c-4e81-8560-47c4c0f561a8.png)

Step 6: Select t2.micro as the instance type and click REVIEW AND LAUNCH.

![step6](https://user-images.githubusercontent.com/91766546/155834601-ec758529-4a63-44ef-8032-f3ddd23c35ce.png)

Step 7: and then on the next page choose LAUNCH.

![p1](https://user-images.githubusercontent.com/91766546/155834650-e44e311a-17e3-4a06-987f-0197ebd4694a.png)

Step 8: There will be a window asking you to create a key pair. Select the 'Create a new key pair' option from the drop down menu and then select "Download". Make sure you know the location the file was downloaded to and don't lose the .pem file. You will need this file in order to connect into your server from your local PC. After you downloaded the key pair, check the box for the acknowledgement, and then click on "Launch Instances".

![p2](https://user-images.githubusercontent.com/91766546/155834655-c5391d62-3547-4bad-afb1-eb9010e73e6d.png)


Step 9: You've successfully launched an EC2 instance!

![p3](https://user-images.githubusercontent.com/91766546/155834668-d78aea6a-e98c-4c83-9158-c44807f2071f.png)

Click on 'View Instances' to see your EC2 instance.

![p4](https://user-images.githubusercontent.com/91766546/155834679-05caea34-31ca-4f58-8e6e-36cee64a6511.png)

## Connect your AWS EC2 server to your local PC via SSH
Step 1: On your local Linux machine, change your working directory to the location where your downloaded key pair .pem file exists. And use the 'ls' command to check if the file exists in that folder.

![p0](https://user-images.githubusercontent.com/91766546/155849605-9c2e68fb-470b-4002-90b6-60153c380ba7.png)

Step 2: Use the following commang to change the premissions for the private key file (.pem), otherwise you can get an error 'Bad permissions'.

![p7](https://user-images.githubusercontent.com/91766546/155849744-c2e2da1c-fb32-4b51-bc6e-f04fccce84e0.png)

Step 3: Get your public IP address from your instance.

![p65](https://user-images.githubusercontent.com/91766546/155849685-98b3f31c-d858-4080-b9ac-fb37d802b521.png)

Step 4: Connect to your EC2 instance by running the following command.

![p6](https://user-images.githubusercontent.com/91766546/155849734-8b06d67c-10b0-4218-8e5c-3620a0d70988.png)

When connected, your ip-address will be shown on your terminal.

![p8](https://user-images.githubusercontent.com/91766546/155849871-4f705ba5-d6cc-474d-ae88-47da318b81ca.png)

## Installing the Nginx Web Server

### What is Nginx?

NGINX (pronounced "engine X", stylized as NGINX, nginx or NginX, is open source software for web serving, reverse proxying, caching, load balancing, media streaming, and more. It started out as a web server designed for maximum performance and stability. In addition to its HTTP server capabilities, NGINX can also function as a proxy server for email (IMAP, POP3, and SMTP) and a reverse proxy and load balancer for HTTP, TCP, and UDP servers.

Step 1:
Start off by updating your server’s package index. 

![p9](https://user-images.githubusercontent.com/91766546/155850963-27332fba-9769-4049-97cb-343a7cc8ce17.png)

Step 2:
Next, you can use the following command to get Nginx installed.

![p10](https://user-images.githubusercontent.com/91766546/155850995-5a4dd2b4-d861-4111-b402-96d882446453.png)

You will be prompted to confirm your installation enter Y using your keyboard.

![p11](https://user-images.githubusercontent.com/91766546/155851055-bf520064-52a6-4ab6-b4c9-f3e2153fd7f9.png)

Step 3:
To verify that your installation was successful and Nginx is now running on your Ubuntu server run the follwing command on your terminal.

![p17](https://user-images.githubusercontent.com/91766546/155851338-621904f9-e231-4500-8f03-3139c32dca19.png)

The result should look like this if your installation is working perfectly.

![p18](https://user-images.githubusercontent.com/91766546/155851365-4c0adc48-3ea8-4a9c-ae8e-2a18300ef93b.png)

If it is green and running, then you did everything correctly - you have just launched your first Web Server in the Clouds!

Step 4: 
Before we can receive any traffic by our Web Server, we need to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet. We have TCP port 22 open by default on our EC2 machine to access it via SSH, so we need to add a rule to EC2 configuration to open inbound connection through port 80:

Open your AWS Management Console and Click on your EC2 instance. Click on the 'Security' tab.

![p12](https://user-images.githubusercontent.com/91766546/155853304-c62940c6-70f3-4130-aadc-b09574432004.png)

Step 5: 
Click on the link under the 'Securty Groups'. You will open a page similar to this one.

![p13](https://user-images.githubusercontent.com/91766546/155853367-0f380ed5-b4cd-41b2-b595-a75c2708af8f.png)

Next, click on 'Edit Inbound Rules' box found on the bottom right side of your screen.

Step 6: 
Click on 'Add Rule' and add the HTTP, TCP port 80 and allow source from anywhere by using 0.0.0.0

![p14](https://user-images.githubusercontent.com/91766546/155853490-46eafd0a-77df-475b-b9d8-ec501ddd5f3d.png)

![p15](https://user-images.githubusercontent.com/91766546/155853498-399def63-9090-4d69-b9cd-f16aa3af1670.png)

![p16](https://user-images.githubusercontent.com/91766546/155853510-dbbb69e6-44fa-444c-8102-be458b02d923.png)

Step 7: 
Our server is running and we can access it locally and from the Internet (Source 0.0.0.0/0 means 'from any IP address'). First, let us try to check how we can access it locally on our Ubuntu shell, run 'curl http://localhost:80' command.

![p19](https://user-images.githubusercontent.com/91766546/155853687-11189bf1-ca40-4c02-a318-9cc956e4fb2f.png)

![p20](https://user-images.githubusercontent.com/91766546/155853756-be2be616-0993-4716-a947-5aa3f1a2f2bd.png)

Step 8:
Now it is time for us to test how our Nginx server can respond to requests from the Internet. Open a web browser of your choice and try to access following url ***'http://Public-IP-Address:80'*** Replace the ***'Public-IP-Address'*** with the public IP address of you AWS EC2 server. You should be able to see this page displayed on your screen.
  
 ![p21](https://user-images.githubusercontent.com/91766546/155853928-256e20dc-37f8-4c9d-b267-928b3ee38cb0.png)

Your web server is now correctly installed and accessible through your firewall.

## Installing MySQL Server

Now that we have your Nginx server up and running, you need to install a Database Management System (DBMS) to be able to store and manage data for your site in a relational database. MySQL is a popular relational database management system used within PHP environments.

Step 1: 
Use ‘apt’ to acquire and install this software.

![p22](https://user-images.githubusercontent.com/91766546/155854078-cd8c36d8-d58f-4e0b-92d1-82240564105c.png)

Hit the Y key and ENTER when this prompt appears on your screen.

![p23](https://user-images.githubusercontent.com/91766546/155854094-ee10c9a2-c86a-4c12-b3cb-454a5ddff455.png)

Step 2: 
Next, run security script to remove insecure default settings and lock down access to your database system. Start the interactive script by running:

![p24](https://user-images.githubusercontent.com/91766546/155854160-4d0706f4-e028-429c-9c39-031124279e5e.png)

This will ask if you want to configure the VALIDATE PASSWORD PLUGIN. Answer Y for yes, or any other key to continue without enabling. I recommend not enabling this plugin for now and proceed by pressing N or any other key on your keyboard to go to the next step.

![p25](https://user-images.githubusercontent.com/91766546/155854174-02c8c8f9-f862-4b7a-bfd7-edb16dd59cb7.png)

![p26](https://user-images.githubusercontent.com/91766546/155854181-e62540c4-88f2-4684-a170-d9e62b21866b.png)

Your server will next ask you to select and confirm a password for the MySQL root user (The database root user is an administrative user with full privileges over the database system.)

Step 3: 
By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. You should remove this by typing 'Y' for each prompt that follows.

![p27](https://user-images.githubusercontent.com/91766546/155854215-db5408e7-3e3e-4167-890c-d615bf2143f6.png)

Step 4: 
check whether you can log in to the MySQL console.

![p28](https://user-images.githubusercontent.com/91766546/155854236-c8c2e0e5-678f-4e58-a05d-62b28e282500.png)

To exit MySQL console, run:

![p29](https://user-images.githubusercontent.com/91766546/155854257-cd29f2f8-daf0-445a-aa1a-0090759a81e1.png)

Your MySQL server is now installed and secured. Next, we will install PHP, the final component in the LEMP stack.

## Installing PHP

You have Nginx installed to serve your content and MySQL installed to store and manage your data. Now you can install PHP to process code and generate dynamic content for the web server.

PHP is a script on the server-side used for the creation of Static or Dynamic Web sites or Web applications. PHP is a pre-processor for hypertext, which used to stand for home pages. The software used to build web applications is an open-source, server-side scripting language. We say a program designed for automated work by writing a script-based language (code lines). It is suitable for the output and construction of dynamic web pages for web applications, e-commerce applications, and database applications.

Let's begin the installation.

To start with, run these two commands at once on your terminal.

![p30](https://user-images.githubusercontent.com/91766546/155854366-2a9492ce-19d1-4973-bc99-2d8b5e175d44.png)

Confirm Y for Yes when the prompt appears.

![p31](https://user-images.githubusercontent.com/91766546/155854386-2b554059-81b7-4103-a69f-99bbb4c45b75.png)

You now have your PHP components installed. Next, you will configure Nginx to use them.

## Configuring Nginx to Use PHP Processor

In this project, we will set up a domain called 'projectLEMP', but you can replace this with any domain of your choice.

Step 1:
On Ubuntu 20.04, Nginx has one server block enabled by default and is configured to serve documents out of a directory at `/var/www/html`. While this works well for a single site, it can become difficult to manage if you are hosting multiple sites. Instead of modifying `/var/www/html`, we’ll create a directory structure within `/var/www` for the **your_domain** website, leaving `/var/www/html` in place as the default directory to be served if a client request does not match any other sites.

Create the directory for projectLEMP using 'mkdir' command

![p32](https://user-images.githubusercontent.com/91766546/155854494-70cc56e7-09a0-4e1c-8943-345c59af65f2.png)

Step 2: 
Next, assign ownership of the directory.

![p33](https://user-images.githubusercontent.com/91766546/155854530-eff88dec-f991-4c19-89aa-bcf4e98a8256.png)

Step 3:
Open a new configuration file in Nginx’s sites-available directory using your preferred command-line editor. For this project we will use nano.

![p34](https://user-images.githubusercontent.com/91766546/155854609-fa8c4115-c25a-4b20-9439-13ec1708a75b.png)

This will create a new blank file where you can write the following configurations.

![p35](https://user-images.githubusercontent.com/91766546/155854636-fd73d54a-e2f2-41a4-8f67-d4b27a44a03e.png)

Once you are done editing enter ctrl+X the press the Y key followed by the Enter key to exit the nano editor.

Step 4:
Activate your configuration by linking to the config file from Nginx’s sites-enabled directory.

![p36](https://user-images.githubusercontent.com/91766546/155854723-1fa975d5-ae05-4a4d-a9b6-b32bb729de9f.png)

Step 5:
Test your configuration for syntax errors by running the following command.

![p37](https://user-images.githubusercontent.com/91766546/155854761-2173f242-b4ba-4204-9d02-38e5d12d631f.png)

You should see something like this on your screen.

![p38](https://user-images.githubusercontent.com/91766546/155854766-8126b8f7-52f1-40fd-b6b4-867bc713c7f4.png)

Step 6:
We also need to disable default Nginx host that is currently configured to listen on port 80.

![p39](https://user-images.githubusercontent.com/91766546/155854817-c230ee03-a68d-4425-8672-50c44aea1c55.png)


Step 7:
Reload Nginx to apply the changes.

![p40](https://user-images.githubusercontent.com/91766546/155854837-a50ac7f1-5d3e-465a-955d-a89a0d689d81.png)

Step 8:
Congratulations! Your new website is now active!!!
But the web root /var/www/projectLEMP is still empty. Create an index.html file in that location so that we can test that your new server block works as expected.

![p41](https://user-images.githubusercontent.com/91766546/155854869-88ebbea5-37ca-49aa-bfe3-92c3651bc81e.png)

Step 9:
Now go to your browser and try to open your website URL using IP address. You should see a screen similar to this one on your browser.

![p42](https://user-images.githubusercontent.com/91766546/155854963-17a417e1-470b-4f80-a1c5-8a71e772bb54.png)

## Testing PHP with Nginx

Your LEMP stack is now completely set up. Good job!!!

You can test it to validate that Nginx can correctly handle .php files off to your PHP processor. You can do this by creating a test PHP file in your document root. Open a new file called info.php within your document root in your text editor.

![p44](https://user-images.githubusercontent.com/91766546/155855116-0f9e3a5a-a7f2-499a-b03b-c264fa4bb553.png)

This will open a blank file. Add the following text, which is valid PHP code, inside the file.

![p45](https://user-images.githubusercontent.com/91766546/155855152-2e46fbfa-869a-47c5-a3bc-57c4366f3168.png)

Once you are done editing enter ctrl+X the press the Y key followed by the Enter key to exit the nano editor.

You can now access this page in your web browser by visiting the domain name or public IP address you’ve set up in your Nginx configuration file, followed by /info.php:

![p46](https://user-images.githubusercontent.com/91766546/155855295-ec27a249-0869-4994-9829-2bac9562b90d.png)

After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server.

![p47](https://user-images.githubusercontent.com/91766546/155855398-547a57d5-1aa2-4627-9af2-e3b95f92a3b7.png)

You can always regenerate this file if you need it later.

## Retrieving data from MySQL database with PHP

Let's create a test database (DB) with simple “To do list” and configure access to it, so the Nginx website would be able to query data from the DB and display it. We will create a database named **example_database** and a user named **example_user**, but you can replace these names with different values.

Step 1:
connect to the MySQL console using the 'root' account.

![p48](https://user-images.githubusercontent.com/91766546/155855491-98e60b22-c585-4afd-ab6e-ac44eafe9dd6.png)

Step 2:
To create a new database, run the following command from your MySQL console.

![p50](https://user-images.githubusercontent.com/91766546/155855563-f552e1b0-6038-4d20-9098-d772b04136f7.png)

Step 3:
create a new user and grant him/her full privileges on the database you have just created.

![p51](https://user-images.githubusercontent.com/91766546/155855603-7756fadb-4907-4f33-ab7d-f96e84722a93.png)

Step 4:
Give this user permission over the 'example_database' database.

![p52](https://user-images.githubusercontent.com/91766546/155855629-877563b5-6d1d-4630-85bc-e47648ddb0ec.png)

Step 5:
Exit from the MySQL console and Test if the new user has the proper permissions by logging in to the MySQL console again using the custom user credentials.

![p53](https://user-images.githubusercontent.com/91766546/155855724-a146dd0f-5543-49d1-9e0a-4e4a7b4b326b.png)

![p54](https://user-images.githubusercontent.com/91766546/155855725-ba4f1188-af23-4759-9462-dd2522b3ea90.png)

This will prompt you for the password used when creating the example_user user. 

![p55](https://user-images.githubusercontent.com/91766546/155855736-ad2e55bb-f6d5-4de2-8be7-a1a637a8224c.png)

Step 6:
After logging in to the MySQL console, confirm that you have access to the example_database database.

![p56](https://user-images.githubusercontent.com/91766546/155855781-6d7a1e01-dee7-42df-8070-c21273af6543.png)

This will give you the following output.

![p57](https://user-images.githubusercontent.com/91766546/155855797-b1a5bfaf-c26b-48bd-878f-5b6d4f8ca17c.png)

Step 7:
Next, we’ll go ahead and create a test table named todo_list. Run the following statement from your MySQL console.

![p59](https://user-images.githubusercontent.com/91766546/155855842-8d71b694-a9a6-48b9-aab2-bf5ad4e1bdd2.png)

Step 8:
Insert a few rows of content in the test table. And repeat the next command a few times, using different VALUES.

![p61](https://user-images.githubusercontent.com/91766546/155855974-40b339d6-961a-4536-a6d4-ca124a0302ab.png)

Step 9:
Exit the MySQL console after confirming that the data was successfully saved to your table.

![p62](https://user-images.githubusercontent.com/91766546/155856078-346dfee9-1407-439d-8935-23c0f109fcc8.png)

Now you can create a PHP script that will connect to MySQL and query for your content. 

Create a new PHP file in your custom web root directory using nano.

![p66](https://user-images.githubusercontent.com/91766546/155856198-5de25b97-7b2b-4412-9710-762e86d31fd5.png)

![p63](https://user-images.githubusercontent.com/91766546/155856213-1710e83e-6c62-4495-9a59-df4b4291ef12.png)

Save and close the file when you are done editing.

You can now access this page in your web browser by visiting the domain name or public IP address configured for your website, followed by /todo_list.php.
If you see a page like this, showing the content you’ve inserted in your test table, your PHP environment is ready to connect and interact with your MySQL server.

![p64](https://user-images.githubusercontent.com/91766546/155856248-136e0f90-3e24-4891-8b2d-bbae51c8c05d.png)

#### Congratulations! You have successfully built a flexible foundation for serving PHP websites and applications to your visitors, using Nginx as web server and MySQL as database management system.

This brings us to the end of this project.



