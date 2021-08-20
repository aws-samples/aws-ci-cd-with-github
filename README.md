# CI/CD With GitHub
## CI/CD Pipeline for AWS CloudFormation Templates

This repository contains code and examples for deploying AWS CloudFormation or AWS CDK using a CI/CD pipeline. It provides a framework to validate infrastructure as code (IaC) using tools like cfn-guard, cfn-lint, and taskcat to test templates.

## Deploy
To deploy this example you will need the AWS CLI, access to an AWS Account, and GitHub repository. 

```bash
aws cloudformation package \
    --template-file main.yaml \
    --s3-bucket ${BUCKET_NAME} \
    --output-template-file main.packaged.yaml

aws cloudformation deploy \
  --template-file main.packaged.yaml --stack-name ${STACK_NAME} \ 
  --parameter-overrides GitHubUser=${GITHUB_USERNAME} \
    GitHubRepoName=${GITHUB_REPO} \ 
  --capabilities CAPABILITY_IAM
```