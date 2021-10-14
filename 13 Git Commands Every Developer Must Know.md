# 13 Git Commands Every Developer Must Know



Reference: https://zepel.io/blog/13-git-commands/



### 1. Git Init



The git init command is usually the first command you’d run in any new project that is not already a Git repository (also commonly called repo).

It can be used to convert an existing, un-versioned folder into a Git repository. Also, you can use it to initialize an empty repo.

**Using Git Init Command**

`**cd**` into the directory you want to initialize.

Then, run this command.

```git
$ git init
```

Copy

This will transform the current directory into a Git repository. A `**.git**` sub-directory will be added. This will allow you to start recording multiple versions of your project.

*Note: Running* `**git init**` *on an already initialized directory will not override any of your settings.*

------

### 2. Git Clone



The git clone command is used to download the source code from a remote repository (like GitHub, Bitbucket, or GitLab).

**Using Git Clone Command**

```terminal
$ git clone <https://url-of-the-repository>
```

Copy

When you clone a repo, the code is automatically downloaded to your local machine.

As a convenience, the downloaded version is linked to the origin (the repository from where you downloaded). I say this is a convenience because when you’re collaborating on the same project, you’d want to push your changes (more on that below) to a single repo.

But sometimes, people wouldn’t want to have this link. If your use case is similar, run

```terminal
$ git remote rm origin
```

Copy

This will disassociate the downloaded current repository from the origin.

------

### 3. Git Branch



Branch is one of the most important functionalities of Git. This allows teams to work on the same code base in parallel. It enables teams to create [Git Workflows](https://zepel.io/blog/5-git-workflows-to-improve-development/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands) and make their workflows more efficient.

Say, you’re working on “*Feature A*”. And your teammate is working on “*Feature B*”. By creating a separate branch for each feature, both of you can work on the same code base in parallel without having to worry about conflicts (at least while you’re writing the code).

You can use this command to create a new branch, view existing branches, or delete a branch.

**Using Git Branch to create a new branch**

```terminal
$ git branch <branch-name>
```

Copy

This command will create a new branch only in your local system. If you want this to be visible to all the members in the repo, you’ll still have to push the branch.

To push a newly created branch, run *`**git push -u <remote> <branch-name>**`*

*Here's a detailed article on [how to create a new branch in GitHub](https://zepel.io/blog/how-to-create-a-new-branch-in-github/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands)* →

**Command to view all branches**

```terminal
$ git branch
```

Copy

or

```terminal
$ git branch --list
```

Copy



**Git command to delete a branch**

```terminal
$ git branch -d <branch-name>
```

Copy

------

### 4. Git Checkout



A mistake I often made when I first started learning git commands was forgetting to switch to the new branch I just created. Yes, after you create a branch, you’ll have to switch to it with another command. That’s where the Git Checkout command comes in.

**Using Git Checkout Command**

```terminal
$ git checkout <branch-name>
```

Copy

This will automatically switch you to the branch name you mentioned in the command.

However, when switching from one branch to another, you need to keep two things in mind:

- If you made some changes in the previous branch, you will have to first commit and push them (I’ll cover this command below) to your remote repo.
- The branch you want to switch must be present in your local system. If not, you can pull them (covered below).

If you’re as lazy as I am, I’m sure you’d want one single command that will both create a new branch and automatically switch to it.

The below command does exactly that.

```terminal
$ git checkout -b <branch-name>
```

Copy

------

### 5. Git Add



Every time you create a new file, delete it, or make a change, you’ll have to tell Git to track it and add it to the staging area. Otherwise, the files you made changes to wouldn’t be added when you try to push your changes.

**Using Git Add Command**

```terminal
$ git add <file-name>
```

Copy

This command will add only a single file to your next commit. If you want to add all the files to which changes were made, you can use

```terminal
$ git add -A
```

Copy

It’s important to remember that using git add will not make any changes in the remote repository. Your changes will be recorded only when you commit them.

------

### 6. Git Commit



Think of Git Commit command like a checkpoint in your development process.

It’s commonly used to save your changes. Maybe after completing a specific work item assigned to you in your [agile tool](https://zepel.io/blog/agile-tools/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands).

Every time you commit your code changes, you’ll also include a message to briefly describe the changes you made. This helps other team members quickly understand what was added, changed, or removed.

**Using Git Commit Command**

```terminal
$ git commit -a
```

Copy

This will commit all the changes in the directory you’re working in. Once this command is run, you’ll be prompted to enter a commit message.

Alternatively, you can enter the commit message in the command itself and skip the additional step where you’ll be prompted to enter the commit message.

To do this, run the following git command:

```terminal
$ git commit -am “<commit-message>”
```

Copy

*Note: The git commit command saves the changes only in your local repository. It does not push to the remote origin and make your changes accessible for others to collaborate.*

*Here's a detailed article on [how to commit code changes to GitHub](https://zepel.io/blog/how-to-commit-to-github/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands)* →

------

### 7. Git Push



To make all your committed changes available to your teammates, you’ll have to push them to the remote origin.

**Using Git Push Command**

```terminal
$ git push <remote> <branch-name>
```

Copy

It’s important to remember that git push command will upload only the changes you’ve committed.

------

### 8. Git Pull



Of course, you’d want to have the latest updates from teammates as well!

The git pull command allows you to fetch all the changes that your teammates pushed and automatically merge them into your local repo.

**Using Git Pull Command**

```terminal
$ git pull <remote>
```

Copy

In many cases, you will run into conflict because you had changed a line in a file that another teammate added. In such cases, you need to resolve the conflicts manually.

------

### 9. Git Diff



Git Diff is my go-to command when I want to quickly see the difference between my current branch and another branch (usually the branch I’m merging into).

**Using Git Diff Command**

```terminal
$ git diff
```

Copy

This will show you any uncommitted changes in your local repo.

**To compare two branches**

```terminal
$ git diff branch1..branch2
```

Copy

This will show all the file differences between the two branches.

**To compare a file from two branches**

```terminal
$ git diff branch1 branch2 ./path/to/file.txt
```

Copy

This command will show a comparison of the changes made to file file.txt across the branches branch1 and branch2.

------

### 10. Git Stash



Git Stash temporarily shelves your work, so you can switch to another branch, work on something else, and then come back to this at a later time.

It’s perfect if you need to work on something else and you’re midway through a code change, but aren’t ready to commit the code.

**Using Git Stash Save Command**

```terminal
$ git stash save “<stash-message>”
```

Copy

This will stash your changes with the message you entered. This can be helpful when you want to come back and restore your stash, especially when you have several stashes.

However, this will only stash your tracked files that you added using git add. If you want to include the untracked files as well, run

```terminal
$ git stash save -u
```

Copy



**Using Git Stash List Command**

When you want to view all the stashed code, you can view them using this command. Once you stash your code, git will assign a stash id, so you can restore a specific stashed code later.

For example:

```terminal
$ git stash list
```

Copy

This might show the following

```
stash@{0}: On master: Stashed with message1
stash@{1}: On master: Stashed with message2
```

**Using Git Stash Apply Command**

This will automatically restore and apply the topmost stash in the stack.

```terminal
$ git stash apply
```

Copy

If you want to restore a specific stash that you want to apply, using the above example, you can simply run `**git stash apply stash@{1}**`.

*Note: When you use* `**git stash apply**`*, the stashed version will be applied to your current working branch. However, it will not delete the stash from the stack.*

**Using Git Stash Pop Command**

To automatically also delete the stash from the stack, the git stash pop command is used.

If you want to do it for a specific stash in the stack, run `**git stash pop stash@{0}**`.

------

### 11. Git Status



When you’re feeling a bit lost with what’s happened in your repo (yes, it can happen) the Git Status command can tell you all the information you’ll need to know.

**Using Git Status Command**

```terminal
$ git status
```

Copy

This can give you information such as:

- Your current branch
- Whether your current branch is up to date
- If there’s anything in the branch that needs to be committed, pushed, or pulled.
- If you have any files that are either staged or not staged.
- And if you have any files that are created, modified, or deleted.

------

### 12. Git Log



While git status gave you nearly all the information you’d have needed, it wouldn’t give you the information about the commit history for the repository.

This is where the git log command comes into the picture.

**Using Git Log Command**

```terminal
$ git log
```

Copy

This displays the entire commit history. If your commit history is large, it’ll show only a portion of it and you can hit *[space]* to scroll or type *q* to quit.

- If you want to view only the last 3 commit history, you can use the following command: `**git log -n 3**`.
- To condense the commit history into a single line and view them, run `**git log --oneline**`. This is the easiest way to get a high level overview of all the commit history. It might still be a bit too much if you’ve got a lot of commits.
- If you want to view the commit history by a specific author, run `**git log --author"<author-username>"**`.

------

### 13. Git Merge



Once you’re done with development inside your feature branch and tested your code, you can merge your branch with the parent branch. This could be either a develop branch or a master branch depending on the git workflow you follow.

When running a git merge command, you first need to be on the specific branch that you want to merge with your feature branch.

Let’s see how to use the git merge command with an example.

**Using Git Merge Command**

Imagine you’re currently in your feature branch called feature1 and you’re ready to merge it to the develop branch.

**We must first switch to the develop branch using the checkout command**.

```terminal
$ git checkout develop
```

Copy

**Before merging, you must make sure that you update your local develop branch.** This is important because your teammates might’ve merged into the `develop` branch while you were working on your feature. We do this by running the pull command.

```terminal
$ git pull
```

Copy

If there are no conflicts while pulling the updates, you can finally merge your `**feature1**` branch into the `**develop**` branch.

We do this by using the git merge command followed by the branch name that we want to merge into our current branch.

```terminal
$ git merge feature1
```

Copy

*You might be interested in this detailed article about [how to create a pull request in GitHub](https://zepel.io/blog/create-pull-requests-in-github/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands)* →

*After creating a pull request, you can use this detailed article to [merge your local branch to the remote branch](https://zepel.io/blog/how-to-merge-branches-in-github/?utm_source=zepelblog&utm_medium=text&utm_campaign=13-git-commands)* →