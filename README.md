# AWS-EC2-instance-deployment-

## Objective

The purpose of this project is to create, configure, and launched a AWS EC2 instance to deploy a wordpress website through it. The goal of this project is to guide you through the process of creating, configuring, and launching an AWS EC2 instance for deploying a WordPress website. This guide will cover every step in detail, ensuring a proper and complete setup.

### Skills Learned

- Create a AWS EC2 instance.
- Connect to the instance remotely.
- Deploy a wordpress website.
- create a MYSQL database for your website.
- give the website a domain and secure it.
  


## Steps


Step 1:
Creating and launching the EC2 instance.

First, on the top left in the searchbar type 'EC2' and make sure to click it. You should then be brought to the ec2 dashboard

![ec2 dahsboard](https://github.com/user-attachments/assets/6a5285f9-6494-4b57-8aa8-68e3ce62862a)

Once at the dashboard you're going to click on the 'launch instance' button that will take you to the next part of this step.

##

Next we set up the instance.

![launch an instance display](https://github.com/user-attachments/assets/7683e5f6-d44c-4b93-848f-6c5ed408ebfd)


Here we will give our instance a name and choose an OS image for it.

##

Here give it a key pair, choose the instance type, and configure its network setttings.
It is crucial you give your instance a keypair for security reasons. Letting you access your instance securely.

![fill ins for instance](https://github.com/user-attachments/assets/f55d31bd-ad35-4991-86cf-9cf423421f7f)

## 
Once you've clicked on 'create new keypair' you give it a name, choose the pair type and choose the key file format. Once created the key will be downloaded onto your device. Make sure to keep this key secured.

![key pair](https://github.com/user-attachments/assets/5a50047a-b9c3-4454-8402-136e5ed1d7d7)

##
Next make sure you allow traffic from ssh, https, and http so you can access your instance. After you can configure the storage which i leave as default.

![network settings](https://github.com/user-attachments/assets/038ae014-00cd-4716-9726-e84d5ae9f949)

##

Next, we can launch the instance which might take a while before its up and running. 

![instance launched](https://github.com/user-attachments/assets/cbf99c48-d22b-4876-8b0b-bf65aace6149)

Once its done launching we can go back to our instance from our dashboard and see that its running.

##

Now we will allocate our IP address if we dont do this everytime we reboot our instance our ipv4 address will change which is what i dont want. We wanna go back to our EC2 dashboard and click on Elastic IP addresses and then click on the orange button the top right corner of the screen.<br>
Leave evrything as the default when Allocating a ip address and hit 'Allocate' on the bottom.


![allocate ip](https://github.com/user-attachments/assets/f6fa6e77-8411-46a4-9f20-6515dc51891e)

##

Now that you've created a new ip address you may select it and click on the actions drop down and click on 'Associate Elastic IP address' and then procceed to choose your instance that you created and click on 'Associate' down below.<br>
If done correctly your Instance will now be associated your ip elastic ip address. To check this, you can go back to your instance and it should have your public IPv4 address updated.

![connect to instance](https://github.com/user-attachments/assets/f2f77d57-4dcf-4bb4-8eb2-05a744419690)

##

Now for the final part of this step we will be connecting our instance via SSH. For this part i will be using my Ubuntu VM to connect to my instance. If you are using windows you may have to use a SSH client.<br>

Firstly i need to find our PEM file which is our key key we created earlier. To do this go to your command line and type in the 'ls' command to bring up all the directories. After, type in 'cd Downloads' which will take me to the directory where i have my key stored. I then type 'ls' again and any files or directories i have in there will appear. 

![how to find pem file](https://github.com/user-attachments/assets/378ab2d7-0389-46c3-b667-78015c03032b)

##

Once we have our key we'll copy and paste it with this command below in order to remotley access our instance. we use: ssh -i "(paste pem file here)" ubuntu@(elastic ip address). if everything is correct it should look similar to the image below. 

If it fails you may have to change the permissions using the command 'chmod 400'.

![ssh connect image](https://github.com/user-attachments/assets/9ee83275-0ce6-4698-bf80-d778a18231b1)

 Step 2:
 Creating our wordpress website

In step two we will install apache web server on our instance. To do this we run the command: sudo apt install apache2 .<br>
Should look similar to down below. Now on your web browser you can type in your elastic  

![install apache web server on instance](https://github.com/user-attachments/assets/29829e5e-a555-4f37-b57b-449f91b717ed)

##

 Now on your web browser you can type in your elastic ip address and look up your website which should look like below (for now).

 ![lamp-stack-ubuntu-22 04-768x949](https://github.com/user-attachments/assets/8c342f4d-242b-4df4-acde-25f723f996a9)

 
![install php runtime (word press is built on php)](https://github.com/user-attachments/assets/c50764b4-6923-4165-a6b7-5bfea2d62816)


A suspicious event occurred on 2022-05-09. Any login activity that happened on 2022-05-09 or on the day before needs to be investigated.
The following code demonstrates how I created a SQL query to filter for login attempts that occurred on specific dates.

![sql portfolio 2](https://github.com/VegaL101/computer-updates-lab/assets/166334918/c76ecf2d-ceac-4d44-8bc8-9e81c966b341)

The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with an OR operator to filter my results to output only login attempts that occurred on either 2022-05-09 or 2022-05-08. The first condition is login_date = '2022-05-09', which filters for logins on 2022-05-09. The second condition is login_date = '2022-05-08', which filters for logins on 2022-05-08.



Step 3:
Retrieve login attempts outside of Mexico.

Login attempts outside of Mexico also need to be looked up due to suspicious activity.

![sql portfolio 3](https://github.com/VegaL101/computer-updates-lab/assets/166334918/0249c5d3-1ebc-4e9b-86e7-e762e82732a1)

FIrst i selected all data from the log_in_attempts table. Then, I used a WHERE  with NOT to retrieve login attempts everywhere but Mexico . I used LIKE with MEX% to find anything that starts with “Mex”  since both MEX and MEXICO can appear on the dataset. 



Step 4:
Retrieve employees in Marketing.

Certain employees in the marketing department located in the east building need their systems to be updated. To do this I need to create a new query. 

![sql portfolio4](https://github.com/VegaL101/computer-updates-lab/assets/166334918/980714e7-7e94-4ac1-b61a-d12cca4a71bb)

This query returns all employees in the Marketing department in the East building. I select all data from the employees table. Then, I used a WHERE with AND to filter for employees who work in the Marketing department and in the East building. I used LIKE with East% since there is more than one office in the east building. I then received the data needed to find out who has yet to update their systems.



Step 5:
Retrieve employees in Finance or Sales.

systems in the Finance and Sales departments also need to be updated. The query returns employees in the Finance and Sales departments.

![portfolio5](https://github.com/VegaL101/computer-updates-lab/assets/166334918/03c97169-b1ee-4339-8444-faa31d408c97)

Again I start by selecting all data from the employees table. Then, I used a WHERE  with OR to filter for employees who are in sales and finance. With this query I can find employees in either department.
Retrieve all employees not in IT
A security update needs to be done on all employees except those in the IT department.



Step 6:
Retrieve all employees not in IT

A security update needs to be done on all employees except those in the IT department.

![sql 6](https://github.com/VegaL101/computer-updates-lab/assets/166334918/512b9716-6f59-431f-b031-8179db973824)


Similar to the query from earlier i return all employees not in the Information Technology department. First, I started by selecting all data from the employees table. Then, I used a WHERE  with NOT to filter for employees not in this department.


Summary:

I created multiple queries to help find information regarding login attempts and employee systemsI. Any data related to login attempts was to investigate suspicious activity and any data involving employee machines was to update any systems that can prove a security risk.








