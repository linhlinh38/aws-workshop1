+++
title = "Delete image from s3 bucket"
date = 2020
weight = 4
chapter = false
pre = "<b>4.4. </b>"
+++

Create a function name **deleteImage** that handles delete an image from S3 bucket

1. Creates a **DeleteObjectCommand**:

```js
const { fileName } = req.params;

const deleteObjectRequest = new DeleteObjectCommand({
  Bucket: jsonSecret.BUCKET_NAME ? jsonSecret.BUCKET_NAME : "",
  Key: `images/${fileName}`,
});

await s3.send(deleteObjectRequest);
```

- **DeleteObjectCommand** specifies the bucket name and object key to be deleted.
- The **await s3.send(deleteObjectRequest)** line asynchronously sends the **DeleteObjectCommand** to the S3 service, initiating the deletion process.

2. Testing your upload api with postman to see if its working or not.
   ![Image](/images/preparation/postman-4.png)
