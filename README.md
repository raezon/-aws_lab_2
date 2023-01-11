## Deploy a high-availability web app using CloudFormation

### Project Overview

Suppose company is creating an Instagram clone like application. Developers pushed the latest version of their code in a zip file located in a public S3 Bucket.
Now the task is to deploy the application, along with the necessary supporting software into its matching infrastructure. This needs to be done in an automated fashion so that the infrastructure can be discarded as soon as the testing team finishes their tests and gathers their results.

### Infrastructure Diagram:

![udagram-infrastructure-diagram](https://user-images.githubusercontent.com/32739028/156870014-732cfd37-63b4-4978-9c16-80cd8d77d4ad.png)

### Project Files

* `/cloudformation-stacks`: 
  * `network-params.json`: Parameters file for network cloudformation stack.
  * `network.yml`: CloudFormation template for creating networking resources for this project.
  * `servers-params.json`: Parameters file for servers cloud formation stack.
  * `servers.yml`: CloudFormation template for creating servers for this project.
* `s3-bucket`: It contain the main html file of the application and upload status screenshot.
* `/scripts`: This folder contains script to create, delete and update CloudFormation stack
* `/workflow-screenshots`: This folder contain screenshots of whole workflow status
* `udagram-infrastructure-diagram.png`: This shows visual aid to understand the CloudFormation script.


### Project Setup
$ cd cloudformation
```

1. To create networking resources using cloudformation template, run the below command.
```

$ ../scripts/create.sh web-network-stack  network.yml network-params.json
```

2. To create servers resources using cloudformation template which pulls source code from S3 bucket automatically while starting, run the below command. After exceuting it these are the resources created:
  * Security Groups
  * IAM Role, Policy, Instance Profile
  * Launch configuration
  * Auto Scaling Group
  * Load Balancer
  * Target Group

```
$../scripts/create.sh web-server-stack  server.yml server-params.json
```

Once the above steps are complete,You can access this url
