## CI-CD Pipeline
**Most fundamental concept in the automated software develeopement**
- ### Continuous Integration
     - Develeopers practicing continuous integration merge their changes back to the main branch as often as possible.
     - Developers chages are validated by creating a build anf runing automated tests agianst the build.
     - This avoids integration challenges that can heppen when waiting for release day to metrge changes into the release branch.
     - This puts a great emphasis on testing automation to check that the application is not broken whenevr new commits are integrated into the main branch.extension of c
- ### Continuous Delivery
      - It is an extension of continuous integration since it automatically deploys all code changes to a testing and /or production environment after the build stage.
      - This means that on top of automated testing you have an automated realese process and you can deploy your application  any time by clicking a button.
      -  In theory, with continuous delivery we can decide to release dailay,weekly,fortnight or what ever suits our business requirements.
      -  IF we want to get the benifits of continuous deliver, we should deploy to the production as early as possible to make sure that we release samll batches that are easy to troubleshoot in case of a problem.

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
- Esentially, Git is delteing commits from one branch and adding them onto another
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
       - 
    
- 




