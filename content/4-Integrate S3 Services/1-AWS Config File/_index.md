+++
title = "AWS Config File"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

- Create a new aws config file in src/config/awsConfig.ts

```js
let jsonSecret= {
 AWS_ACCESS_KEY_ID: process.env.AWS_ACCESS_KEY_ID;
 AWS_SECRET_ACCESS_KEY: process.env.AWS_SECRET_ACCESS_KEY;
 BUCKET_NAME: process.env.BUCKET_NAME;
};
```

- This code creates an object **jsonSecret** to store **AWS credentials** and **bucket name**.

```js
let s3 = new S3Client({
  credentials: {
    accessKeyId: jsonSecret.AWS_ACCESS_KEY_ID,
    secretAccessKey: jsonSecret.AWS_SECRET_ACCESS_KEY,
  },

  region: "us-east-1",
});
```

- This code imports the **S3Client** class from the **@aws-sdk/client-s3** package. This package provides the necessary tools for interacting with S3.
- Then exports the **s3** variable, which holds the `S3Client` instance. This allows other parts of your application to use it to interact with S3.
