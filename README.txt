Follow the procedure below to deploy this cloudformation script.
(1) Create the S3 bucket and let the developers upload the files to be deployed inside it.
(2) Create the network infracstructure by running the cloud formation script to deploy it as below.

aws cloudformation create-stack --stack-name myinfra --template-body file://myinfra.yml --parameters file://infra-parameter-file.json --region=us-west-2 

(3) Create other required infracstructure by running below.

aws cloudformation create-stack --stack-name myserver --template-body file://myservers.yml --parameters file://servers-parameter-file.json --region=us-west-2 --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM

(4) In the output of the last run cloudformation script, click on the URL of the Load balancer shown to access the site. 