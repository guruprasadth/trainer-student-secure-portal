# EduCloud Portal

## Project Overview
Secure AWS + Linux based file portal for Trainers and Students.

## Architecture
<img width="1548" height="767" alt="diagrma" src="https://github.com/user-attachments/assets/f5152aa2-a6b8-45e9-a2c6-9c30d9dc55b2" /></br>

##  AWS Services Used
- VPC
- EC2
- S3
- RDS
- CloudFront
- IAM
- Auto Scaling
- SNS
- Lambda
- API Gateway

##AWS VPC Setup #########
- Create VPC and 2 public and private subnet and route table associate subnet to route
table.

- Create internet gateway for public subnet and private subnet have internet gateway.
  
<img width="940" height="461" alt="image" src="https://github.com/user-attachments/assets/5d46255e-744b-4391-a95d-8b3b4f1fcf44" />

##AWS EC2 Service Setup####
-create a instance to deploy the front and backend 

-here We deploy the frontend in the private ec2-instance in html directory and we access by using Elastic Load Balance(ELB) it has provide the DNS ID

-It having user login (Trainer, students & Support-staff) each user having unique name and password to login portal.

-Trainer can upload the resources to should access for students along with they can view the assignments submitted by students

sample out put images

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/50bccd75-23e0-4581-a0af-c0a493c59e54" /></br>

Trainer login.

•	Trainer can upload the resources to should access for students along with they can view the assignments submitted by students. 

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/c45903cc-082a-4aef-983f-00d194357c2d" />

Student login.

•	Student can submit the assignments and also download the resources that uploaded by trainer

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/4711028a-22fb-4c22-81b7-bbbc9efd5d7b" /></br>

###here create a one public instance to perform the Linux Administrationoperations####

- It is alternative way so teacher would share secure files via NFS#####
- 
## Linux Setup

User & Group Management

<img width="1920" height="1080" alt="useradd" src="https://github.com/user-attachments/assets/1e114e49-683e-410b-9291-3012685661ce" /></br>

ACL Permissions

<img width="1920" height="1080" alt="setfacl logs" src="https://github.com/user-attachments/assets/6b685e2e-eba7-4480-8f83-454808a81219" /></br>

LVM Extension

<img width="1920" height="1080" alt="pvextend-5g" src="https://github.com/user-attachments/assets/33ec06e9-758f-449e-b5f7-7043313ed6f1" /></br>

LUKS Encryption

<img width="1920" height="1080" alt="crypt setup" src="https://github.com/user-attachments/assets/612add85-21c5-4814-8612-bf048388325b" /></br>

LUKS mount
<img width="1920" height="1080" alt="crypt-set2" src="https://github.com/user-attachments/assets/4f3c613b-ea52-45b1-9da6-5882826f4945" /></br>

Cron Jobs

<img width="1910" height="485" alt="logs back to s3" src="https://github.com/user-attachments/assets/b23483ea-1e38-41b0-962e-46cca259825e" /></br>

- NFS & FTP Configuration
  
  <img width="1920" height="1002" alt="nfs slient config" src="https://github.com/user-attachments/assets/bb7b110a-42b0-42c2-a59c-88a9d824c8da" /></br></br>
  
- FTP to students would submit the assignment and download the resources
  
- <img width="1920" height="1080" alt="ftp client" src="https://github.com/user-attachments/assets/074229fe-0175-4fb3-8a7f-041fa422b057" /></br>

Auto Scaling Group (ASG).

•	It is highly Scalable service it manages the instance. 

•	when instance usage 80 above it will create one more instance.

•	When the instance health is 20% scale in the instance.

<img width="940" height="404" alt="image" src="https://github.com/user-attachments/assets/32783e09-2594-4a65-8fda-827b76602e0b" /></br>



S3(Simple Storage Service) 

•	it is object storing with enabled the lifecycle for 90 means glacier archive.

•	Once object uploaded the older file are deleted based on the lifecycle configuration along with bucket policy.

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/cb6f8a8d-f739-4eaf-8469-085ac8e89606" /></br>

S3 Lifecycle configuration.

After 90 days the files or object are delete.

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/5dd30564-f518-4a43-847b-8036fc4db1c4" /></br>

RDS (Relational Database Service).

•	Created the RDS for storing the users information like trainers,students.

•	It store the users details , file details, date and time

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/ee194281-70fd-4b7c-9d95-b8bce17a39a3" /></br>

#we used mysql for datastore 

<img width="940" height="296" alt="image" src="https://github.com/user-attachments/assets/314b5c54-98a0-4b9d-bc6b-ad9d85d435bd" /></br>

Cloudfront

•	It is service used to delivery the content over a network without latency

•	Here S3 used as a origin and we used for students to download the resources 

•	In this project we used to deliver the content or files in the S3 bucket to the user when they download the file.

<img width="940" height="404" alt="image" src="https://github.com/user-attachments/assets/c3dc9f1d-0673-42cf-8573-6c39a3c9f729" /></br>

