+++
title = "IAM Role"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

#### Creating IAM Role

1. **Log-in to the AWS Console** from the [AWS Web Services homepage](https://aws.amazon.com/)
2. Navigate to the Identity and Access Management (IAM) page by either:
   - Clicking on the account name in the top right corner and select **My Security Credentials**
   - Typing `IAM` into the services search-bar and selecting 'IAM'
     ![Image](/images/preparation/iam-service.png)
3. From the left pane of the IAM console, select **Roles** then click on **Create role** button.
   ![Image](/images/preparation/create-role.png)
4. Create a new role for EC2 instance to access S3 storage.

- Choose **AWS Service** for Trusted entity type and **EC2** for Use case sections. Then click **Next** button.
  ![Image](/images/preparation/user-role-1.png)
- Add permission for access S3 storage. Then click **Next** button.
  ![Image](/images/preparation/user-role-2.png)
- Enter a Role name (for example: ec2-role-for-s3-and-secret-management) and review create role information.
  ![Image](/images/preparation/user-role-3.png)

5.  Click **Create role** button.
    ![Image](/images/preparation/user-role-4.png)
6.  After successfully creating a role, go to your new role details page, dropdown the **Add permissions** and choose **Create inline policy**
    ![Image](/images/preparation/user-role-5.png)
7.  Click **JSON** tab and enter the policy below to the Policy editor
    ![Image](/images/preparation/user-role-6.png)

```js
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "Statement1",
			"Effect": "Allow",
			"Action": [
				"secretsmanager:GetSecretValue"
			],
			"Resource": [
				"arn:aws:secretsmanager:us-east-1:017820676824:secret:upload-image-to-s3-secret-8UsdOW"
			]
		}
	]
}
```

8. Enter the name for the new policy and click **Create policy** button
   ![Image](/images/preparation/user-role-7.png)
