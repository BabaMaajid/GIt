
# Installing the CodeDeploy agent on EC2
```YAML

- Create EC2 Instance with IAM Role attached
    - Assign the Policy `AmazonS3ReadOnlyAccess` to allow CodeDeploy agent to read the version from S3 Bucket
    - Add User Data as mentioned below
- Assign tags to EC2 Instances
- Launch the instance and run the command - `sudo service codedeploy-agent status` to validate - CodeDeploy Agent is not running in EC2 instance
- Create an Application in CodeDeploy
- Push app revision to S3 Bucket (create a S3 bucket with versioning if its not created) - see section - **deploy the files into S3** below
- Create a Service Role for CodeDeploy and assign Codedeploy policy
   - go to IAM
   - Create a service role
   -   Service or use case(Code deploy)
        - rule name
- Create CodeDeployment Group and assign IAM role created above
    - go to deployment
     - select the application
    -create Development group
       - give name
        - assign service rule as done in previous step
         - Amazon ec2 instance
          - Key name and value dev server
          - disalbe the loadbalance



- Do necessary settings and create Code Deployment
- Run the Deployment
- Verify whether the website is working (Make sure to check the security group of ec2 instance)
```
# Manual Steps for CodeDeploy Agent
```
sudo yum update -y
sudo yum install -y ruby
sudo yum install -y wget
cd /home/ec2-user
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status

#If error
sudo service codedeploy-agent start
sudo service codedeploy-agent status
```


# create a bucket and enable versioning
## https://docs.aws.amazon.com/cli/latest/reference/s3/mb.html
## https://docs.aws.amazon.com/cli/latest/reference/s3api/put-bucket-versioning.html
```
aws s3 mb s3://aws-manifold-devops --region ap-south-1 
aws s3api put-bucket-versioning --bucket aws-majid-devops --versioning-configuration Status=Enabled --region ap-south-1 



# deploy the files into S3
# https://docs.aws.amazon.com/cli/latest/reference/deploy/push.html
```
aws deploy push --application-name demo-app --s3-location s3://aws-majid-devops/demo-app/app.zip --ignore-hidden-files --region ap-south-1 
```

# Automatically run for multiple CodeDeployAgent
select the EC2 service --> Actions--> Image and templates-->Launch moer like this
# User data
```
#!bin/bash
sudo yum update -y
sudo yum install -y ruby wget
wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
```
# How to Create EC2 Instance
1. EC2
2. Insatances
3. launch Instances
   - Name(Dev-server)
   - Amazon linux AWS
      - Amazon lInux 2AMI(HVM)
    - Instance type(t2.micro)
    - Key pair create
    - Network Settings
       - Allow all the threes
    - Configurage storage
       - 10 GB
    - Advnaced details
       - Create new IAM Profile(Should have permissions for Acessesing S3 Bucket)
           - Create Role
                - Aws Service
                - Use case (EC2) --> Next
                - Amzons3readonly --> Next
                - Role name(give any name) and keep remaining settings as it is --->Create role
    - Specify the user-data(nOt specified)
    - EC2 Instance Created
    - Now for this EC2 I have to run  CodeDeploy agent for this indiviual EC2 instance as CDA is the one that        is which is able to commincate with this deploy service to                  
             
