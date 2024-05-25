# Steps to create k8s cluster with `kops` tool on AWS Cloud

## Pre-reqs
Buy a public DNS domain (e.g on hostinger, or godaddy) e.g cdstrainings.io

Steps on AWS
 create a Route53 Public hosted zone for the subdomain of cdstrainings.io e.g myk8s.cdstrainings.io
 create nameserver records on DNS domain (cdstrainings.io) with values from AWS Route53 hosted zone
 create s3 bucket (default settings) myk8s-cdstrainings-kops-state 
 create ubuntu VM
 create IAM role and attach the role the VM

Steps on the Ubuntu VM
```bash
sudo apt update -y
sudo apt install awscli
aws config #optional if IAM role isn't attached to the VM
ssh-keygen
# install kubectl , get installation steps from kubernetes.io documentation , copy the binary to /usr/local/bin
# install kops , get the binary from the github.com/kubernetes releases, copy the binary to /usr/local/bin
kops version
kubectl version
nslookup --type=ns myk8s.cdstrainings.io
kops create cluster --name myk8s.cdstrainings.io \
--state=s3://myk8s-cdstrainings-kops-state --zones=eu-west-2a,eu-west-2b \
--node-count=2 --node-size=t2.micro --master-size=t3.medium \
--dns-zone=myk8s.cdstrainings.io --node-volume-size=8 --master-volume-size=8
# above kops command create cluster configuration

# run the kops update cluster --name <> with the s3 bucket flag/option as --state=s3:// and --yes flag, and --admin flag

# wait for 15mins atleast
# kops validate cluster --state=s3://

# kops creates .kube/config in your home directory
# kope delete cluster --name <> --state=s3://
```

Checks the resources on AWS
 new VPC is created
 VMs are create (one for master, two for nodes)
 Autoscaling groups
 Route53 hosted zone for subdomain, entries for API Server endpoint

