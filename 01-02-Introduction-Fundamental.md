# CHAPTER 1: INTRODUCTION

# CHAPTER 2: EKS FUNDAMENTAL

![container architecture](https://github.com/hassj/EKS-GURU/blob/main/01-Image/01-container-intro.JPG)

## Chapter 2.3: EKS 101

[docker hub](https://hub.docker.com/search?q=&type=image&image_filter=official)

[docker official image](https://docs.docker.com/trusted-content/official-images/)

1. Certified kubernetes conformant

2. High availability and scale your cluster

3. Self-healing

![serverless on aws](https://github.com/hassj/EKS-GURU/blob/main/01-Image/02-serverless-in-aws.JPG)

![eks terminology](https://github.com/hassj/EKS-GURU/blob/main/01-Image/02-eks-terminology.JPG)

![summary](https://github.com/hassj/EKS-GURU/blob/main/01-Image/02-eks-intro-sum.JPG)

- Some of command usefull on eks : ``eksctl`` 

> the compute used in AWS is EC2 (the application statefull) and fargate (application running stateless) 

## Chapter 2.4: Advantages of EKS

EKS can deeply integrated with many of service running and supported on AWS such as:

- cloudtrail : logging of user and API activity 

- cloudWatch: monitoring and control plane logs

- Identity access management (IAM): authentication, authorization and permissions

- VPC: network isolation, security groups, network ACL

- Auto scaling group: allows to scaling the application automatically

- Elastic load balancing (ELB): Expose your app to the internet

### EKS control plane

- supported the ability of high available across 3 AZ zones in a single region

- latest patches and security applied automatically.

- single tenant, it's not share to any EKS cluster or any AWS account.

### Getup and running

- You can create a eks cluster with multi node, multi-AZ 

- no vendor lock in

## Chapter 2.5: Working with EKS

[Objects in kubernetes](https://kubernetes.io/docs/concepts/overview/working-with-objects/)

[Mange k8s objects via configuration file](https://kubernetes.io/docs/tasks/manage-kubernetes-objects/declarative-config/)

