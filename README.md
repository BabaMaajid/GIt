

# AWS cloud
# Agenda of The Section
- Creation of AWS Account
- Setting Up of Account(IAM User and MFA)
- Configure CLI
- Hnads On-IAM
- IAM Policy Generator
- S3 Bucket(Creation ,Versioning,Lifecycle Management)
- EC2 Instances(Launch and SSH)
# Creation of AWS Account
- Go to (https://aws.amazon.com/free/) for creation of the account(Root user emailid)
- 
- 


- 
## CI-CD Pipeline
- A Practice where code changes are automatically built,tested and getting it ready for a production release.
- Automate build and test
- Deploy tto pro environmnet sfely without business downtimme
- Faster Deployment
**Most fundamental concept in the automated software develeopement**
- ### Continuous Integration
     - Develeopers practicing continuous integration merge their changes back to the main branch as often as possible.
     - Developers chages are validated by creating a build and runing automated tests agianst the build.
     - This avoids integration challenges that can heppen when waiting for release day to metrge changes into the release branch.
     - This puts a great emphasis on testing automation to check that the application is not broken whenevr new commits are integrated into the main branch.extension of c
- ### Continuous Delivery
      - It is an extension of continuous integration since it automatically deploys all code changes to a testing and /or production environment after the build stage.
      - This means that on top of automated testing you have an automated realese process and you can deploy your application  any time by clicking a button.
      -  In theory, with continuous delivery we can decide to release dailay,weekly,fortnight or what ever suits our business requirements.
      -  IF we want to get the benifits of continuous deliver, we should deploy to the production as early as possible to make sure that we release samll batches that are easy to troubleshoot in case of a problem.
- ### Continuous Deployment
      - Continuous deployment goes one step further than continuous delivery. with this practice, every chage that passes all stages of your production pipeline is released in your customers. There's no humna intervnetion, and only a failed test will prevent a new change to be deployed to production.
      - Continuous deployment is an excellent way to accelerate the feedback loop with your customers and take pressure off the team as therre isn't a release day anymore.
      - Developers can focus on building software, and they see their work go live minutes after they have finished working on it.

  ![](CICD(1).jpg)
  ## ENVIRONMENTS FOR APPLICATION
    ![](ENV(3).jpg)
    ## GIt Rebase Vs Git Merge 
## View The Branches 
    - git branch
## Delete The Branches
   - git branch -d branch_name
## Git Log details(All tne commits that have been performed on this master branch)
 - git log --oneline
## Git checkout -b feature

## GIT Rebase
- Rebase is an action in git that allows us to rewrite commits from one branch onto another branch.
- Esentially, Git is deleteing commits from one branch and adding them onto another
- git pull
- git checkout -b dev
- nano index.html(do some modifaction)
- git status
- git add index.html
- git commit -m "changed"
- git checkout master
- editing again 
- emacs index.html
- git add .
- git commit -m "title changed to home"
- Make more changes to master index.html
- emacs index.html
- git add
- git commit -m "Second change done in master file"
## Performing the rebase
- git checkout dev
- I am saying perform the rebase from the master branch
- Before doing that I ma agin swtiching back to master branch
- git log --oneline
## Changes from master branch

- 4fcf21e (HEAD -> master) change home to home_1
- 82ac023 tiltle changet to home
- ec2abc4 home page updated to home
- c222e59 title chaged
- 1aae850 this is my first commit

## Changes from dev branch

- 1ddf9c (HEAD -> dev) title changed to name
- ec2abc4 home page updated to home
- c222e59 title chaged
- 1aae850 this is my first commit

# Now from dev branch I will perform rebase
 - git rebase master

 #### Why rebase
  - The primary reason for rebasing is to maintain a linear project history
 - Unnecesary Merge commit is not required

**Note**  Never rebase commits once they have been pushed to public repository. the rebase would replace the old commits with the new ones and it would look like that part of the project history abruptly vnaishes


# GIT STASH
- git stash save "save message"
- git stash list #lsits the stashed changes.
- git stash apply <stashid>
-  git stash pop # Apply the top changes to my file
-  git stash drop <stashid> droping the stash
-  git stash clear #dropping all stashes

-  for hands on create new repository
  
## AWS Code Commit Security hands on
- Go to IAM dashboard
- Go to  User groups
- Give user  group name
- Attach a Policy
- Create USer group
- now select user group
- go to permissions
   - Add Permissions
     -create inline policy
       - clickJSON
       - Paste file
       - Review Policy
       - Name
       - Create Policy
         
       - 
    
# YAML Files:
## YAML
  - Y: YAML
  - A : Ain't
  - M: Markup
  - L: Language
- YAML is a data serailization language that ia often used for configuration files
- Popular Programming langauge as it is human-readable and easy to understand.
- It can also be used in conjunction with other progrmaming lanuages.

![image](https://github.com/BabaMaajid/GIt/assets/7793038/8246b20e-1835-423b-a8dc-32a95bd3ca63)
|:--:| 


## YAML Syntax
- Uses Python-style indentation to indicate nesting.
- Whitespaces for indentation & Tab are not allowed.
- No Format Symbol like braces, square, brackets, or quotation tags.
- Uses .yml or .yaml extension.
**Best practice is to use small case for keys**
## YAML Structure 
- Structure of a YAML file is a map or a list.
- Maps allows us to assocaite key-value pairs.
- Keys are unique, and the order doesn't matter.
- A mapin YAML needs to be resolved before it can be closed, and a new map is created.
## YAML Data Types
- Scalars(Strings,integers,dates,numbers or Boolean).
- A list(collection of items) and it can start with a dash, with indentaion separating the parent.
- New Map can be created by either increasing indentation level or by resolving the previous map.
# AWS CodeBuild
- Fully managed continuous integration service that compiles source code, run tests, and produces software packages that are ready to deploy
- No need to provision, manage, nad scale our own build servers
- CodeBuild scales continuous and processes multiple builds concurrently, so the builds are not left waiting in a queue
- Get started uding prepackaged build environments or allows aws to create custom build environments
- Charged by minute for the compute resources you use.
# AWS Code Build Works
- A Build Project includes information about how to run a build, including where to get the source code,which build environment to use,which build commnands to run ,and where to store the build output. A build environment represents a combination of OS , Programming language,runtime,tools that codeBuild uses to run.
- CodeBuild uses the build Project to create the environment.
- CodeBuild downloads the source code into the build envirinment and then uses the builkd specifications(buildspec), as defined in the project or included directly in the source code. A Buildspec is a collection of build commands and related settings,in YAML Format, that CodeBuild uses to run a build output.
- if there is any  build output,  the build environment uploads its output to an S3 bucket.
- The build environment sends information to CodeBuild and Amazon CloudWatch logs.
- While the build is running , we can see the AWS code build console,AWS CLI or AWS SDKs to get summarised build information from CodeBuild and detailed build information from Amazon Cloudwatchlogs

![image](https://github.com/BabaMaajid/GIt/assets/7793038/6b4a5c2f-8dd8-492f-8e6b-8c101f952d59)

# Aws Event Bridge
-  Amazon EventBridge is a fully managed event bus service provided by Amazon Web Services (AWS). It simplifies the building and management of event-driven architectures.
-  Go this service and create rules
   - Give rule name
   - select Rule Type with an event pattern or  Schedule
   - -next
   -  select event source
   -  Creation method **use pattern from**
   -  event pattern select **AWS services, Codecommit, ALLevents**
   -  Next
   -  select Target (AWS resource CodeBuildProject)
   -  Project ARN
        - go to codebuild
        - build details(ARN)
# AWS CodeDeploy
- Fully managed Deployment service
- Can automate Software Deployments on Amazon EC2,AWS Fargate,AWS Lambda and On-premise servers.
- Avoid downtime
- Provides Autoscaling as well as Rollback support
# Deploy with AWS CodeDeploy
- AppSpec Configuration file
    - Contains the command to run at each phase of deployment
- Integrate with the existing software delivery toolchain using AWS CodeDeploy APIs.
- Enable Scaling with Aws CodeDeploy
- It Supports two type of deployment configurations
    - In-Place : Update the application on existing instances(expect downtime)
    - Blue Green : Gradually replace existing instance(blue) with Instances running new version(green)
**Deployment Group or Autoscaling group**: This will help us to identify which server to place i.e to which set of E2 services code will be pushed
 - logical identification of my indiviuall Ec2 instances.
   
## Hand ON CODE DEPLOY
1.  Create EC2 with IAM Roles attached (S3) with tags assigned.
    -  S3- to enable EC2 to read Source Code from S3 Bucket
    -  SSM - Allow Deployment Group to Install /update Code Deploy Agent(Optional)
2.  Create Application on code Deploy
3.  Push code Revision to S3 Bucket
4.  Create Deployment Group and Validate CodeDeploy Agent installed with SSM(Which instance to deploy, How to deploy and which version to deploy)
5.  Deploy the application to EC2 insatnces
# appspec.yml
- Application Specification file to manage each deployement as a series of life cycle evnet hooks
- Depending on Application compute platform APPSpec format will be decided.
- Amazon ECS compute platfoem:
    - JSON
    - YAML
    - Directly typed in console
- AWS lambda Compute Platform
    - JSON
    - YAML
    - Directly computed into console
- EC2/on-premises compute paltform
    - Always YAML format
- The AppSpec file is a YAML formatted file or a json fromatted file used by AWS CodeDeploy to manage a deployment and decides:
     - What must be installed onto instances
     - What lifecycle event hook to run
It expects in Root Directory.
# hooks foe an EC2 Deployment 
- AWS CodeDeploy agent runs through a series of steps to perform a deployment . these steps or phases are called events/hooks.
- "hook" is executed once per deployment of an instance
- One r more scripts can be specified in a hook
- Importnat Hooks:
  - Application stop
  - Download bundle
  - BeforeInstall
  - Install
  - AfterInstall
  - ApplicationStart
  - Validate Service
  - BeforeBloockTraffic 
  - AfterBlockTrafic
  - BeforeAllowTraffic 
  - AllowTrafic
  - AfterAllowTraffic
# Deployment Configuration
- OneAtATime
- HalfAtATime
- AllAtOnce
- Custom
 # Code Pipeline
 - Combination of Continuous Integration and Continuous Delivery service for quicker and more reliable infrasture
 - Automaticall Buils, test and Deploys a user code whenever ther is a code change ,based on release process models
 - Integrates with AwS services like CodeCommit,S#,CodeDeploy,Elastic Beanstalk,OpsWorks and Lambda
 - Create Pipeline with GUI or CLI.
# Reasons to USe CodePipeline
- CodePipeLine enables us to increase the speed and quality of the software updates by automating the software build,test and release process.

