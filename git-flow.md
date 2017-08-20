# git flow (ignore this part, not yet finished)
---

git flow is a plugin for git, which makes it very easy for you to have a stream line work flow that you can share with your teammates.

git flow creates its own command to group commands in git.

## initialization
---

what you need to do first is to initialize git-flow in your repository. point is that **you need to have git already initialized in your repository**

        $ git flow init -d
        
`-d` means default setting for git-flow

there are default four kinds of branches available in git-flow. let's suppose that you have created a new branch based on *develop* called *feature/new_feature* by git. then this new branch will be initialied to be a feature branch by git-flow

if you type 

        $ git flow feature finish new_feature
        
then this new branch will be closed and deleted. if you type `$ git branch` you will see that branch *feature/new_feature* disppeared
