# GIT-Essentials / GIT for everybody
  This repository was meant as a test one for my GIT Course. It's purpose is to experiment and save my notes on the matter. It dose not contain any data except text files I use to better understand how to manipulate a repository.
    
## Instal and configure GIT:
  - instal GIT for Windows 
  - Configure GIT on my pc: (so he knows where we are)
  1. configure email and name to easy pair 
  2. name:   git config --global user.name "AndreeaM"
    
       email:  git config --global user.email "andreeaMiron@protonmail.com"
  3. use cat ~/.gitconfig to make sure you have a account
        mkdir *name* - makes a folder

## Set up SSH:
  *SSH is a signature key to add to github so the actions are validated
  1. ssh-keygen -o = to generate the key
  2. cat *location it said it put the .pub in, the public key* and copy the key 
  3.   in github in settings add ssh key and name it
  Now this validates our stuff in our name 


## Create a new repository:
    git init 
    git add README.md 
    git commit -m "first commit"   
    git branch -M main  = optional 
    git remote add origin git@github.com:DarkTamara/git-Essentials.git  = links to the github 
    git remote -v = see what i use and github username and repository
    git push -u origin main 

 
## Making a commit and pushing it:
  pushing = get code from my computer to github
  steps:  1. unstaged work
          2. staged work
          3. commit work
          4. push work

1. unstaged = not telling git to add this file to a package, needs to be added
2. staged = when it's commited this is going to be in there too 
    git add first-push.txt 
3. commit = creating a package with all the staged files with a autor and a message, this is not on github yet, it's just packed
    git commit -m "first official push"
4. push = deliver the package to github/origin

        git push origin master
        git is the comand, 
        push is the action we do, 
        origin is github in this case, 
        master is the primary brench

# Comands and situational comands:
    git status = shows what files are commited, changed, renamed, all status of files. If files are modified they show up in here 

## Add
Can add all files with add . 

## Deleting files
    rm fileName = deletes the file
In case i mistakely deleted and i don't wanna commit it:

    git reset HEAD first-push.txt   = this unstages this file if stated(ADD), this delete will not be commited
In case i deleted it from my pc, if i have a version of that file submitted:

    git checkout -- first-push.txt  = this reverts the deletion, reverts changes in working directory

## Origin 
This is where your remote code lives 

    git remote -v = to see where the remote origin is 
You can have multiple repositories to push, multiple origins 

## Branching 
A copy of the original work, they are meant to hold changes and merge into master later 

    git checkout -b new-branch  = creates new branch, local new branch till push 
    git branch = to see the branches 
    git checkout master = moves to master branch 
    git checkout new-branch = move to new-branch
    git push origin new-branch = after commit, the push is supposed to be on the new branch 
_If you select other branches the push dose not take place and it shows all is up to date._

## Merge
Take one branch and applying it to another branch. Make sure the merging branch is up to date :

    git pull origin master = look for new changes in github and apply on my code in pc
    git merge new-branch = merge new branch in selected branch, master in my case 
    #this merges the tho, but it's staged only 
    git push origin master = update gitHub, adds the files in new-branch to master, dose not delete new-branch 

## History 
Shows all changes in a branch and the person.

    git log = shows all commits 
_to get out hit q_

## Pull 
This pulls form origin the branch I select.

    type nul >> "file.txt" = create new file
In case you modify stuff and the origin is also modified :
  it will reject because the origin has work you don't have solution:
  
    1. git pull origin master 
This will update the commits i don.t ahve in my pc, thena dd my work, then add the merge commit that GitHub dose so i can know where the merge happened 
    
    2. git push origin master 
This now can go on because i have all the work on gitHub merged with mine and ready to push. This dose not work when the same file is modified at the same time, similar way to go but not the same

In case you don't want all that is in github but wanted to see it, not merge to local:

        git fetch origin master = will download the code but will not apply the code 
        git log --oneline --graph --decorate --all = shows me all the tree, if i have commits fetched i can see them here 
Head is where i am on local 

    git pull origin master = to update, not download, but update to what i fetched 
_pull = fetch + merge_

## Time Travel
In github u can click <> and will show that commit stage.
In cmd, copy hash and : <br>
This sends us in that state, and i can experiment, we are in a detached head state. Helps to look at files and see what that state was like. Make sure you are on the branch you wanna see.

    git checkout *hash here*
Reverse and go to latest: 

        git checkout *branchname*

Create a new branch in a past time:
This creates a new branch that has the files of that moment in time i created it from. Is a way to attache the head and work on a past moment and try new branches. Can be merged in master and can show up in latest version. 

    git checkout *hash*
    git checkout -b *new branch name*
    do all the changes you wnat to do
    git commit
    git push origin *new branch name here*

## README.md files 
They are written in marksdown language 

        # big title
        ## smaller title
        
# Advanced comands:

## Viewing file differences
Shows the differences between last commit and now, added or removed: 

    git diff <fileName> 
_Good workflow to use status and then diff before a commit_

## How to ignore files
For files that you don't want to add to your repository.
    Create a .gitignore and store all files you want to ignore 
_Dosen't even appear in status._

## Custon Git alias
Custom created comands, like macros.
_You can open files in VS code terminal by using 
    
    code <filename>_ 
Course way:
1. Open/create .gitconfig 
2. 
    
        [alias]
        lg = log --topo-order --all --graph --date=local --pretty=format:'%C(green)%h%C(reset) %&gt;&lt;(55,trunc)%s%C(red)%d%C(reset) %C(blue)[%an]%C(reset) %C(yellow)%ad%C(reset)%n'
This worked for me tho:
1. git config --global alias.lg 'log --oneline --graph --decorate --all'
<br>_Created a easy way to see the whole commit tree and where i am._

## Fixing Git commit messages
Make sure it is not yet submitted to GitHub. This works for the last commit you made.

    git commit --amend 
_Edit the typo here in the file that opens_

## Forking a repository
Means taking all the code and copying it to your profile. Copying a project to another account.
Useful for copying and making changes to a project you have no acces to. Usually you should look at the readme.md and the licencing. 
To fork there's a button on GitHub.

## Git Issue 
Not something bad bad. More like a forum, you can just post suggestions or point out misspleed things, or identify real issues with the code.
It can be assigned, it can be labeled and more. They can be closed but they are still searchable. 

## Pull Request
When a modification is created, ex. a new branch, when the change is pushed in gethub it will show the option to create a pull request. This way you can set it up for review before it merges. It can be assigned and use labels. 
The commit can be reviewed. After the merge it can be deleted if not needed anymore, but it only deletes it on GitHub. <br>
To delete localy:

    git branch -d <filename>

## Undo a commit 
Ex: doing a commmit and going back in a previous commit, undoing it. Two ways:

- soft reset = this uncommits but dose not delete the file  
    
        git reset --soft <hash name> or <origin/master>
- hard reset = this deletes until that commit
    
        git reset --hard <hash name>

## Force push 
If you accidentally pushed a commit you didn't want pushed. Be evry carefull iwth this force push.
The ideea is that you push from a past commit to origin. It will delete all files commited after that point. It can not be undone.

    git reset --hard <hash name> 
This deletes the origin/master point. The commit can still be seen in the tree and can be reverted. <br>
When you try to push this, it will give a error because we are in a past state. You can use pull and then pull or a force pusha nd overwrite this all.

    git push origin master --force 
Files dissapear and the commit on github is gone. 

## Rebasing 
Makes easier to read the tree by rewriting it. Rebase a branch onto master:

    git rebase <name of the branch>
Rebase is like merge only it shows up as a continuation of amster branch, not a separate branch and a merge, keeps the tree more clean. Makes it harder to see where the merge was made. 
Merge is more ok for big projects.

## Resolving merge and rebase conflicts
A conflict happens when there's two change in the same file, basically in the same place. They can be merge conflicts, and rebase conflict.

### Merge conflict: a file is commited on github and on local
    git pull origin master 
Automatic merge failed; fix conflicts and then commit the result.

    git diff <file.name>
This shows the differences between the two versions. 
Open the file and solve the conflicts in the edditor, it will tell you to choose the version you want to keep. 

    git add .
    git commit
    git push origin master 

### Rebase conflict:
In case you work in the last state and make a change on a file, but you also have that file on a branch in another state.
On master do:

    git rebase <branch name>
Will show:

    "git add/rm <conflicted_files>", then run "git rebase --continue".
    CONFLICT (add/add): Merge conflict in rebase-conflict.txt
! In case you are not sure about this, use :
    
    git rebase --abort 
Edit the file and resolve the conflicts. Can be modified in any way, the local, the master origin files, or even a hybrid made by me. To cheeck if it worked after modification, do a 
    
    git dif <filename> to see if there are only + and -.
    git add.
    git status
  (all conflicts fixed: run "git rebase --continue")
No commit needed.

    git rebase --continue
    git log --oneline

## Stash Code 
Save some code behind the scenes and acces later. Useful when you switch branches to work on something elese and don't wanna lose work. Not commmited and not lost.
The file can be grabbed later and worked on later <br>
_You can create a new barnch with git branch <branchName> but you won't be checkedout on that branch. git checkout <newBranchName> creates a new branch adn also checes you in it._<br>
If you do a git checout master and the work on the other branch is not commited, the work comes to the master branch. Brings the work in the other branch.
Use this instead:

    git stash 
To see the stashed code:

    git stash list 
_This list is global, not on a branch_
_In the tree log this work in progress appears. 8e388b0 (refs/stash) WIP on stash-example: c0b90c2 Rebase conflict example_ <br>
To apply the list :

    git stash apply
The apply won't delete the file from the stash, you must do this in order to drop the last file added to the stash:

    git stash drop

## Adding Taggs to commits
A way of marking a milestone. You can easy fix them and then checkout to them.
Go to where you wnat the tag to be and add the line:

    git tag <tag text here>
It will show up in log.
Tag list, alphabetical: 

    git tag 
Pushing a tag:

    git push origin <tag text here>
Multiple tags push:

    git push origin --tags 
Removing a tag:

    git tag -d typo-name 
    git push origin --delete tag-name 

# Notes
Just some notes I found interesting from the Course on building a website

## Repo name
Repository name should be: 

    username.github.io 
## Themes 
startbootsrap.com 

## Ignorable files
Do not commit all files in a project, when using many files and packages. 
Filetypes to ignore: 
- for python: 
    - .pyc
    - pycache
