# The Git & Github Bootcamp

## Section 6. Working With Branches
---
### 6.41 What Really Matters In This Section
**Critical:** Branching? What is it? Why use it? Understanding Git HEAD, Git Branch, Git Switch, Git Checkout
**Importatn:** Deleting & Renaming Branches, Master VS. Main Branch
**Nice To Have** HEAD & Refs behind the scenes

[Section Slide: S6_Git+&+Github_+Branching.pdf](doc/S6_Git+&+Github_+Branching.pdf)

----

### 6.42 Introducing Branches
![Commit Chains](img/42_1_CommitChains.png "Commit Chains")
![Branches](img/42_2_Branches.png "Branches")

----

### 6.43 The Master Branch (Or is It Main?)
![Master Branch 1](img/43_1_MasterBranch_1.png "Master Branch 1")
![Master Branch 2](img/43_2_MasterBranch_2.png "Master Branch 2")
![Master Branch 3](img/43_3_MasterBranch_3.png "Master Branch 3")

----

### 6.44 What On Earth Is HEAD?
![HEAD](img/44_1_HEAD.png "HEAD")

The most recent commit to the current checkout branch is indicated by the **HEAD**. A pointer to any reference, in a sense. The “current branch” can be thought of as the HEAD. The HEAD is moved to the new branch when you use the “checkout” command to swap branches.

**HEAD** is the reference to the most recent commit in the current branch. This means HEAD is just like a pointer that keeps track of the latest commit in your current branch. However, this definition just gives us a basic overview of HEAD, so before deep diving into HEAD let us learn about two things before that is **refs** and **head**.

When you initialize your local directory to a git repository, you see that a .git folder is created. Let us now create a file demo.txt and add this file to the staging area and commit the changes. 

Now let us get into the .git/refs folder, we can see two more subdirectories being created which are heads and tags. Inside the heads folder, you can find the branch names such as master, main, etc, and in tags such as v0.2, v0.3, etc. These are all examples of refs. 


When we talk about branch names in the heads folder, a ref such as master represents the tip (latest commit ID) on that branch and this is called head. In this folder, we can find different files for different branches and each file will represent the latest commit ID of that branch. So, if any of the new commits is made this file keeps track of the latest commits.

----

### 6.45 Viewing All Branches With Git Branch
Document: [git branch](https://git-scm.com/docs/git-branch)
![View Branch](img/45_1_ViewBranch.png "Viewing Branches")
The branch name with __*__ before the branch name is current branch.

----

### 6.46 Creating & Switching Branches
Document: [git branch](https://git-scm.com/docs/git-branch)
Document: [git switch](https://git-scm.com/docs/git-switch)
![Create Branch](img/46_1_CreateBranch.png "Creating Branches")
![Switch Branch](img/46_2_SwitchBranch.png "Switching Branches")

----

### 6.47 More Practice With Branching
`git commit -a -m "xxxxxxxxx"` sample we to add and commit.

----

### 6.48 Another Option: Git Checkout Vs. Git Switch
`git checkout` can do similar thing of `git switch`
Document: [git checkout](https://git-scm.com/docs/git-checkout)
![Checkout](img/48_1_Checkout.png "Checkout")
`git checkout -b <branch-name>` is to create a new branch and switch to new branch.
![Creating & Switching](img/48_2_Switch_Create.png "Creating & Switching")

----

### 6.49 Switching Branches With Unstaged Changes?
It will report an error if we switch branches with unstaged changes for the exist files.
If the unstaged changes are create new files and doesn't conflict another branch, there is no error and the unstaged new files will keep in local repo.

Whatever, suggest to stage the changes before switch the branches.

----

### 6.50 Deleting & Renaming Branches
Document: [git branch](https://git-scm.com/docs/git-branch)

Use the `git branch -d <branch_name>` or `git branch --delete <branch_name>` to delete a branch.
* Can't delete the current branch. Before delete branch, must switch to other branches;
* Report ERROR, if the delete branch not fully merged. If want to continue delete a un-merged branche, use `git branch -D <branch_name>` or `git branch --delete --force <branch_name>`.
  
Use the `git branch -m <branch_name>` or `git branch --move <branch_name>` to move/rename a branch and corresponding reflog.
* Rename must on the branch, which need to rename;

----

### 6.51 How Git Stores HEAD & Branches

The Git HEAD is saved in `.git/HEAD`. 
If we run `cat HEAD`, it will show `ref: refs/heads/master`. That means current `HEAD` is get from `master` branch last commit.

We can open the head files in `.git/refs/heads/**`. Each file name is the branch name and each file saved the corresponding last commit as its head.


----

### 6.52 Branching Exercise
[Branching Exercise](https://plum-poppy-0ea.notion.site/Branching-Exercise-b5460c881d56400cb046357d9a430bf8)

Sample Code:
```
 1977  mkdir Patronus
 1978  ls
 1979  cd Patronus
 1980  git init
 1981  git branch -m main
 1982  touch patronus.txt
 1983  ls
 1984  git add .
 1985  git commit -m "add empty patronums file"
 1986  git branch harry
 1987  git branch
 1988  git branch snape
 1989  git checkout harry
 1990  git switch harry
 1991  code .
 1992  git add .
 1993  git commit -m "add harry's stag patronus"
 1994  git checkout snape
 1995  code .
 1996  git add .
 1997  git commit "add snape's doe patronus"
 1998  git commit -m "add snape's doe patronus"
 1999  git branch lily
 2000  git switch lily
 2001  code .
 2002  git add .
 2003  git commit -m "add lily's doe patronus"
 2004  git branch
 2005  git branch -d snape
 2006  git branch
 ```
