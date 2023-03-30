# aws-amplify

AWS Amplify

Related repo:
- [aws-amplifyapp](https://github.com/gabepublic/aws-amplifyapp)

## AWS Docs

- [AWS Amplify Documentation Homepage](https://docs.aws.amazon.com/amplify/index.html)
- [AWS Amplify User Guide](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)


## DD

- [Serverless Computing - Getting Started](https://aws.amazon.com/serverless/getting-started/?nc=sn&loc=2&serverless.sort-by=item.additionalFields.createdDate&serverless.sort-order=desc)

- [Build a Serverless Web Application](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)

- [Host a Static Website - Host your simple marketing website or web application on AWS](https://aws.amazon.com/getting-started/hands-on/host-static-website/)


## AWS Getting Tutorial - Build a Serverless Web Application
Using AWS Lambda, Amazon API Gateway, AWS Amplify, Amazon DynamoDB, 
and Amazon Cognito 

- Source: [Build a Serverless Web Application](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/module-1/)
    
### Module 1 - Static Web Hosting with Continuous Deployment

Configure AWS Amplify to host the static resources for the web application
with continuous deployment built in

- We will use the Github repo [website-vue-build-wildrydes-site](https://github.com/gabepublic/website-vue-build-wildrydes-site)
  that was pre-created from downloading thee following
```
$ aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
```
  - The content of this repo can be reproduced from the source Github repo
    [website-vue-wildrydes-site](https://github.com/gabepublic/website-vue-wildrydes-site)
    by running `npm run build` and copy the content of the `dist` folder

- Go to Aws console - Amplify page
- Click New App on the top right and choose Host Web App
- Select Github on the "Get started with Amplify Hosting" page
  - Amplify Hosting requires read-only access to your repository
- Select the repo; the field "Recently updated repositories"
- Select the repo "Branch"
- There is option to select a specific folder in the repo by "checking"
  the "Connecting a monorepo" and pick a folder
- On the "Build settings" page,
  - Enter the "App name"; it's been pre-populated with repo name
  - Leave the "Build and test settings" as is; the settings are shown
    below and can be downloaded to `amplify.yaml`
  ```
  version: 1
  frontend:
    phases:
      # IMPORTANT - Please verify your build commands
      build:
        commands: []
    artifacts:
      # IMPORTANT - Please verify your build output directory
      baseDirectory: /
      files:
        - '**/*'
    cache:
      paths: []  
  ```
  - Check "Allow AWS Amplify to automatically deploy all files hosted in
    your project root directory"
  - Advanced settings - left as default, fields include:
    - Build image - Use our default build container, or provide your own.
      - [Learn more](https://docs.aws.amazon.com/amplify/latest/userguide/custom-build-image.html)
    - Environment variables - add environment variables to save secrets 
      and API keys that you do not want to store in your repository;
      - Default: no entries
    - Live package updates - override the default installed versions of 
      packages or tools for your app
      - Default: No live updates currently configured. Use the dropdown 
        below to add some. The list includes: Amplify CLI, Yarn, Bundler,
        Cypress, VuePress, Next.js version, Node.js version, etc.
- Select Next.
- On the "Review" page select Save and deploy
- The process takes a couple of minutes for Amplify Console to create 
  the necessary resources and to deploy your code.



## How-to

- [Setting up Amplify access to GitHub repositories](https://docs.aws.amazon.com/amplify/latest/userguide/setting-up-GitHub-access.html)
