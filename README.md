# CloudFormation

CloudFormation is AWS tool for declarative infrastructure as code. It provides a common language for you to model and provision AWS and third party application resources in your AWS cloud environment.

## Project Description and Procedure

This project describes how I used AWS CloudFormation to deploy a WebApp project. The following procedure was followed to deploy the project.


```python
(1) Create a S3 bucket and upload the WebApp code files to be deployed inside it.

(2) Create the network infracstructure by running the cloud formation script to deploy it as shown below.

aws cloudformation create-stack --stack-name myinfra --template-body file://myinfra.yml --parameters file://infra-parameter-file.json --region=us-west-2

This will create the network resources required for the project.
- VPC
- Internet Gateway
- Public and Private subnets
- NAT gateway
- Route tables and associations

(3) Create other required infracstructure by running below script.

aws cloudformation create-stack --stack-name myserver --template-body file://myservers.yml --parameters file://servers-parameter-file.json --region=us-west-2 --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM

This will create the other infrastructure resources required for the project.
- Security Groups
- Roles
- Launch Configurations
- AutoScaling Groups
- Load Balancers

(4)  In the output of the last run cloudformation script, click on the URL of the Load balancer shown to access the webapp.


```
