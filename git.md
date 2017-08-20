# how to use git
---

## download

[git download page](https://git-scm.com/downloads)

---
## configure

- to see whether git is working

        $ git --version

- all work should be done and signed up by *someone*, so we should configure a uername and e-mail

        $ git config --global user.name "username"

        $ git config --global user.email "email_address"

---
## initialization and a first commit

go to the directory where you want to git

to initialize .git/

        $ git init .

to check tracked and untracked files

        $ git status

git doesn't track every file in your directory, you need to add files to be tracked. for example to add *test.txt*

        $ git add test.txt

if you want to add all files in your directory to git, `$ git add *`. this will add all your folders (incluidng files in these folders) and files in your directory to be tracked by git. if you want some files or folders not to be tracked but still want to use `$ git add *` command for convenience, you need to set up you .gitignore file 

then to see the changes

        $ git status

you will see a new green line `new file: test.txt`

this is the staging area. changes are recognized by git, but not yet been saved into git. if we want to save the changes, you need to do `$ git commit`. the staging area just tells you if we make a commit what will be saved

to commit changes, or in other words, to save your changing
 
        $ git commit -m 'added a file test.txt'

you now have your first commit. to check commits your have made.

        $ git log

to quit log, just type keyborad `q`

adding a line 'this is a new line' into test.txt, then test.txt is modified. do

        $ git status

again, you will see red line`modified: test.txt`, red color tells you these changes have been made but not yet be added

to see the changes, you can do 

        $ git diff test.txt

before we commit these changes, we need to add these changes 

        $ git add test.txt

and commit, then this change would be saved

        $ git commit -m 'added first line of code'

you can chenck all commits you have made by 

        $ git log

to go into the detail of a particular commit

        $ git show number

where number is first 6 character of the commit id



---
## branching

you have your source code which works perfectly well. but you want to make some changes to it, and everything maight went wrong due to your modification. then we use git branch and start to work in a new branch, which allows you to make some changes without modifying your source code until you merge your new branch into your original branch.

how branch works is making a copy of the original branch to a new branch.

the default branch when you initialize your git in your directory is *master*. to create a new branch *develop*

        $ git branch develop

you can check all branch you created by 

        $ git branch

the the \* mark and the green color tells you which branch you are now. 

to move to branch *develop*, type

        $ git chechout develop

then we can see status, make changes, add changes and commit changes exactly the same as we introduced above.

if we go back to *master* branch

        $ git chekout master

nothing is modified.

let's do something more on develop branch

        $ git checkout develop

        $ git checkout -b new_feature

this will create and checkout to a *new_feature* branch based on *develop* branch

what should we do to combine all changes we have made in branch *new_feature* to branch *develop*, we use git merge

first we need to go back to *develop* branch

        $ git checkout develop

and merge *new_feature* back to *develop*

        $ git merge new_feature

what git will do is create a new commit called merge commit. if you check the commit by

        $ git log

you will see commits we have made in branch *new_feature* are now in branch *develop*

also to merge branch, instead of `$ git merge new_feature`, you can type

        $ git merge --no-ff new_feature

and we will be asked to edit merge message

1. type some message
2. `Ctrl+C+O`
3. type the file name(such as "Merge_new_feature") and press Enter
4. `Ctrl+X` to exit (press n if all the buff are already saved)

at this stage, the change in *develop* caused by merging *new_feature* are **already added and commited**

## pushing to github
---

to push your repository to a github repository, you need to create an empty repository in github, then link your local repository to your remote github empty repository. you can do this following the steps shown in the setting page when a new repository is initialized in github.

after you have linked your local repository to your github repository, or ir you are working on a git clone local repository, you can push a particular branch in the repository after you finished your commit. for example if we want to push branch *develop*

        - git push -u origin develop
        
then enter username and password of your github account. done! 
