# git

# Create file named README.md that will contain the documentation 
`touch README.md`

# Create a directory named work that will contain all works
`mkdir work`

# Section: Setting Up Git
## This is to config the uesrname for git
`git config --global user.name "Myusername"`
## This is to config the email for git
`git config --global user.email "myGmail@gamil.com"`

# Section: Git commits to commit
## Create a file named hello.sh
`touch .\work\hello\hello.sh`
## Print inside the prevoius file a statement
`echo "echo "Hello, World"" > hello.sh`
## Initialized a repository inside hello directory 
`git init ./work/hello/`
## get the stauts for the git repository 
`git status ./work/hello/`
* The output indicate there is a change and not added for the repository

output:
```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        work/hello/

nothing added to commit but untracked files present (use "git add" to track)
```

## Stage the changed file and commit the changes
`cd ./work/hello`\
`git add hello.sh`\
`git commit -m "This is the first commit"`

## Change the file content then add it to the repository
`git add hello.sh`
`git commit -m "line 3 and 4"`

# Section: History

## Show the history of the workind directory
`git log`
\
output:
```
commit dbe753fc4235ed3cb173e4a736ad1e2d1ff10e91 (HEAD -> master)
Author: Sayed4Work <hasonx2005@gamil.com>
Date:   Wed Aug 7 00:18:21 2024 +0300

    line 4 and 5

commit 5b3402814bb22982b0b64da81b2b32c6db28dd23
Author: Sayed4Work <hasonx2005@gamil.com>
Date:   Wed Aug 7 00:09:56 2024 +0300

    line 3 and 4

commit a5eb82054c6595dd6f58cdfa1447c941448bc630
Author: Sayed4Work <hasonx2005@gamil.com>
Date:   Wed Aug 7 00:02:12 2024 +0300

    This is the first commit
```

## Show One Line History
`git log --oneline`
output
```
dbe753f (HEAD -> master) line 4 and 5
5b34028 line 3 and 4
a5eb820 This is the first commit
```

## Show history with customize output
`git log -n 2`
this will show just two entries\
output:
```
commit dbe753fc4235ed3cb173e4a736ad1e2d1ff10e91 (HEAD -> master)
Author: Sayed4Work <hasonx2005@gamil.com>
Date:   Wed Aug 7 00:18:21 2024 +0300

    line 4 and 5

commit 5b3402814bb22982b0b64da81b2b32c6db28dd23
Author: Sayed4Work <hasonx2005@gamil.com>
Date:   Wed Aug 7 00:09:56 2024 +0300

    line 3 and 4
```
` git log --since="5.minutes.ago"` This will show the the logs in last 5 min

## Customize the git log format 
`git log --pretty=format:'* %h %as | %s%d [%cn]'`

output:
```
* dbe753f 2024-08-07 | line 4 and 5 (HEAD -> master) [Sayed4Work]
* 5b34028 2024-08-07 | line 3 and 4 [Sayed4Work]
* a5eb820 2024-08-07 | This is the first commit [Sayed4Work]
```

## Go back to the first commit 
`git checkout HEAD~2`\
Run `bash hello.sh `\
output:
```
Hello,
```

## Go back to the second commit
`git checkout master` go to the master commit so you can say all the logs again\
`git checkout HEAD~1` go to the second commit or you can just use the hash for the commmit\
`bash hello.sh ` Will not print anythings beacasue there is just comments

## Go back to the latest version 
`git checkout master`go to the latest version of commits\
output:
```
Hello, World
```

# Section: TAG me

## Referencing Current Version
`git tag v1` tag current repo as v1\
output:
```
commit dbe753fc4235ed3cb173e4a736ad1e2d1ff10e91 (HEAD -> master, tag: v1)
```

## Tagging previous version
`git tag v1-beta HEAD~1`tag previous commit\
output:
```
5b34028 (tag: v1-beta) line 3 and 4
```

## Navigating Tagged Versions:
`git checkout v1-beta` to move for the previous commit\
`git checkout v1` to move for the master commit

## Listing Tags:
`git tag` this command will list all the tags\
output:
```
v1
v1-beta
```
# Section: Changed your mind?

## Reverting Changes:
`git checkout hello.sh` This is will undo the change in the file

## Staging and Cleaning:
`git add .`\
`git status` \
output:
```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
       This line Green: modified:   hello.sh
 ```
`git restore --staged hello.sh` It will restore the file after you add it\
\
Now check the status the green line from the previous check now is red

`git checkout hello.sh` To discard the changes you made to the file\

`git status`\
output:
```
On branch master
nothing to commit, working tree clean
```

## Committing and Reverting:
Change the file content then\
`git add .`\
`git commit -m "Bad"`

### Tagging and Removing Commits:
`git tag oops`\
then you can use this command to remove the add and the commit you have done be mistake:
`git reset --hard HEAD~1`

### Displaying Logs with Deleted Commits:
`git reflog` This will show all the deleted commits\
`git show oops` This will show the all the info about a one commit