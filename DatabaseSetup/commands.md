Create a connection to the Amazon RDS database from the EC2 instance

1. Connect to the ec2 instance via ssh
   
2. Change to root user:
    $ sudo su
   
3. Download some Linux packages, if not installer already in userdata.
    $ sudo amazon-linux-extras install epel -y
   
4. Install the MySQL repository package. Enter y wherever asked.
   $ sudo yum install https://dev.mysql.com/get/mysql80-community-release-el7-5.noarch.rpm
   
5. Install the MySQL community server. Enter y wherever asked.
   $ sudo yum install mysql-community-server

6. Verify the version for MySQL.
   $ mysql --version

If all installed well, the command should show the MySQL version installed

7. Get your rds instance Endpoint. On the database instance console, under the connectivity tab, copy the Endpoint
8. Run the following command on the terminal:
    mysql -h <mysql-instance-dns> -u <username> -p

Example:
mysql -h database-instance.cfjitlrhaxvx.us-east-1.rds.amazonaws.com -u rdsuser -p
Press enter then enter the password


Run MySQL commands to test:
SHOW databases;
use database;
show tables;
select * from address;

