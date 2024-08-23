+++
title = "Configure Source code for backend"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Configure Source code for backend

1. Create a Nodejs express app and install the dependencies
   - Go to your project directory, open the terminal and type:
   ```js
   npm init -y
   npm i ts-node nodemon --save-dev
   npm i express dotenv multer cors
   npm i @aws-sdk/client-s3 @aws-sdk/client-secrets-manager @aws-sdk/s3-request-presigner @aws-sdk/client-sns @types/cors @types/express @types/multer @types/node typescript --save-dev
   ```
2. Add `.env` file for store your secrets

   ```js
   PORT = 80;
   AWS_ACCESS_KEY_ID = xxxxxxxxxxxx;
   AWS_SECRET_ACCESS_KEY = xxxxxxxxxxxx;
   BUCKET_NAME = xxxxxxxxxxxx;
   AWS_REGION = xxxxxxxxxxxx;
   ```

   - **AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY** are typically retrieved from the IAM User we create before.

3. Add a .gitignore file to prevent your secrets and sensitive information in .env file from being pushed to github
   ```js
   .env
   node_modules
   ```
4. Create your server.ts

```js
import express, { Express, Request, Response } from "express";
import dotenv from "dotenv";
import cors from "cors";
import { router as Router } from "./routes";

dotenv.config();

const app: Express = express();
const port = process.env.PORT || 80;

app.use(cors());

app.get("/", (req: Request, res: Response) => {
  res.send("Express + TypeScript Server");
});

app.listen(port, () => {
  console.log(`[server]: Server is running at http://${app.head.name}:${port}`);
});
```

5. Testing if your server is running

   ```js
   npm start
   ```

   OR

   ```js
   npm run dev
   ```

6. Create a git repository for your src code
   ![Image](/images/preparation/git.png)
