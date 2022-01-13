# GIT 

------

## Workflow

A **repository** a.k.a. **repo** is nothing but a collection of source code.

There are four fundamental elements in the Git Workflow.

**Working Directory**, **Staging Area**, **Local Repository** and **Remote Repository**.

![git_workflow](https://data.exactspace.co/docs-img/git_workflow.png)

1. **It can be staged.** Which means the files with the updated changes are marked to be committed to the local repository but not yet committed.
2. **It can be modified**. Which means the files with the updated changes are not yet stored in the local repository.
3. **It can be committed**. Which means that the changes you made to your file are safely stored in the local repository.

## Commands

#### Configurations

##### git config

Configure your credentials to the current repository

```shell
git config user.name "Your Name Here"
git config user.email your@email.com
```

Configure credential globally

```shell
git config --global user.name "Your Name Here"
git config --global user.email your@email.com
```

Unset the configs

```shell
git config --global --unset user.name
git config --global --unset user.email
```

##### Edit config

```shell
git config --global --edit
```

#### Initializing Git

##### git clone

Every user “clones” a copy of a repository (a collection of files) and has the ***full\*** history of the project on their own hard drive. This clone has *all* of the metadata of the original while the original itself is stored on a self-hosted server or a third party hosting service like GitHub. Locate to the directory you want to clone the repo. Copy the link of the repository you want and enter the following

```shell
git clone remote_repository_URL
```

##### git pull 

command to get files from the remote repository directly into the working directory. It is equivalent to a `git fetch` and a `git merge`.

```shell
git pull origin master
```

##### git branch

Lets you know the current branch you are on.

```shell
git branch
```

##### git checkout

Switch to a different branch

```shell
git checkout branchname
```

##### Create a branch

```shell
git checkout -b branchname
```

#### Contributing to the repo

##### git add 

command to add a file that is in the working directory to the staging area.

```shell
git add .
```

**Note**: "." specifies to add all the changes in the current directory. If you want to add specific file

```shell
git add file.txt 
```

##### git status

Lists all new or modified files to be committed

```shell
git status
```

##### git commit 

command used to add all files that are staged to the local repository.

```shell
git commit -m "commit message"
```

##### git push 

command to add all committed files in the local repository to the remote repository. So in the remote repository, all files and  changes will be visible to anyone with access to the remote repository.

```shell
git push -u origin your_branch_name
```

##### Uncommit changes

Remove the most recent commit

```shell
git reset HEAD~1
```

Commit again!

##### Revert back to the last commit

you can choose to revert back to the last committed version by entering:

```shell
git checkout .
```

OR for a specific file

```shell
git checkout -- <filename>
```

#### Other commands

##### git log

You can use the **git log** command to see the history of commit you made to your files:

```shell
git log
```

##### git fetch and merge

```shell
git fetch AND git merge
```

When you use `git pull`, Git tries to automatically do your work for you. **It is context sensitive**, so Git will merge any pulled commits into the branch you are currently working in. `git pull` **automatically merges the commits without letting you review them first**. 

When you `git fetch`, Git gathers any commits from the target branch that do not exist in your current branch and **stores them in your local repository**. However, **it does not merge them with your current branch**. This is particularly useful if you need to keep your repository up to  date, but are working on something that might break if you update your  files. To integrate the commits into your master branch, you use `git merge`.

##### Delete branch

```shell
git branch -d branch_name
git branch -D branch_name
```

**Note:** The -d option is an alias for --delete, which only deletes the branch if it has already been fully merged in its upstream branch. You could also use -D, which is an alias for --delete --force, which deletes the branch "irrespective of its merged status." [Source: man git-branch] 

##### Hard reset

```shell
git reset --hard origin/<branch_name>
```

##### Pull from a specific branch

```shell
git pull origin other-branch
```

