kubectl 

1. Setup kubectl 
   a. Download kubectl version 1.21
   b. Grant execution permission 
   c. move to /usr/local/bin 
   d. Test that your kubectl installation was successful  
   ```sh 
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   mv ./kubectl /usr/local/bin 
   kubectl version --short --client
   ```
2. Setup eksctl (make sure kubeclt and eksctl both are same version)
   a. Download and extract the latest release 
   b. Move the extracted binary to /usr/local/bin
   c. Test that your eksclt installation was successful 
   ```sh
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   eksctl version
   ```
  
3. Create an IAM Role 
   `Note: create IAM user with programtic access if your bootstrap system is outside of AWS`
   IAM user should have access to 
   IAM
   EC2
   VPC
   CloudFormation


4. Create your cluster and nodes 
   eksctl create cluster \
   --name my-cluster \
   --region ap-south-1 \
   --node-type t2.small \
   --nodes-min 2 \
   --nodes-max 2
