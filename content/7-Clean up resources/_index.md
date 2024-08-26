+++
title = "Clean up resources"
date = 2021
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

In the end of this workshop, we will clean up all resources that we have created!

1. Terminate the EC2 instance: This will stop the instance from running and release its resources.

- In the Instances list, locate the EC2 instance you created.
- Select the instance by checking the checkbox next to it.
- Click the "Actions" button.
- Choose "Instance Actions" and then select "Terminate Instance".
- Confirm the termination by clicking "Terminate".

2. Delete the S3 bucket: Be cautious when deleting a bucket, as it will also delete all the objects stored within it. Ensure you have a backup if needed.

- Locate the S3 bucket you created.
- Select the bucket by clicking on its name.
- If the bucket contains objects, you can either empty it manually by deleting each object or use the "Empty bucket" option. To empty the bucket, click the "Actions" button, then "Manage bucket" and finally "Empty bucket".
- Once the bucket is empty (or if it was already empty), click the "Actions" button again.
- Choose "Delete" and confirm the deletion.

3. Remove any associated security groups or IAM roles: These may have been created to grant permissions to the EC2 instance or S3 bucket.

- In the IAM console, go to "Roles".
- Check the roles created for your EC2 instance or S3 bucket and delete them.
