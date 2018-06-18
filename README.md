# CAE
CAE is an agnostic and extensible Configuration Audit Engine based on a MicroServices Architecture guidelines with containerized and scalable components for production workloads.

CAE supports increased operational efficiency by providing an automated & standard way of auditing VNF configurations.

![alt text](https://github.com/moffzilla/CAE/blob/master/media/CAE-Conceptual.png)
 	
	
## Requirements

- Running on Xenial (Cores=2 Mem=8G Root-Disk=30G)
- This project has tested it in AWS Region: us-east-1
- The Demo deployment is self-contained ( all CAE components including ElasticSearch )
- The Ansible Playbook provided is for reference, it helps to provision an AWS instance, install Docker & Docker Compose (1.16.1),build CAE base image and deploy a basic set up for testing
- Make sure resources as the AMI image, SSH Keys, Security Groups referenced in the artifacts exist in the selected region.
- You’ll need AWS CLI installed.
- You will need installed this Python module & Boto can be installed from your OS distribution or python’s using the pip command, install the AWS CLI and Boto3
- Before executing make sure you have access to AW
    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY
    AWS Region
- More minimum requirements can be found examining the Playbooys, make sure to update your personal settings, e.g. ssh-key
## Deployment

Run Self-Contained Playbook
 
	Under "~/deploy"

Execute:

	ansible-playbook ec2_module-cae.yml -vvvv --user=ubuntu

You can ingest your own reference configuration by using onap-dump :

	python tools/onap-dump.py -H [ElasticSearch IP] -p [vnf-vendor] -d  tools/data/master/[Master-Configuration].json

You can Audit your own runtime configuration by  :

	python tools/onap-pipe.py -H [Redis-IP] -d tools/data/config/[VNF-Config]

You can launch the basic CAE GUI :

	docker run --net=cvaas001dev148_default -d -p 5000:5000 --privileged=true -e ELASTICHOST=172.18.0.3:9200  --name cvaas-gui moffzilla/cvaas-gui:dev340 /bin/bash -c "./web/run.sh 172.18.0.6"
	
	
	
