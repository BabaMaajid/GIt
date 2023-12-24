## GIt Rebase Vs Git Merge 
# View The Branches 
    - git branch
# Delete The Branches
   - git branch -d branch_name
# Git Log details(All tne commits that have been performed on this master branch)
 - git log --oneline
# Git checkout -b feature

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





