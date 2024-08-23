+++
title = "Introduction"
date = 2024-08-19T00:00:00+07:00
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

Before we dive into the specifics of our workshop, let's take a moment to introduce the primary tools and services we'll be utilizing.

**Content:**

- [Amazon EC2 - Amazon Elastic Compute Cloud](#amazon-ec2---amazon-elastic-compute-cloud)
- [Amazon S3 - Amazon Simple Storage Service](#amazon-s3---add-a-payment-method)
- [AWS SDK - Your Toolkit for Building on AWS](#aws-sdk---your-toolkit-for-building-on-aws)
- [AWS Secrets Manager](#aws-secrets-manager)

#### Amazon EC2 - Amazon Elastic Compute Cloud

![Image-ec2](/images/aws-icon/EC2.png)

- **AWS EC2** is like renting virtual computers online. Instead of buying and maintaining your own physical servers, you can use AWS to create virtual ones whenever you need them. These virtual computers can be used for many things, like running websites, storing data, or analyzing large amounts of information.

- The great thing about EC2 is that you only pay for what you use. So, if you need more computers for a busy time, you can easily add them. When things slow down, you can reduce the number of computers to save money. It's flexible and cost-effective.

- For more information: [Amazon Elastic Compute Cloud (Amazon EC2)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

#### Amazon S3 - Amazon Simple Storage Service

![Image](/images/aws-icon/Simple-Storage-Service.png)

- **Amazon S3** is like a massive online storage closet. You can put any type of file in it, from pictures and videos to documents and software. It's designed to be super easy to use and can handle almost any amount of data.

- Think of it as a place where you can store your digital stuff safely and access it from anywhere in the world. You don't have to worry about running out of space or losing your files. S3 is used for all sorts of things, like storing website content, backing up data, and hosting large files.

- For more information: [Amazon Simple Storage Service (Amazon S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

#### AWS SDK - Your Toolkit for Building on AWS

![Image](/images/aws-icon/SDKs.png)

- **AWS SDK** is a collection of tools and libraries that make it easier for developers to interact with AWS services. It provides a bridge between your code and AWS, handling complex tasks like authentication, error handling, and data formatting. Instead of writing lengthy code to manage these details, you can use the SDK to focus on building the core logic of your application. Think of it as a helpful assistant that simplifies your work with AWS.

- By using AWS SDK, you can focus on building your application's core features without worrying about the underlying AWS infrastructure.

#### AWS Secrets Manager

![Image](/images/aws-icon/Secrets-Manager.png)

- **AWS Secrets Manager** is like a secure lockbox for your sensitive information. It helps you store, manage, and retrieve secrets like passwords, API keys, and database credentials. Instead of hardcoding these secrets directly into your applications, you can keep them safe and secure in Secrets Manager.

- This service makes it easier to rotate passwords regularly, reducing the risk of security breaches. It also helps you control who can access your secrets, ensuring that only authorized users can use them. Think of it as a central place to protect your valuable digital keys.

- For more information: [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)
