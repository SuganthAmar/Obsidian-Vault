# Localized and Centralized VCS
-A localized version control system keeps local copies of the files.
-In centralized source control, there is a server and a client. The server is the
master repository which contains all of the versions of the code.

# Distributed version control systems
• In a distributed version control system each user has a complete
local copy of a repository on his individual computer.

![[Pasted image 20240318212151.png]]

 `git init` -> initialize the empty git repository in the current directory
 **.git** -> this folder maintains all the versions and all the changes
  `git status` -> this will tell you the files that are untracked that should be included in the repo
  `git add .`-> this will start tracking the files on the local changes
  `git commit -m "First commit"` -> this command will commit the changed code into the local changes with some message (-m)

## To Add the User to the GIT
`git config --global user.email "add ur mail"` -> This will add the user of the mail to change and commit the code in this file

`git config --global user.name "Your Name"` -> This will add the Name of the user to change things on the file code

**--global** -> this is used to set the user name for all the repositories


![[Pasted image 20240319104630.png]]

# Remote Repository 
![[Pasted image 20240319104749.png]]


## Two Things to notice after the remote git repo is created 
### 1) create a new repository on command line
To create new repository
**command**

##### Example
![[Pasted image 20240319105200.png]]

### 2) Push an existing repo from the command line

![[Pasted image 20240319105257.png]]

**url** => https://github.com/SuganthAmar/reponame.git
                     username        reponame with .git extension

In the `git push -u origin main` command, the `-u` option stands for `--set-upstream`.

When you push a local branch to a remote repository for the first time, you typically use the `-u` or `--set-upstream` option followed by the remote repository name (`origin` in this case) and the branch name (`main` in this case). This option tells Git to set up a tracking relationship between your local branch and the remote branch.

-------------------------------------------------------------------------
`cat .git/config` -> this will show the new entries

---------------------------------------------------------------

`git branch -M main` -> this will change the branch name from **master** to **main**
  
The `git branch -M main` command is used to rename the current branch to `main`. Here's what each part of the command does:

- `git branch`: This is the Git command used for working with branches.
- `-M`: This is a shortcut for the `--move` option. It tells Git to rename the branch.
- `main`: This is the new name you're assigning to the current branch.

This command is commonly used when you're working with Git repositories where the default branch name is `master`, but you want to rename it to `main`, which is a practice becoming increasingly common to remove potentially problematic terminology.



`git log` -> Shows all the pervious commits to the current branch
`git diff` -> Will show the difference between the file that you have changed i.e what exactly is changed
`git diff --cached` -> Will show the difference between the file that you have changed i.e what exactly is changed **after the file that is been staged**
`git log --oneline` -> Will give the commit id in smaller in character           
`git show "commit_id"` -> Will show what things are newly added in different colour


`git pull` -> this command will pull the code that have been changed by other code to remote repo to local repo

## Branches in GIT

`git branch -c testing`: //testing is the new branch name

- This command is used to create a new branch named `testing` based on the current branch.
- The `-c` option is short for `--copy`, which means it creates a new branch copying the current branch's content.

`git branch -a`:

- `git branch`: This is the Git command used for working with branches.
- `-a`: This option stands for "all" and tells Git to list both local and remote branches.

**Switching Branches**:
- To switch to an existing branch, you specify its name as an argument. For example:

    `git checkout main`
    
    we can also use `git switch main` -> to switch the branches
    
**Creating and Switching to a New Branch**:

- You can create a new branch and switch to it simultaneously by providing the `-b` option followed by the branch name. For example:

    `git checkout -b new-feature`

### Remove:
The `git rm` command is used to remove files from the working directory and the index (staging area) so that they are no longer tracked by Git. Here's how it works:

1. **Remove a File from Git Tracking**:
    
    - If you have a file in your working directory that you want to remove from version control, you can use `git rm` followed by the filename. For example:
        
        `git rm file.txt`
        
2. **Remove Files Matching a Pattern**:
    
    - You can also remove multiple files or files matching a pattern using wildcards. For instance:
        
        `git rm '*.txt'`
        
3. **Remove Files and Keep Them in the Working Directory**:
    
    - By default, `git rm` will remove the files from both the working directory and the index. If you want to keep the files in the working directory but remove them from the index, you can use the `--cached` option. For example:
        
        bashCopy code
        
        `git rm --cached file.txt`
        
4. **Force Removal of Files**:
    
    - If you want to remove files forcefully without checking their status, you can use the `-f` or `--force` option. Be cautious when using this option, as it can lead to permanent data loss. For example:
        
        `git rm -f file.txt`
    `
    
    `git merge testing` -> this command will merge the testing branch to current branch

### GitIgnore File

The `.gitignore` file is a special file in a Git repository that specifies intentionally untracked files to ignore. These files are typically ones that you don't want to include in your version control system for various reasons, such as build artifacts, temporary files, or sensitive information like API keys.

`git push --all origin` -> this will push all the code to that specific branch all at once 

## Clone

`git clone "git repo url"` -> this will clone the remote repo to local machine

# Rollback on GIT

### From Staging Area
`git restore --staged filename` ->

The `git restore --staged` command is used to unstage changes that have been added to the staging area (index) but haven't been committed yet. Here's what it does:

- `git restore`: This command is used to restore files in various ways, such as restoring changes in the working directory or restoring files to a specific commit.
- `--staged` (or `--cached`): This option specifies that the operation should be applied to the staged changes in the index.

`git diff previous_commit_id..current_commit_id` -> This will show the diff between the two commit difference in the remote repo

### Revert

The `git revert` command is used to create a new commit that undoes the changes made by a previous commit. Unlike `git reset`, which rewrites history by removing commits, `git revert` creates new commits to reverse the effects of past commits while preserving the commit history.

Here's what `git revert` can do:

1. **Undo Specific Commits**:
    
    - You can use `git revert` to undo the changes introduced by one or more specific commits. For example:
        
        `git revert <commit-hash>`
        
2. **Undo Multiple Commits**:
    
    - You can revert multiple commits in a single operation by specifying a range of commits. For example:
        
        `git revert <start-commit>..<end-commit>`
        
3. **Undo Merge Commits**:
    
    - `git revert` can also be used to revert merge commits, which can be particularly useful for resolving conflicts or undoing changes introduced by a merge. For example:
        
        `git revert -m 1 <merge-commit-hash>`
	
	HEAD -> will always point to the current latest commit

# GIT SSH 

## To create a public and private key
`ssh-keygen.exe`

copy the content of the **public key** and paste it in the 
github.com -> settings -> ssh and gpg keys -> give title and paste the key over there.

## GIT CHEAT SHEET

![[Pasted image 20240319181654.png]]

![[Pasted image 20240319181730.png]]
