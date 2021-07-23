# GIT-Essentials
    This repository was meant as a test one for my GIT Course. It's purpose is to experiment and save my notes on the matter. It dose not contain any data except text files I use to better understand how to manipulate a repository.
    
## Instal and configure GIT:
    - instal GIT for Windows 
    - Configure GIT on my pc: (so he knows where we are)
        1. configure email and name to easy pair 
        name:   git config --global user.name "AndreeaM"
        email:  git config --global user.email "andreeaMiron@protonmail.com"
        2. use cat ~/.gitconfig to make sure you have a account
        mkdir *name* - makes a folder

## Set up SSH:
    *SSH is a signature key to add to github so the actions are validated
        1. ssh-keygen -o = to generate the key
        2. cat *location it said it put the .pub in, the public key* and copy the key 
        3.   in github in settings add ssh key and name it
    Now this validates our stuff in our name 


## Create a new repository:
    *you can switch to SSH 
        echo "# git-Essentials" >> README.md 
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

    1 unstaged = not telling git to add this file to a package, needs to be added
    2 staged = when it's commited this is going to be in there too 
        git add first-push.txt 
    3 commit = creating a package with all the staged files with a autor and a message, this is not on github yet, it's just packed
        git commit -m "first official push"
    4. push = deliver the package to github/origin
        git push origin master
                git is the comand, 
                push is the action we do, 
                origin is github in this case, 
                master is the primary brench

# Comands and situational comands:
    git status = shows what files are commited, changed, renamed, all status of files 
    if files are modified they show up in here 

## ADD
    # can add all files with add . 

## DELEETED FILES BACK
    rm fileName = deletes the file
        #in case i mistakely deleted and i don't wanna commit it:
            git reset HEAD first-push.txt   = this unstages this file if stated(ADD), this delete will not be commited
        #in case i deleted it from my pc, if i have a version of that file submitted:
            git checkout -- first-push.txt  = this reverts the deletion, reverts changes in working directory

## ORIGIN = where ur remote code lives 
    git remote -v = to see where the remote origin is 
    #you can have multiple repositories to push, multiple origins 

## BRANCHING = a copy of the original work, they are meant to hold changes and merge into master later 
    git checkout -b new-branch  = creates new branch, local new branch till push 
    git branch = to see the branches 
    git checkout master = moves to master branch 
    git checkout new-branch = move to new-branch

    git push origin new-branch = after commit, the push is supposed to be on the new branch, 
    #if you select other branches the push dose not take place adn it shows all is up to date 

## MERGE = take one branch and applying it to another branch 
    #make sure the merging branch is up to date :
        git pull origin master = look for new changes in github and apply on my code in pc
    
    git merge new-branch = merge new branch in selected branch, master in my case 
    #this merges the tho, but it's staged only 
    git push origin master = update gitHub, adds the files in new-branch to master, dose not delete new-branch 

## HISTORY = shows all changes in a branch and the person
    git log = shows all commits 
    #to get out hit q 

## PULL = pulls form origin the branch i select
    #type nul >> "file.txt" = create new file
    #in case you modify stuff and the origin is also modified :
        it will reject because the origin has work you don.t have
        solution:
        1.  git pull origin master 
            #this will update the commits i don.t ahve in my pc, thena dd my work, then add the merge commit that
             GitHub dose so i can know where the merge happened 
        2.  git push origin master 
            #this now can go on because i have all the work on gitHub merged with mine and ready to push
        
        #this dose not work when the same file is modified at the same time, similar way to go but not the same


    #in case you don't want all that is in github but wanted to see it, not merge to local:
        git fetch origin master = will download the code but will not apply the code 
        git log --oneline --graph --decorate --all = shows me all the tree, if i have commits fetched i can see them here 
        #head is where i am on local 
            git pull origin master to update, not download, but update to what i fetched 
            pull = fetch + merge 

## TIME TRAVEL = in github u can click <> and will show that commit stage 
    = in cmd, copy hash and : git checkout *hash here*
    #this sends us in that state, and i can experiment, we are in a detached head state. 
    this helps to look at files and see what that state was like  
     #make sure you are on the branch you wanna see 

    Reverse and go to latest: 
        git checkout *branchname*

    Create a new branch in a past time:
        1. git checkout *hash*
        2. git checkout -b *new branch name*
        3. do all the changes you wnat to do
        4. git commit
        5. git push origin *new branch name here*
    #this creates a new branch that has the files of that moment in time i created it from
    #this is a way to attache the head and work on a past moment and try new branches 
    #can be merged in master and can show up in latest version 

## README.md files = written in marksdown language 
        # big title
        ## smaller title
        
