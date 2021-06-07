## Pull Requests
Pull requests are changes in the code of an open-source project being submitted to the project developers. If the changes are approved and pass tests, they can be merged by developers into the project. If you know you have something meaningful to contribute to a project, it would be a great idea to submit a pull request. 

## How to submit a PR (Pull Request)
**1.** Go to the repository you would like to contibute to in GitHub and click the 'Fork' button in the top right corner.

![pullRequests-1](Ryan2020/pullRequests-1.png)

**2.** Clone your forked repository locally. Then, make a new branch. Checkout that branch and make the desired changes. An example might be:
```
git clone https://github.com/byuccl/MyRepo
cd MyRepo
git branch mybranch
git checkout mybranch
<do some editing on myFile>
git commit --signoff myFile -m "Commit message"
```

**3.** Whenever you commit, make sure to --signoff (or simply run `git cm` if your .gitconfig file includes the alias. See the end of this page for an [example .gitconfig file](#.gitconfig)). Also only add the necessary files to the commits. This way you are intentional and perfectly aware of what you will be contributing to the project.

**4.** Once you've committed the changes you would like to your repo in GitHub (`git push`), click on the 'Compare' button, and from there you will see the green button 'Create Pull Request'. See the pictures below, but remember not to use your master branch like I did. Better to make a branch with a specific name for your changes (see [Contribution Best Practices](#Important-Best-Practices-for-Contributions) below).

![pullRequests-2](Ryan2020/pullRequests-2.png)

![pullRequests-3](Ryan2020/pullRequests-3.png)

**5.** Give the pull request a good title and description, and submit. Finally, work with the repository members to clear up any issues and once the pull looks good, a developer will merge it.
***

## Important Best Practices for Contributions
**_First_**, make sure to make each of your changes on different branches with names related to the changes. Don't commit to your master branch. Keep the master branch of your fork open for updating to the most recent version of the main repository.

A few useful commands:
* `git branch -d [branch_name]`  (deletes the branch)
* `git branch -m \<old_name> \<new_name>`  (renames a branch)
* `git log --all --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit`  (good way to visualize all of your branches and commits, easily included in the .gitconfig file under `lg` so that you can simply run `git lg` -- See [example .gitconfig file](#.gitconfig) at bottom of this page.)
***

**_Second_**, make sure your pull request is connected to the most recent commit of the project. This is most important if there is a conflict in the pull request preventing a merge. To do this, you can actually rebase your changes on top of the most recent master.

Instructions for updating your forked repo branch with the most recent master from the main repository and rebasing branches, using symbiflow's fpga-tool-perf as an example:
1. `git remote add symbiflow https://github.com/SymbiFlow/fpga-tool-perf.git` (first time only -- adds symbiflow as a named reference from which you can pull)
2. `git fetch symbiflow` (Updates symbiflow to its current state)
3. `git checkout main` 
4. `git pull symbiflow main` (Updates your master with symbiflow's current master)
5. `git push origin main` (Gives your forked repo the updated master)
6. `git checkout <branch>`
7. `git rebase main` (if there are conflicts, resolve them, stage the previously conflicting files, and `git rebase --continue`)
8. `git push --force origin <branch>` (Forces the forked repo to accept the updated branch)

Repeat steps 6-8 for each branch that needs to be updated. 

Repeat steps 2-5 every time your master needs to be updated.
***

**_Third_**, open-source projects have coding standards. SymbiFlow projects, and many others, maintain their coding standard using yapf.

Symbiflow projects use `make format` to do this. Look at the Makefile of your project to see if there is an easy command you can run. It will look something like this in the Makefile:
```
format: ${PYTHON_SRCS}
	yapf -i $?
```
This goes through each python file and standardizes it. Thus, you will want to run this command as the last step before submitting or merging any pull request you make.
***

**_Fourth_**, you may want to condense all of your changes (commits) down to one or two commits summarizing the changes.

Instructions for squashing multiple commits into one:
1. `git checkout <branch>`
2. `git rebase -i <maing-commit-hash>`
3. Change the type of change you want to do to `s` (short for squash) for all the commits but the first (the one at the top -- keep that one as `pick`)
4. Update the commit message (to briefly summarize all changes) and then save.
5. `git push --force origin <branch>`
***

## Issues
Issues highlight problems, suggestions, or bugs that need to be implemented or fixed. If you want to discuss an bug/implementation/idea with the other contributors/developers, create an issue to get a discussion going.

One of the best features of the issue is that they can be linked to a pull request that resolves it, so that when the pull request is merged, the issue is closed.

## How to create an Issue
**1.** Go to the repository in GitHub and click on the 'Issues' tab.

**2.** Click on the green 'New Issue' button. Specify a title and write a description of the issue.

![pullRequests-4](Ryan2020/pullRequests-4.png)

**3.** To attach an issue to a pull request, you simply need to reference the issue in the description of the pull request with one of the key words below followed by "#\<issue-number>"
```
close     closes    closed
fix       fixes     fixed
resolve   resolves  resolved
```
```
fixes #221
```
***

## .gitconfig
If you don't have an alias section in your `.gitconfig` file, add it. An example is shown below. Running `git cm` for signed-off commits and `git lg` to keep track of branches has been especially useful for me.

```
# This is Git's per-user configuration file.
[user]
        name = Ryan Johnson
        email = ryancj14@gmail.com
[alias]
        co = checkout
        ci = commit
        cm = commit -s
        pl = pull -S
        br = branch
        st = status
        unstage = reset HEAD --\n
        last = log -1 HEAD
        lg = log --all --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
        fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```

----------------------------------
Initially created by Ryan Johnson, August 2020.