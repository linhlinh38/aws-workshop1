+++
title = "Uploading image to s3 bucket"
date = 2020
weight = 3
chapter = false
pre = "<b>4.3. </b>"
+++

In `src/controllers/imageController.ts` file, create a function `uploadImage` that handles uploading an image to an S3 bucket

1. Creating the `PutObjectCommand`:

```js
const fileName = Date.now() + "_" + file.originalname;
const fileContent = file.buffer;
const putObjectRequest = new PutObjectCommand({
  Bucket: jsonSecret.BUCKET_NAME ? jsonSecret.BUCKET_NAME : "",
  Key: `images/${fileName}`,
  Body: fileContent,
  ContentType: file.mimetype,
});
```

- **Bucket**: Specifies the name of the S3 bucket where the file will be uploaded.
- **Key**: Defines the object key (filename) within the bucket where the file will be stored.
- **Body**: Contains the binary data of the file to be uploaded.
- **ContentType**: Sets the MIME type of the file, which helps clients understand the file format.

2. Sending the Request:

```js
await s3.send(putObjectRequest);
```

- The `await s3.send(putObjectRequest)` line asynchronously sends the `PutObjectCommand` to the `S3 service`. This uploads the file to the specified bucket.
