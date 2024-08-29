# CHAPTER 4: HANDS-ON LAB

- creating EKS form cli command example

`eksctl create cluster --name dev --region us-east-1 --zones=us-east-1a,us-east-1b,us-east-1d --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed`

- check aws version `aws --version`

- download and upgrade aws cli v2: 
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
which aws																			// determine location of aws executable file
sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update		// update it
aws --version

```

- configure aws with user credential

```
aws configure

note that Default output format is json

```

- Downloading and installing kubectl 

```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin						// copy the binary to diretory PATH
kubectl version --short --client																		// make sure kubectl is installed 
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp		// download eksctl
sudo mv /tmp/eksctl /usr/bin																			// move the extracted binary to the path /usr/bin
eksctl --version																						// check eksctl version
eksctl help 

```

## Provision an EKS Cluster

- Provision an EKS cluster with three worker nodes in us-east-1:

`eksctl create cluster --name dev --region us-east-1 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed`

> in case occur error, just play around as bellow: 

`` AWS::EKS::Cluster/ControlPlane: CREATE_FAILED – "Resource handler returned message: \"Cannot create cluster 'dev' because us-east-1e, the targeted availability zone, does not currently have sufficient capacity to support the cluster. Retry and choose from these availability zones: us-east-1a, us-east-1b, us-east-1c, us-east-1d, us-east-1f (Service: Eks, Status Code: 400, Request ID: 21e7e4aa-17a5-4c79-a911-bf86c4e93373)\" (RequestToken: 18b731b0-92a1-a779-9a69-f61e90b97ee1, HandlerErrorCode: InvalidRequest)"``

- reenter this command: 

`eksctl create cluster --name dev --region us-east-1 --zones us-east-1a,us-east-1b,us-east-1c,us-east-1d,us-east-1f --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed`

> you can check it out the eks creating log via cloudformation.

- in In the CLI of EC2, check the cluster

```
eksctl get cluster
aws eks update-kubeconfig --name dev --region us-east-1
```

- Creating simple application on your EKS cluster

``git clone https://github.com/ACloudGuru-Resources/Course_EKS-Basics``

> take a note that, need to creat service LB before create deployment or pod, since the pod need to point to the service when it created in time

- checking the application from the outside

`curl "<LOAD_BALANCER_DNS_HOSTNAME>"`

- Test high availability cluster, by delete all of 3 worker nodes, you should see the ability of EKS when provide the high availability for your eks cluster.

- finale step of lab: delete your eks cluster `eksctl delete cluster dev --region us-east-1`, if need, enter your console to delete 3 worker nodes, and IAM account.


