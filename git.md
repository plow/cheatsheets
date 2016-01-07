### Commiting

Add forgotten files to the last commit not yet pushed:<br/>
`git commit --amend`

Delete the most recent commit, keeping the work you've done:<br/>
`git reset --soft HEAD~1`

Delete the most recent commit, destroying the work you've done:<br/>
`git reset --hard HEAD~1`

Unstage a file while retaining the changes in working directory:<br/>
`git reset [file]`

Delete untracked files from workspace:<br/>
`git clean -f`      (`git clean -df` to delete directories as well)

Overwrite local file with latest version from master:<br/>
`git checkout filename`     // if not staged and not committed

`git reset HEAD filename` <br/>
`git checkout filename`     // if staged but not yet committed

Delete all unpushed commits and reset workspace to origin/master state:<br/>
`git fetch origin` <br/>
`git reset --hard origin/master`


### Diffs

Diff of what is changed but not staged/committed:<br/>
`git diff`

Diff of what is staged but not yet committed:<br/>
`git diff --staged`

Diff of what is changed compared to HEAD (staged or not staged) <br/>
`git diff HEAD`

Show the diff of what is in branchA that is not in branchB <br/>
`git diff branchB...branchA`


### Logs

History of my commits: <br/>
`git log --format=%ci%n%Cgreen%s%n --author=sfankhauser` // author summary for ptime <br/>
`git log --format="%Cblue %h %Cgreen%ai %Creset%s"`      // oneline with date <br/>
`git log --decorate --all --oneline --graph`             // show graph and tags, heads, etc.q


### Tagging

`git tag -a v0.005 9fceb02 -m "Sprint 5 Release"`

`git tag -a v0.XXX -m "Sprint X Release"` <br/>
`git push --tags origin master`

`git push --delete origin tagname`


### Branching / Merging

Locally create branch 'testing': </br>
`git branch testing`

Locally switch to branch 'testing' (sets HEAD to 'testing' branch. affects your workspace data if testing branch is divergent with current branch): <br/>
`git checkout testing`

Merging branch 'hotfix' into branch 'master' (it's assumed you're on the master branch - git checkout master):<br/>
`git merge hotfix`

Delete branch 'hotfix': <br/>
`git branch -d hotfix`

List all branches: <br/>
`git branch -v`

Branch from a previous commit: <br/>
`git branch branchname <sha1-of-commit>`

___

Local branch:   `master` (or `foo`) <br/>
Local HEAD:     `HEAD` <br/>
Remote branch: 	`origin/master` (or `origin/foo`) <br/>
Remote HEAD:    `origin/HEAD` <br/>
