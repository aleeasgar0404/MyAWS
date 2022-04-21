## Capstone Project



# Step 2: Get the Project Assets 
1. Clone the repository:
2. Extract the files to the Apache www folder:
   unzip Example.zip -d /var/www/html/

   
# Step 3: Install a LAMP web server on Amazon Linux 2

### LAMP (Linux, Apache HTTP server, MySQL database, and PHP) stack

sudo yum -y update
sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2

sudo yum install -y httpd mariadb-server
sudo systemctl start httpd

sudo systemctl enable httpd
sudo systemctl is-enabled httpd

# Step 4: Create a MySQL RDS database instance 
with the following specifications.
- [ ] Create a db subnet group 
- [ ] Databasetype: MySQL
- [ ] Template: Dev/Test
 - [ ] DBinstanceidentifier: Example
 - [ ] DB instance size: db.t3.micro
 - [ ] Storage type: General Purpose (SSD)
 - [ ] Allocatedstorage: 20GiB
 - [ ] Storageautoscaling: Enabled
 - [ ] Standbyinstance: Enabled
- [ ]  Virtualprivate: ExampleVPC
- [ ]  Databaseauthenticationmethod: Passwordauthentication 
- [ ]  Initialdatabasename: exampledb
- [ ]  Enhancedmonitoring: Disabled

# Step 5: Create an Application Load Balancer
- Create target group 
- Create an auto scaling group 
- Lunch Web Instances in the private subnet
# Step 6: Importing the data into the RDS database
 1. get the SQLDump file:
 

 2. connect to the RDS database, run this command:
```sh
mysql -u admin -p --host <rds-endpoint>
 ```
 3. Test that you can access the RDS DB 
 ```sh
 use exampledb;	
show tables; 

 ```
 
  
4. Import the data into the RDS database.
```sh
mysql -u admin -p exampledb --host <rds-endpoint>  < Countrydatadump.sql       
```
# Test the ALB 
- Test data was imported 
```sh
 use exampledb;	
show tables; 
select * from countrydata_final; 
 ```

# Step 7: Configure the system parameters in Parameter Store Systems Manager

Add the following parameters to the Parameter Store and set the correct values:
1. /example/endpoint 

2. /example/username   
3. /example/password  
4. /example/database exampledb


