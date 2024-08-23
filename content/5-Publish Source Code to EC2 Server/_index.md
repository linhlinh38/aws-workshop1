+++
title = "Publish Source Code to EC2 Server"
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

#### Overview

To access S3, our code needs the BUCKET_NAME, AWS_SECRET_ACCESS_KEY, and AWS_ACCESS_KEY_ID. Never share these keys publicly to avoid losing money. We store them in a .env file on our local server. However, when running on EC2, we need a secure way to access these keys without exposing them in the code. AWS Secrets Manager provides a solution by storing these keys securely and granting EC2 the necessary permissions to retrieve them.

#### Setup AWS Secrets Manager

1. Navigate to the Secrets Manager page by Typing `Secrets Manager` into the services search-bar and selecting 'Secrets Manager'
   ![Image](/images/preparation/create-secret.png)
2. Choose **Other type of secret** and enter the **secret key and value**. After review the secret information, click **Next** button
   ![Image](/images/preparation/create-secret-1.png)
3. Enter Secrets name. At the **Resource permissions** section, click button **Edit Permissions** and enter below permission for allow specific role that we create before to access secrets
   ![Image](/images/preparation/create-secret-2.png)
   ```js
   {
   "Version" : "2012-10-17",
   "Statement" : [ {
    "Effect" : "Allow",
    "Principal" : {
      "AWS" : "arn:aws:iam::017820676824:role/ec2-role-for-s3-and-secret-management"
    },
    "Action" : "secretsmanager:GetSecretValue",
    "Resource" : "*"
   } ]
   }
   ```
4. Review the create Secrets Manager information, you can see the sample code given from aws for configure and implementing your code to get the key. After review, click **Store** button.
   ![Image](/images/preparation/create-secret-3.png)

#### Update AWS Config file

In AWS Config file, update this code to get the key from AWS Secrets Manager and using the return secret to create a new S3Client

```js
    const client = new SecretsManagerClient({
    region: "us-east-1",
    });
    const secret = await client.send(
      new GetSecretValueCommand({
        SecretId: secret_name,
        VersionStage: "AWSCURRENT",
      })
    );

    jsonSecret = JSON.parse(secret.SecretString as string);

    s3 = new S3Client({
      credentials: {
        accessKeyId: jsonSecret.AWS_ACCESS_KEY_ID,
        secretAccessKey: jsonSecret.AWS_SECRET_ACCESS_KEY,
      },

      region: "us-east-1",
    });
```

#### Deploy your src code to EC2 Server

1. Connect to your EC2 Server by either click **Connect** button in EC2 Instance Connect tab or using SSH Client
   ![Image](/images/preparation/connect-ec2.png)
2. After doing SSH into the EC2 instance you need to change the user to the super user by using the command:

```js
    #sudo su
```

2. Install NodeJS and NPM using nvm

```js
    #curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Now you need to activate nvm by using the command :

```js
    #. ~/.nvm/nvm.sh
```

By using nvm you have to install Node.js. Put the below command in the command line :

```js
    #nvm install node
```

Check the nvm and Node.js version by using the commands:

```js
    #nvm --version
```

![Image](/images/preparation/ssh-1.png)

3. Install Git

```js
    #yum update -y
    #yum install git -y
```

You can check the version of the Git by putting the command

```js
    #git --version
```

![Image](/images/preparation/ssh-2.png)

4. Clone the repository from GitHub

```js
    #git clone https://github.com/your-repository-link
```

Now get into that folder and check the sub folders and files of the Node.js application. Use the command to check the files:

```js
   #cd backend-aws-workshop1
   #ls
```

5. Install all the required dependencies

```js
   #npm install
```

6. Run the application

```js
   #npm run dev
```

![Image](/images/preparation/ssh-3.png)

7. Access the server:

- If everything till now is working fine then we will be able to see the application running on the port number 80. You can access the server through the public ip address of your EC2 server
  ![Image](/images/preparation/ssh-4.png)

8. Test your API again:

- Using postman to test the api, change the IP address to your public EC2 IP address:
  ![Image](/images/preparation/ssh-test-2.png)
