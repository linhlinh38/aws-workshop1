+++
title = "Get All Images Pre-signed Urls"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

Create a function name **getAllImagePreSignedUrls** that handles getting all the presigned url of images from S3 bucket

1. List Objects:

```js
const listObjectRequest = new ListObjectsV2Command({
  Bucket: jsonSecret.BUCKET_NAME ? jsonSecret.BUCKET_NAME : "",
  Prefix: "images/",
});
```

- The **listObjectRequest** creates a command to list objects within the specified S3 bucket.
- The **Bucket** property sets the bucket name.
- The **Prefix** property filters the results to only include objects starting with "images/".

2. Retrieve Image Data and Generate Pre-signed URLs:

```js
const data = await s3.send(listObjectRequest);
```

- The **s3.send(listObjectRequest)** asynchronously sends the command to S3 and retrieves a list of objects.

```js
const urls = data.Contents?.map(async (item) => {
  const getObjectCommand = new GetObjectCommand({
    Bucket: jsonSecret.BUCKET_NAME,
    Key: item.Key,
    ResponseContentDisposition: "inline",
  });
  const url = await getSignedUrl(s3, getObjectCommand, { expiresIn: 3600 });
  return {
    url,
    fileName: item.Key?.split("/")[1],
  };
});

let resolvedUrls;
if (urls) {
  resolvedUrls = await Promise.all(urls);
}
```

- The **data.Contents** array contains information about each object, including its key.
  For each object in **data.Contents**, a **GetObjectCommand** is created with the bucket name and object key.
  The **getSignedUrl** function is used to generate a **pre-signed URL** for the object, with a 1-hour expiration time.
  Then the URL and the filename (extracted from the object key) are added to the urls array.

3. Return Response:

```js
return res.json(resolvedUrls);
```

- The function returns a JSON response containing the array of resolved URLs.

4. Test your API with postman or orther testing methods you prefer:
   ![Image](/images/preparation/postman-2.png)
5. Try to access the image link return from browser to see if your presigned url works.
   ![Image](/images/preparation/postman-3.png)

**Note:** If you get the error **Access Denied**, its may because your bucket policy not allow access from the internet so that make sure under the permissions tab, the **Block new public bucket policies** is unchecked. You can try to add a new bucket policy below:

```js
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "PublicReadGetObject",
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::your-s3-bucket-here/*"
       }
   ]
}
```
