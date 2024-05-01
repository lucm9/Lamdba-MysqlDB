# Lamdba-MysqlDB

# Create a Lambda function that listens for the creation of a .csv file in an S3 bucket and then uploads the content of the file into an RDS MySQL database.

Requirements:

 - The credentials of the database should not be hardcoded into the Lambda function.

Prerequisite:

Create an S3 bucket containing a zipped pymysql module.
Set up an EC2 instance that will be used to connect to the MySQL database to confirm that the file has been dumped into the database.
 - Use user data to bootstrap updating the instance.
 - Run the following commands after connecting to the instance:

```
sudo apt update -y
sudo apt install python3.11 -y
sudo apt install python3-pip
sudo su
sudo pip3 install pymysql
```

Install the zip application:
`sudo apt install zip -y`

Connect to your AWS user by installing awscli into your instance.
Create an access key for your IAM user.

Configure AWS CLI:
` aws configure ` 
After connecting to your user programmatically, upload the zipped pymysql into an S3 folder: 

`aws s3 cp pymysql.zip s3://bucket-name/path/to/upload/`

Create a VPC and create RDS MySQL inside it.
 - Create a VPC with 2 public and private subnets.
 - Create your MySQL database inside the VPC.
 - Make sure the database is publicly accessible.
 - Configure the RDS security group to allow traffic coming from your EC2 instance.

Log into your database and create a database and a table inside the database:


Create an IAM role giving permissions to S3, CloudWatch, and RDS.
Create your Lambda function.
Attach the newly created role to the Lambda function.
Upload from S3 location:
Copy pymysql URL from S3 and paste it.
Create a file in the Lambda executioner folder called lambda_function.py.
Open the file and insert the code (delete any existing code).

## Additional Steps:
Add a trigger from another S3 bucket to the Lambda function. 

This will be the S3 bucket you upload your CSV file to.
Whitelist traffic entering the RDS database.
Change timeout limit to about 30 seconds.

