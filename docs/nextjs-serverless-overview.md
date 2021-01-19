# Overview


We'll start from scratch, creating a new Next.js app. We'll then, step by step, use the [Serverless Next.js Component](https://github.com/serverless-nextjs/serverless-next.js) and use the [Serverless Framework](https://www.serverless.com/framework/docs/providers/aws/guide/intro/) to deploy. 

The project is powered by the amazing serverless-components. At its core it uses 4 components:

- @serverless/aws-s3
- @serverless/aws-cloudfront
- @serverless/aws-lambda
- @serverless/domain

Most of the heavy lifting is done by the components themselves, serverless-next.js simply orchestrates.

