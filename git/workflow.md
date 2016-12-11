## Git Workflow

### Tricky Things
Scenario:
>You complete a part of a feature branch and would like to push it to origin.
>You checkout development, pull from remote origin, and then checkout your
>feature branch. You rebase your feature branch on the now updated development
>and push your feature branch to remote origin.
>However, a couple days later you find something that really needs changing in
>that feature branch. So you change it, checkout development, pull remote origin,
>and checkout feature branch again. You then rebase feature branch onto the now
>updated development and try to push, but it won't let you!

The reason you will not be able to push the feature branch after you have rebased
and pushed it a second time is because rebase changes your branches past history.
Therefore, there will be a conflict with the old rebased and pushed feature branch
and the new rebased and pushed feature branch.

One way to handle this situation is to delete the feature branch off of your
remote repo. That takes a few steps though, and there is an easier way to do it.
Simply type the following command in your feature branch after rebasing it onto
development:

    git push --force-with-lease [origin <branch-name>]

Just for clarity, the square brackets around the end of the command mean that those
commands might be optional, thus making it so you only have to type the first part.
It is good form to try to avoid --force commands as much as possible but in this
instance that would be a correct use of one.
