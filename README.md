# CAE
CAE is an agnostic and extensible Configuration Audit Engine based on a Ms Architecture.

 	
## Requirements

- Running on Xenial (Cores=2 Mem=8G Root-Disk=30G)
- This project has tested it in AWS Region: us-east-1
- Please note that we mount an extra volume and use as default for Docker storage.
- Make sure resources as the AMI image, SSH Keys, Security Groups referenced in the artifacts exist in the selected region.
- This project defaults region US-West-1 (N. Virginia) & uses Ubuntu 16.04 guess OS.
- You’ll need AWS CLI installed.
- Before executing make sure you have access to AWS
    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY
    AWS Region
- More minimum requirements can be found examining the Playbooys.
- You will need installed this Python module & Boto can be installed from your OS distribution or python’s using the pip command, install the AWS CLI and Boto3:

## Deployment

Create the host with AWS CloudFormation
 
	Under "~/deploy"

Execute:

	aws cloudformation create-stack --stack-name ONAP-stack --template-body file://$PWD/deploy/aws-cloudformation-ONAP-Docker-Base.json

You can replace the following default settings:

	KeyName": "generic-cloud-wk"
	
	AnsibleRepository": https://github.com/moffzilla/ONAP.git"
	
	AnsiblePlaybook: "deploy/ap_onap.yml"
  
        OOMTemplate: "minimal.cfg.j2"
