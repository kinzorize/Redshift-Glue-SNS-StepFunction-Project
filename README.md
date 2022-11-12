# Redshift-Glue-SNS-StepFunction-Project

Orcherate Redshift ETL using Glue and Step Function
Fetch source data from Amazon Redshift Cluster using AWS Glue and Step Functions to gain analytical insights more quickly.
I read the date from Redshift using Redshift Spectrum and load the data to Redshift and extract the transform data from Redshift and put it into S3.In this project, i put the Redshift in the Private subnet to ensure the confidentiality of our data.

# Steps

- create VPC
- Create 4 subnets : 2 Public and Private subnets (A and B with specific CIDR range within two availability zone A and B)
- Create 1 internet Gateway for the Public Subnets and attach it to my VPC
- Create 1 NAT Gateway for the Private Subnets to enable the Private subnets to communicate with other service like S3.
- Create 1 Route Table for public route
- Edit the route table attached to your VPC and add Destination 0.0.0.0/0 and under target select your public created internet Gateway and save.
- Then click on Subnet Association to associate the route table to Public Subnet A.
- Create Another route table for Public Subnet B and associate it with Public Subnet B using internet Gateway
- create 2 Route table (my private route A and B) and assocaited it with the created NAT Gateway

* Create Redshift Cluster but before that, click on the left icon and click on configuration and stroll down to the last and click on 'manage Subnet Groups'
* Then create new Subnet Group under the subnet , add your VPC and add the subnets you created initially.
* Create IAM role and json policy that will be attached to the Redshift cluster
* Connect the database then create a new connection and ensure using AWS Secret Manager to protect your database
* use the AWS CLI to create a unique bucket and copy the python files to the S3 bucket.
* Create a connection on AWS Glue using your Redshift cluster information.
