### For This Wiki

* After making any changes you are sure you want to keep:
```
git add -A  # or git add <file> to update a single file
git commit -m "message about updated items"
git push
```

Use `git status` to make sure you have the right files ready to be commited

### Other Important Git Functionalities
Before pushing to a public repository, pull to merge changes made to the repository with yours. Then you can resolve conflicts and push yours. Before pulling, remember to commit your changes so they don't get overwritten by the pull. Just run:
```
git cm
git pull
```
### List of Git Commands
 
* git init - initializes an empty git repository
* git commit - makes a new save of changes made (files must be staged before they can be committed)
    * -m “\<message>” – gives the commit message
    * -a – commits snapshot of all the changes at once
* git status - lists the modified files which are ready to be added to the repository
* git add \<file> - adds a file (also works with a directory) to the index
* git add -A - adds all files in the directory to the index (that haven’t been added)
* git pull origin master  - fetches changes from a remote repository to a local one
* git remote add origin \<link of your central repository> - sets the central repository as the origin
* git push origin master - pushes your local changes to the remote repository
* git branch \<name>  	- makes a new branch or moves it somewhere else
* git checkout \<branch>  - changes the head to a different branch
    * ~n - points to the *n*th ancestor
    * ^ - points to the parent
* git checkout -b [branch_name] - create a new branch and checkout to new branch
* git merge \<branch_name> - merges the branch specified with the current branch
* git rebase \<branch_name> - makes the branch appear as a linear sequence
* git diff - shows file differences which are not yet staged
* git reset [file] - unstages the file but preserves its contents
* git rm [file] - deletes the file and stages the deletion
* git show [commit] - shows the metadata and content changes of the specified commit
* git branch -d [branch_name] - deletes the branch
* git branch -m \<old_name> \<new_name> - renames a branch
***
What I did to add a certain commit from @acomodi at his direction:
```
git remote add antmicro https://github.com/antmicro/fpga-tool-perf.git
git fetch antmicro
git cherry-pick 5318926a9e87d7e7498b5d9b8435736277fcdd32
```
***
If an error comes up that the project has unrelated histories, then you can use this, but make sure you pulling from the right spot. You may have to resolve any differences manually.
```
git pull --allow-unrelated-histories
```
***
## .gitconfig file
```
# This is Git's per-user configuration file.
[user]
	name = Ryan Johnson
	email = ryancj14@gmail.com
[filter "lfs"]
	process = git-lfs filter-process
	required = true
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
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
***

Instructions for updating your forked repo branch with the most recent master from the main.
So, what I usually do is the following:
1. (first time only) git remote add symbiflow https://github.com/SymbiFlow/fpga-tool-perf.git
2. git fetch symbiflow
3. git checkout master
4. git pull symbiflow master
5. git push origin master (this way your master is up to date with the upstream master)
6. git checkout <branch>
7. git rebase master (+ solve confilcts if there are some)
8. git push --force origin <branch>

***
Can you also squash the commits of your branches and push force?
This can be done by doing:
1. git checkout <branch>
1. git rebase -i <master-commit-hash>
2. Change the type of change you want to do to s for all the commits but the first
3. Update the commit message
4. git push --force origin <branch>

----------------------------------
Initially created by Ryan Johnson, June 2020.