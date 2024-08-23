+++
title = "Create EC2 Instance"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

#### Create EC2 Instance

1. Navigate to the EC2 page typing `EC2` into the services search-bar and selecting 'EC2' service
   ![Image](/images/preparation/create-ec2.png)
2. In the EC2 Dashnoard, select **Launch instance** for create a new EC2 Instance.
   ![Image](/images/preparation/create-ec2-1.png)
3. Enter a name for EC2 Instance (for example: upload-image-to-s3-server).
   ![Image](/images/preparation/create-ec2-2.png)
4. Choose an Amazon Machine Image (for example I choose Amazon Linux) and choose instance type (for example I choose t2.micro).

- **\*Free Tier Eligible:** If you have trial account then the options which marked Free Tier Eligible is free for your account.
  ![Image](/images/preparation/create-ec2-3.png)

5. Create a new key pair and allow the access from the internet to your EC2 instance.
   **Note:** Key pair would help to log in to our instance using an SSH client.
   ![Image](/images/preparation/create-ec2-4.png)

6. Dropdown **Advanced details** tab, at **IAM instance profile** section, attach the IAM Role (ec2-role-for-s3-and-secret-management) you have just created above to your EC2 instance. This role will allow your EC2 instance to access the S3 bucket and AWS secret manager.
   ![Image](/images/preparation/create-ec2-6.png)

7. You can review the summary of the create EC2 information from the left bar and then click **Launch instance**.
   ![Image](/images/preparation/create-ec2-5.png)
