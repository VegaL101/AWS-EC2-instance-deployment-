# AWS-EC2-instance-deployment-

## Objective

The purpose of this project is to create, configure, and launch a AWS EC2 instance to deploy a wordpress website through it. This guide will cover every step in detail, ensuring a proper and complete setup. In this project we will be using SSH on a Ubuntu VM to connect to our instance. If you are on windows make sure to have a SSH client for this project.

### Skills Learned

- Create a AWS EC2 instance.
- Connect to the instance remotely.
- Deploy a wordpress website.
- create a MYSQL database for your website.
- Use certbot to activate HTTPS securing and protecting our website .
  


## Steps


Step 1:
Creating and launching the EC2 instance.

First after Creating an AWS account and logging in, you should be at the main console menu. On the top left in the searchbar type 'EC2' and make sure to click it once you've found it in the search bar. You should then be brought to the ec2 dashboard

![ec2 dahsboard](https://github.com/user-attachments/assets/6a5285f9-6494-4b57-8aa8-68e3ce62862a)

Once at the dashboard you're going to click on the 'launch instance' button that will take you to the next part of this step.

##

Next, we set up our instance.

![launch an instance display](https://github.com/user-attachments/assets/7683e5f6-d44c-4b93-848f-6c5ed408ebfd)


Here we will give our instance a name and choose an OS image for it. For this project we will be using the UBuntu OS image.

##

We then give it a key pair, choose the instance type, and configure its network setttings to the same as below.
It is crucial you give your instance a keypair for security reasons. Letting you access your instance securely.

![fill ins for instance](https://github.com/user-attachments/assets/f55d31bd-ad35-4991-86cf-9cf423421f7f)

## 
Once you've clicked on 'create new keypair' you give it a name, choose the pair type and choose the key file format. Once created the key will be downloaded onto your device. Make sure to keep this key secured.

![key pair](https://github.com/user-attachments/assets/5a50047a-b9c3-4454-8402-136e5ed1d7d7)

##
Next, make sure you allow traffic from ssh, https, and http so you can access your instance. After, you can configure the storage which i leave as default.

![network settings](https://github.com/user-attachments/assets/038ae014-00cd-4716-9726-e84d5ae9f949)

##

Next, we can launch the instance which might take a while before its up and running. 

![instance launched](https://github.com/user-attachments/assets/cbf99c48-d22b-4876-8b0b-bf65aace6149)

Once its done launching we can go back to our instance from our dashboard and see that it is running.

##

Now we will allocate our IP address if we dont do this everytime we reboot our instance our ipv4 address will change. We want our ip address to be static. So we go back to our EC2 dashboard and click on Elastic IP addresses and then click on the orange button the top right corner of the screen.<br>
Leave evrything as the default when Allocating a ip address and hit 'Allocate' on the bottom.


![allocate ip](https://github.com/user-attachments/assets/f6fa6e77-8411-46a4-9f20-6515dc51891e)

##

Now that you've created a new ip address. You may select it, click on the actions drop down, and click on 'Associate Elastic IP address' and then procceed to choose your instance that we created earlier and click on 'Associate'.<br>
If done correctly your Instance will now be associated with your elastic ip address. To check this, you can go back to your instance and it should have your public IPv4 address updated.

![connect to instance](https://github.com/user-attachments/assets/f2f77d57-4dcf-4bb4-8eb2-05a744419690)

##

Now for the final part of this step we will be connecting to our instance via SSH. For this  i will be using my Ubuntu VM. If you are using windows you may have to use a SSH client.<br>

Firstly, we need to find our PEM file which is our key we created earlier. To do this go to our terminal and type in the 'ls' command to bring up all the directories. After, type in 'cd Downloads' which will take me to that directory where i have my key stored. I then type 'ls' again and any files or directories i have in there will appear. 

![how to find pem file](https://github.com/user-attachments/assets/378ab2d7-0389-46c3-b667-78015c03032b)

##

Once we have our key we'll copy and paste it with this command below in order to remotley access our instance. we use: ssh -i "(paste pem file here)" ubuntu@(elastic ip address). if everything is correct it should look similar to the image below. 

If it fails you may have to change the permissions using the command 'chmod 400'.

![ssh connect image](https://github.com/user-attachments/assets/9ee83275-0ce6-4698-bf80-d778a18231b1)

##

 Step 2:
 Creating our wordpress website

In step two we will install apache web server on our instance. To do this we run the command: sudo apt install apache2 .<br>
Should look similar to down below. Now on your web browser you can type in your elastic  

![install apache web server on instance](https://github.com/user-attachments/assets/29829e5e-a555-4f37-b57b-449f91b717ed)

##

 Now on your web browser you can type in your elastic ip address and look up your website which should look like below (for now).

 ![lamp-stack-ubuntu-22 04-768x949](https://github.com/user-attachments/assets/8c342f4d-242b-4df4-acde-25f723f996a9)

##

Now after checking that we can go back to our terminal to continue this step.<br>

since wordpress is built on PHP we need to install PHP runtime and MYSQL connector for PHP so that they may work together.<br> The command for this is: sudo apt install php libapache2-mod-php php-mysql <br> same as the image below.
 
![install php runtime (word press is built on php)](https://github.com/user-attachments/assets/c50764b4-6923-4165-a6b7-5bfea2d62816)

##

Next we install MYSQL sever for our database so we put in the command: sudo apt install mysql-server

![mysqlerver(for database)](https://github.com/user-attachments/assets/b1be628f-d05c-40d6-8698-d330db9acd7d)

##

One quick configuration we have to make on our mysql server is to change our mysql authentication plugin to a native password.
We use the command: sudo mysql -u root<br> this lets us connet to our mysql prompt as a root user 

![configure mysql server](https://github.com/user-attachments/assets/9e8d7aa4-fc4b-445d-88cc-1c73337c4e03)

##

Now we type in the command: alter user 'ROOT'@LOCALHOST iDENTIFIED WITH my sql_native_password BY '(your password)'; <br>

Make sure to creare a strong password as i use a very simple and easy to guess password for the sake of this project.

![SQLCREATEPASSWORD](https://github.com/user-attachments/assets/e9a4172a-548d-463e-9415-40f36ceafb48)

##

Next to create a new user for my sqlserver other than the root user and to do this we type in: CREATE USER 'wp_user'@localhost IDENTIFIED BY '(password you created)'

![createmysqluser](https://github.com/user-attachments/assets/6bbe2622-bb2d-4d6a-8e9d-2fa9a3745d5e)

##

next we need to create a seperate database for our website and we call it 'wp'. I type in: CREATE DATABASE wp;

![seperate db to use w WP](https://github.com/user-attachments/assets/3b60a47d-be8d-4dd4-ac5c-fb74097949ce)

##

Next we give all the privileges in this database to the user we just created. We do this by typing: GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost; <br> After this we should be done with making configurations for mysql server so we hold 'ctrl' and 'd' to exit of the mysql prompt.


![all priviliges of wp to user](https://github.com/user-attachments/assets/9ab53862-fb5f-4b8b-84fc-3159d1a85d9e)

##

Now whats left is to actually install wordpress. So we'll go to the wordpress website and go to their releases linked <a href=https://wordpress.org/download/releases/>Here<a/>, Here we will copy the link of the latest released 'tar.gz' file.

now we go back to our terminal and input: cd /tmp <br> which will change our directories and now we can type: wget (link of the tar file) <br>
should look similar to below.

![wget wordpress](https://github.com/user-attachments/assets/31d05ea2-a5bc-4788-9cb8-ff30d5341960)

##

Now type in 'ls' to find our file and to unzip the file we just input the command: tar -xvf (the file you downloaded) <br>
After this type in 'ls' again and you should see a new folder called wordpress.

![find and unzip tar](https://github.com/user-attachments/assets/f79b3cf7-8990-4077-af98-369261fc4fbf)

##

We then need to move this folder into the document root of apache. So we type: sudo mv wordpress/ /var/www/html/ <br>
which should move it. To verify it did so correctly we type: cd /varwww/html/

![move wordpress to root of apache](https://github.com/user-attachments/assets/ace29919-7d4b-400f-b944-2576b6f5e8d3)

##

We now go back to our website, type '/wordpress. after your ip address and reload the page and if everything has been done correctly you should be taken to the wordprerss installation screen. We then click on 'Let's go!' to continue.

![installation of wordpress](https://github.com/user-attachments/assets/142e30c0-27e6-4bb0-8e6c-955c6337a901)

##

Here we configure our database information but after clicking 'submit' You will be met with an error.  

![wp setup config](https://github.com/user-attachments/assets/1e449fa5-9ca9-4c5e-af4a-48e2b5c35d47)

##

The error will say 'unable to write to wp-config.phpfile.' so we will copy the entire code below, go to our wordpress directory and type in: nano wp-config.php <br>
we do this to create a new file in our directory and to past all the code we just copied from before into this file. After doing so the file should look like the image below and if everything looks correct we can now save the file.

![config file paste](https://github.com/user-attachments/assets/2690ad2b-fcbb-4393-8505-8d8f3aa33352)

##

 We come back to our browser and we can continue you to 'run installation'. If what appears next looks like the screenshot below that means our error has been resolved.<br> 
 Here we fill out our website information i have a simple password as an example for this project but it is important that you employ strong password practices. <br>
 Once everything is filled we click on 'Install Wordpress' to continue.

![install wordpress(after file config)](https://github.com/user-attachments/assets/eead5197-2e20-4a9c-9327-4112b57ad19c)

##

Here we can now click ' login' which will take you to your login admin page.

![wordpressdashboardlogin](https://github.com/user-attachments/assets/8eec39f0-f4d7-48bd-9733-3dd09fbd2466)

##

Next, we login which will take us to our wordpress dashboard. and go back to wordpress to see our updated website. Everything should be at default until you begin to make changes. 

![default wordpress website(actual site)](https://github.com/user-attachments/assets/bf7ccb9a-5b00-4dff-af59-7d1df3721017)

##

Once at the dashboard. We wanna go to settings on the bottom left and click on 'General'. Which will show the screen below 

![general settings  domain changes](https://github.com/user-attachments/assets/681b99d6-c162-4778-80e5-ebd79bc12e91)

##

Before we proceed on wordpress, Now is the time to create a domain. There are many domain name services some are free but i would reccommend a paid one. Once we we have our domain We wanna make sure to create a 'A' type record that points to our IP address and has a 'TTL' of 60.
<br>
i have no specific screenshots to share as this part entirely depends on the service you use.
Although in my example i have created my domain using Hostinger.

##

Now that you have your domain name and have added a 'A' type record we'll go back to our terminal and and type: cd /etc/apache2/sites-available <br> to change our directory and the type: ls<br>
to find our '000-default.conf' file<br>
Here we can modify our file so we can add two new fields. One will be 'ServerName (your website)' and the other 'ServerAlias www.(your website)'. We then save and exit the file and if done correctly it will look like image below. In this project my websited is 'www.mywpsample.tech'.

![servernameserveralias](https://github.com/user-attachments/assets/5579620e-5e4b-41bd-9893-c191b8cb7350)

##

Next, you wanna restart apache so our chnages take in effect. We do this by typing the command: sudo systemctl restart apache2 <br>
as shown below:

![restart apache after default change](https://github.com/user-attachments/assets/2d4e734f-ff6e-45a0-b329-cdace4a04146)

##

Now, back onto our wordpress settings we fill out 'WordPress Address' and 'Site Address' with our website address. Make sure to leave in the 'http://' before your address.<br>
you can see my websites address down below as an example.

![general settings  domain changes](https://github.com/user-attachments/assets/f8f02bea-21dd-468a-99a6-83b59f2754b8)

Once you have your domain, make sure to add it just as i did in my example and to save your changes at the bottom. When you click save your website will temporarily be broken but we will be applying the fix for this in the next part of the step

##

Now in this part of the step we fix our website and get rid of wordpress as a subpath on our website and instead have our website address take us directly to our wordpress website.<br>

We wanna go back to our terminal and type: cd /etc/apache2/sites-available <br> to change our directory and the type: ls<br>
to find our '000-default.conf' file and open it up with the command: sudo nano-default.conf

![set wordpress as default ip from apache default](https://github.com/user-attachments/assets/13f2bcf7-4ffa-47a4-b1a1-ea93f60c59ec)

Once inside the file we look for our Documentroot and add '/wordpress' at the end of 'html' the whole thing should be typed out as: /var/www/html/wordpress<br>
once changed you can save your changes and exit.

##

After these changes we can restart apache2 to update it. We type: sudo systemctl restart apache2

![restart apache after default change](https://github.com/user-attachments/assets/b1c13000-58ff-4a53-aaf4-7cd9bcf8e48b)

##

Once we have done that we can come back and refresh our page if done correctly our wordpress website will appear by default. 

![default wordpress website(actual site)](https://github.com/user-attachments/assets/a74bc03d-574c-4de0-98cb-0f82594289ef)

##

Step 3:

On this final step we'll be wrapping up this project. Now that we have finally created our website, we now must make sure our website is secured. You might have seen that our website so far is using 'http' and not 'https' which is what we really want. <br> The difference is https typically uses port 443 which encrypts data using SSL/TLS, providing a secure and safe channel for communication. Also, https Utilizes digital certificates to authenticate the server, helping ensure that users are communicating with the intended website.

with only http we are left unsecured and users become vulnerable to several types of attacks such as: <br>

- Man-In-The-Middle (MITM) attacks: Where communication between the user and the website can be intercepted by an attacker, allowing them to modify or steal information <br>
- Eavesdropping: Since data is transmitted in plain text, attackers can intercept and read the data being exchanged between the client and server.<br>
- Phishing Attacks: HTTP sites lack authentication mechanisms, making it easier for attackers to create spoofed sites that appear legitimate, tricking users into providing sensitive information.<br>

And several more attacks and security issues.

##

To make our website secured, we will be using a tool called certbot. Certbot is a free, open-source tool that helps you easily get and renew SSL/TLS certificates from Let's Encrypt. It makes it simple to enable HTTPS on websites.<br>
To install certbot we go to our terminal and type in the command: sudo apt install certbot python3-certbot-apache<br>
Example below.

![certbotinstall](https://github.com/user-attachments/assets/d39230fd-f602-4d1d-9255-a3e1e7f30e03)

##

Now to run certbot we type the command: sudo certbot --apache <br> 
It will probably ask you to enter your email address and to aggree to the terms of service. After doing so we are presented with our websites we've created and we are asked 'Which names would you like to activate HTTPS for?'. We leave the option as blank and hit enter to start the process. <br>
Make sure everything looks similar to the image below.In my example above i only activated  HTTPS on one of my domains but make sure you do both options when doing so.

![certbot success](https://github.com/user-attachments/assets/171006eb-601b-4900-9d18-27889e221477)

If the certificates have been deployed successfully you should get a message saying saying 'successfully received certificate' or along those lines. After this we can go back to our website and check our site. You can confirm that your website is secure if you see "HTTPS" in the address bar or a padlock icon on the left side of the URL. This shows that your site is now protected and secure.
##

Summary: 

In this project, we explored the fundamentals of creating and configuring an AWS EC2 instance for hosting a WordPress website. We learned how to install essential components for our website and how to set up and run WordPress effectively. Finally, we implemented Certbot to establish a secure channel for communication, ensuring our website is safe and reliable.





