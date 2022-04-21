# Getting started with ROSA
**Creating your first ROSA Cluster**

If you'd like an easy to follow guide for creating your first ROSA cluster:

1. Please review the [prerequisites](https://github.com/nedoshi/Red-Hat-OpenShift-Service-on-AWS/blob/main/prerequisites.md) which contains important information about the AWS account requirements.You will need the following pieces of information from your AWS account:
    - AWS IAM User
    - AWS Access Key ID
    - AWS Secret Access Key
2. Account Setup
* A Red Hat account

  If you do not have a Red Hat account, create one here https://console.redhat.com/. Accept the required terms and conditions. Then check your email for a verification link.
  
* Install the AWS CLI

  [Install the AWS CLI](https://aws.amazon.com/cli/) as per your operating system.
  
* Enable ROSA

  Complete this step if you have not enabled ROSA in your AWS account.
  Visit https://console.aws.amazon.com/rosa to enable your account to use ROSA.
  Click on the orange "Enable OpenShift" button on the right.It will take about a minute and then you will see a green "service enabled" bar at the top

* Install the ROSA CLI#

  Install the ROSA CLI as per your operating system.
  
  Download and extract the relevant file for your operating system
  ```ex: tar -xvf rosa-linux.tar.gz```
  
  Save it to a location within your "PATH".
  ```ex: sudo mv rosa /usr/local/bin/rosa```
  
  Run rosa version to make sure it works and that it returns the version number.
  
* Install the OpenShift CLI#

  There are a few ways to install the oc CLI:

    a. If you have the rosa CLI installed, the simplest way is to run rosa download oc
          - Once downloaded, untar (or unzip) the file and move the executables into a directory in your PATH

    b. Or, you can [download and install](https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/getting-started-cli.html#installing-openshift-cli) the latest OpenShift CLI (oc)
