# GIT-CHEAT-SHEET
<br>

### SETUP
> Configuring user information used across all local repositories
```bash
git config --global user.name “[firstname lastname]”
```
###### set a name that is identifiable for credit when review version history
#
```bash
git config --global user.email “[valid-email]”
```
###### set an email address that will be associated with each history marker
#
```bash
git config --global color.ui auto
```
###### set automatic command line coloring for Git for easy reviewing
#
#
### SETUP & INIT
> Configuring user information, initializing and cloning repositories
```bash
git init
```
###### adding remote repository to your local
#
```bash
git remote add <shorthand-name> <HTTP_url>
git remote add origin https://github.com/EbenGitHub/FantasticProject.git
```
###### adding source repository to your local
#
```bash
git remote add <shorthand-name> <HTTP_url>
git remote add upstream https://github.com/EbenGitHub/FantasticProject.git
```
> If we are working on in a project that is someone else, and we fork git to our github repository, and clone it to our local computer. 
> Our local clone will refer to our forked repository as `origin`. `git remote add origin https://github.com/EbenGitHub/FantasticProject.git`
> We can also connect our local clone to the original source repository and it will be refered as `upstream`. `git remote add upstream https://github.com/EbenGitHub/FantasticProject.git`
###### to change the remote repository name
#
```bash
git remote rename <old_name> <new_name>
git remote rename origin mine
git remote rename upstream source
```
###### to check the remote repository and path
#
```bash
git remote 
```
###### to check the remote repository and full path
#
```bash
git remote -v
```
###### initialize an existing directory as a Git repository
#
```bash
git clone [url]
```
###### retrieve an entire repository from a hosted location via URL
#
#
### STAGE & SNAPSHOT
> Working with snapshots and the Git staging area
```bash
git status
```
###### show modified files in working directory, staged for your next commit
#
```bash
git add [file]
```
###### add a file as it looks now to your next commit (stage)
#
_or_
```bash
git add --chmod=+x [file]
```
###### add a file as it looks now to your next commit (stage) with execution permission
#
```bash
git reset [file]
```
###### unstage a file while retaining the changes in working directory
#
```bash
git diff
```
###### diff of what is changed but not staged
#
```bash
git diff --staged
```
###### diff of what is staged but not yet commited
#
```bash
git commit -m “[descriptive message]”
```
###### commit your staged content as a new commit snapshot
#
#
### APPLY EXECUTABLE FILE
> Add exutable permission to the git file
```bash
git update-index --chmod=+x [file]
```
#
#
### BRANCH & MERGE
> Isolating work in branches, changing context, and integrating changes
```bash
git branch
```
###### list your branches. a * will appear next to the currently active branch
#
```bash
git branch [branch-name]
```
###### create a new branch at the current commit
#
```bash
git checkout
```
###### switch to another branch and check it out into your working directory
#
```bash
git merge [branch]
```
###### merge the specified branch’s history into the current one
#
```bash
git log
```
###### show all commits in the current branch’s history
#
#
### INSPECT & COMPARE
> Examining logs, diffs and object information
```bash 
git log
```
###### show the commit history for the currently active branch
#
```bash
git log branchB..branchA
```
###### show the commits on branchA that are not on branchB
#
```bash
git log --follow [file]
```
###### get short summary of log informations
#
```bash
git log --oneline --graph --decorate --all
```
> MASTER -- our local branch head
#
> ORIGIN/MASTER  --  remote tracker
###### get details of log informations
#
```bash
git log --stat
```
###### to see how many commits each contributor has added to the repository
#
```bash
git shortlog
```
> `git shortlog` displays an alphabetical list of names and the commit messages that go along with them. 
> If we just want to see just the number of commits that each developer has made, we can add a couple of flags: 
> * `-s` to show just the number of commits (rather than each commit's message) and 
> * `-n` to sort them numerically (rather than alphabetically by author name).
```bash
git shortlog -s -n
```
> Another way that we can display all of the commits by an author is to use the regular `git log` command but include the `--author` flag to filter the commits to the provided author.
```bash
git log --author=<author_name>
git log --author=Surma
```
> Eg. if there are two Surma authors with different last name, `git log --author=Surma` will show commits of both authors
> If we want to be more specific, we can do:
```bash
git log --author="<first_name> <last_name>"
git log --author="Surma Lewis"
```
###### get details information about a commit
#
```bash
git show <COMMIT_ID>
git show 5966b66
```
###### filtering commits by information in the current message or description area.
#
```bash
git log --grep=bug
git log --grep bug
git log --grep="unit tests"
```
###### show the commits that changed file, even across renames
#
```bash
git diff branchB...branchA
```
###### show the diff of what is in branchA that is not in branchB
#
```bash
git show [SHA]
```
###### show any object in Git in human-readable format
#
#
### TRACKING PATH CHANGES
> Versioning file removes and path changes
```bash 
git rm [file]
```
###### delete the file from project and stage the removal for commit
#
```bash
git mv [existing-path] [new-path]
```
###### change an existing file path and stage the move
#
```bash
git log --stat -M
```
###### show all commit logs with indication of any paths that moved
#
#
### IGNORING PATTERNS
> Preventing unintentional staging or commiting of files
```bash
logs/
*.notes
pattern*/
```
###### Save a file with desired paterns as .gitignore with either direct string
matches or wildcard globs.
#
```bash
git config --global core.excludesfile [file]
```
###### system wide ignore patern for all local repositories
#
#
### SHARE & UPDATE
> Retrieving updates from another repository and updating local repos
```bash
git remote add [alias] [url]
```
###### add a git URL as an alias
#
```bash
git fetch [alias]
```
###### fetch down all the branches from that Git remote
#
```bash
git merge [alias]/[branch]
```
###### merge a remote branch into your current branch to bring it up to date
#
```bash
git push [alias] [branch]
git push <remote-shortname> <branch>
git push origin master
```
###### Transmit local branch commits to the remote repository branch
#
```bash
git pull
git pull <remote-shortname> <branch>
git pull origin master
```
> If you don't want to automatically merge the local branch with the tracking branch then you wouldn't use `git pull` you would use a different command called `git fetch`. 
> You might want to do this if there are commits on the repository that you don't have but there are also commits on the local repository that the remote one doesn't have either.
> Git fetch is used to retrieve commits from a remote repository's branch but it does not automatically merge the local branch with the remote tracking branch after those commits have been received.
###### fetch commits from remote to local without merging to our branch
#
```bash
git fetch
git fetch <remote-shortname> <branch>
git fetch origin master
```
###### to merge changes of commits fetched to our branch
#
```bash
git merge <remote-shortname>/<branch>
git merge origin/master
```
###### push merged changes to our remote repository
#
```bash
git push <remote-shortname> <branch>
git push origin master
```
###### fetch and merge any commits from the tracking remote branch
#
#
### Forking a Repository
> Fork a repository that means you duplicate it
> Typically you fork a repository that belongs to someone else. 
> So you make an identical copy of their repository and that duplicate copy now belongs to you.
> This concept of `forking` is also different from `cloning`. 
> When you clone a repository, you get an identical copy of the repository. 
> But cloning happens on your local machine and you clone a remote repository. 
> When you fork a repository, a new duplicate copy of the remote repository is created. 
> This new copy is also a remote repository, but it now belongs to you.
###### to connect to our forked repository
#
```bash
git remote add origin <url_forked_repo>
```
###### to pull changes from source repository not forked repository
#
```bash
git fetch origin master
```
###### to connect to the original source repository
#
```bash
git remote add upstream <url_source_repo>
```
###### to pull changes from source repository not forked repository
#
```bash
git fetch upstream master
```
###### to merge changes from source repository and push to our forked repository
#
```bash
git checkout master
git merge upstream/master
git push origin master
```
> `upstream/master` - keep track of where the source repository's master branch is.
> `origin/master` - keep track of where the forked (our) repository's master branch is.
###### to fetch changes and merge them into the master branch
#
```bash
git pull origin master
git pull upstream master
```
#
#
### REWRITE HISTORY
> Rewriting branches, updating commits and clearing history
```bash
git rebase [branch]
```
###### combine the last three commits into one
#
```bash
git rebase -i HEAD~3
```
> `HEAD~2`, `HEAD~1`, and `HEAD` will merge to one.
> `HEAD` indicates your current location (it could point to several things, but typically it'll either point to a branch name or directly to a commit's SHA). 
> `~3` part means "three before", so `HEAD~3` will be the commit that's three before the one you're currently on
> `HEAD~3` will be referenced as a base, but it won't be merged.
> `-i` means interactively
> We're using this relative reference to a commit in the `git rebase` command.
#
> don't forget to forcefully push changes to githun. otherwise github won't accept pushes to prevent commit deletion. `git push -f`
> I recommend that you create a `backup` branch before rebasing, so that it's easy to return to your previous state. If you're happy with the rebase, then you can just delete the backup branch!
###### apply any commits of current branch ahead of specified one
#
```bash
git reset --hard [commit]
```
###### clear staging area, rewrite working tree from specified commit
#
#
### TEMPORARY COMMITS
> Temporarily store modified, tracked files in order to change branches
```bash
git stash
```
###### Save modified and staged changes
#
```bash
git stash list
```
###### list stack-order of stashed file changes
#
```bash
git stash pop
```
###### write working from top of stash stack
#
```bash
git stash drop
```
###### discard the changes from top of stash stack
#
#
__GitHub__ Education
#
_EbenGitHub_ 



