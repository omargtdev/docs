# Git Useful Commands

### init
Initializes an repository.
- `git init --bare` - For simulate a "server" repository or only save information about some git repo.
- `git init` - Init a repo.

### stage
Git stage area is for the files to be tracked by git.
- `git add <file(s)>` - Add files to the stage to follow up.

### restore
Restore files from the staging area.
- `git restore <file(s)>` - Restore files when are not staged, if they were commited before.
- `git restore --staged <files>` - Restore files when are staged, put them outside stage (untracked).

### commit
Make "photos" in the "history line"
- `git commit` - Open terminal configurated to commit the staged files.
- `git commit -m <message>` Short way to do a commit with a message.

### diff
Compare file changes.
- `git diff` - Compare actual changes with last commit.
- `git diff <startHash>..<endHash>` - Compare changes between the start and end commit provided.

### checkout
Check and/or restore files and jump between branches and commits.
- `git checkout -- <files>` - Restore files when are not staged (like `git restore`).
- `git checkout (<branchName> | <commitHash>)` - Change where HEAD points, i.e. switch branches, go to speficic commit, etc.
- `git checkout -b <branchName>` - Create a branch and switch to it.

### log
Show history of commits that were made.
- `git log` - Show commits of current branch.
- `git log --oneline` - Show commits in short way.
- `git log --graph` - Show commits in graphical way.
- `git log -p` - Show commits showing the file changes (diff).

### revert
Revert your catastrophes.
- `git revert <commitHash>` - Revert the changes of a commit creating a new commit.

### reset
Move in the timeline, where:
> **soft** keeps the changes in the stage.
> **mixed** does not keep the changes in stage.
> **hard** does not keep anything.
- `git reset [--soft | --mixed | --hard] <commitHash>`

### remote
Set remote locations to push/pull/fetch changes.
- `git remote` - Show the names of remote repos that exist in this repo.
- `git remote -v` - Show the name with url (direction) of remote repos.
- `git remote add <name> <url>` - Add a remote repo to point to.
- `git remote rename <oldName> <newName>` - Rename a remote repo.

### branch
Manage your code with commits in multiple branches.
- `git branch` - Show all branches of current repo.
- `git branch -d <name>` - Delete a branch.

### merge/rebase
Merge commits from target branch to current branch.
- `git merge <branchName>` - Merge all commits of the specified branch to actual branch creating a commit of merge. Specified branch does not change.
- `git rebase <branchName>` - Merge all commits of the specified branch to actual branch taking the last commit of the current branch as the last.

### push
Send your changes to the origin/tag specified.
- `git push <branchName> (<originName> | <tagName>)` - Push all changes of the branch specified to the "server".

### pull
Bring changes from the remote target to current repo.
- `git pull <branchName> <originName>` - Get the last changes of the branch specified from the origin repo.

### stash
An "vault" to save your changes since last commit, like you didn't do anything.
- `git stash` - Move all changes to temp stash to save them.
- `git stash list` - Show all temp changes.
- `git stash pop` - Get the last changes in stash.

### tag
Set like "flags" to a specific commit.
- `git tag [-l]` - List all tags.
- `git tag -a <name>` - Adding a tag with interactive editor.
- `git tag -a <name> -m  <message>` - Adding a tag with specified message.
- `git tag -d <name>` - Delete a tag.
