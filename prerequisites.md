### AWS prerequisites for ROSA with STS

Setting the AWS security token version
If you want to create a Red Hat OpenShift Service on AWS (ROSA) cluster with the AWS Security Token Service (STS) in an AWS opt-in region, you must set the security token version to version 2 in your AWS account.

Prerequisites
You have installed and configured the latest AWS CLI on your installation host.
1. List the ID of the AWS account that is defined in your AWS CLI configuration:
```
aws sts get-caller-identity --query Account --output json
```
Ensure that the output matches the ID of the relevant AWS account.
2. List the security token version that is set in your AWS account:
```
aws iam get-account-summary --query SummaryMap.GlobalEndpointTokenVersion --output json
```
Example output
```
1
```
3. To update the security token version to version 2 for all regions in your AWS account, run the following command:
```
aws iam set-security-token-service-preferences --global-endpoint-token-version v2Token
```
Red Hat managed IAM references for AWS
With the STS deployment model, Red Hat is no longer responsible for creating and managing Amazon Web Services (AWS) IAM policies, IAM users, or IAM roles.

### Provisioned AWS Infrastructure
This is an overview of the provisioned Amazon Web Services (AWS) components on a deployed Red Hat OpenShift Service on AWS (ROSA) cluster. For a more detailed listing of all provisioned AWS components, see the OpenShift Container Platform documentation.

EC2 instances
AWS EC2 instances are required for deploying the control plane and data plane functions of ROSA in the AWS public cloud.

Instance types can vary for control plane and infrastructure nodes, depending on the worker node count. At a minimum, the following EC2 instances will be deployed:

 - Three m5.2xlarge control plane nodes

 - Two r5.xlarge infrastructure nodes

 - Two m5.xlarge customizable worker nodes

### AWS Elastic Block Store (EBS) storage
Amazon EBS block storage is used for both local node storage and persistent volume storage.

  Volume requirements for each EC2 instance:

    Control Plane Volume

    Size: 350GB

    Type: io1

    Input/Output Operations Per Second: 1000

    Infrastructure Volume

    Size: 300GB

    Type: gp2

    Input/Output Operations Per Second: 900

    Worker Volume

    Size: 300GB

    Type: gp2

    Input/Output Operations Per Second: 900

### Elastic load balancers
Up to two Network Elastic Load Balancers (ELBs) for API and up to two Classic ELBs for application router. For more information, see the ELB documentation for AWS.

### S3 storage
The image registry and Elastic Block Store (EBS) volume snapshots are backed by AWS S3 storage. Pruning of resources is performed regularly to optimize S3 usage and cluster performance.

  - Two buckets are required with a typical size of 2TB each.

### VPC
Customers should expect to see one VPC per cluster. Additionally, the VPC will need the following configurations:

 - **Subnets**: Two subnets for a cluster with a single availability zone, or six subnets for a cluster with multiple availability zones.

 - **Router tables**: One router table per private subnet, and one additional table per cluster.

 - **Internet gateways**: One Internet Gateway per cluster.

 - **NAT gateways**: One NAT Gateway per public subnet.

