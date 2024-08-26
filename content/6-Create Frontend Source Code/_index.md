+++
title = "Create Frontend Source Code (Optional)"
date = 2021
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

This project is nearly done, but if you want to have a UI to show your all your api, then lets create a frontend for its

1. To create a frontend, you can use my frontend source code sample [here](https://github.com/linhlinh38/frontend-aws-workshop1) or use any template you want
   ![Image](/images/preparation/front-end-ws1.png)
2. To make your frontend connect to ec2 server, define your url mapping with the public ip of your ec2 server
   ```js
   const axiosInstance = axios.create({
     baseURL: "http://54.165.100.46:80" /*this is your EC2 public ip*/,
   });
   ```
3. Run the Frontend Source
4. Now let's see what we have created <3
   ![Image](/images/preparation/ui-ws1-1.png)
