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


Here we will give our instance a name, Pick the OS image, and give it a keypair.

##
It is crucial you give your instance a keypair for security reasons. Letting you access your instance securely.

![fill ins for instance](https://github.com/user-attachments/assets/f55d31bd-ad35-4991-86cf-9cf423421f7f)

## 
Once you've clicked on 'create new keypair' you give it a name, choose the pair type and choose the key file format. Once created the key will be downloaded onto your device. Make sure to keep this key secured.

![key pair](https://github.com/user-attachments/assets/5a50047a-b9c3-4454-8402-136e5ed1d7d7)

##



Step 2:
Retrieve login attempts on specific dates.

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








