# Git cheat sheet
This document helps you to get started on the version control system
workflow of the this project. In here you will find helpful commands
and an explanation of every step from cloning the repository and finally
adding your contents to the project.

For a detailed description on how to use branches, how to work with
merge requests, and what tags are used how in this project, please refer
to [Branch standards](branch_standards.md).

## Getting started

First of all you have to clone the this project to be able to start
the development process. If you want to use a graphical tool for coding,
you should have already installed one that you like. Cloning the
this project with your favorite IDE isn’t a part of this guide but
you better setup and use IDE. The cheat sheet will help you to get
things going on the command line only.

## Git Knowledge

If you are not familiar with using Git, you can learn it more in detail
using from [Git - SCM Guide](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) and also from [Git Guide](https://rogerdudler.github.io/git-guide)

### Prerequisites

You need to have access on the dedicated Git instance. Create
an issue on <https://github.com/redhat-cop/org/issues> if you don’t have
an account or permission on there.

To be able to clone a git repository, the git binary is a core
requirement. Please make sure you have it available on your local
operating system.

A smooth workflow with the remote git instance requires you to add one
of your public keys for authentication with the server. If you don’t
have a key already, please follow the [Git
guidelines](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).

### Clone the project

Open your preferred command line tool to get started.

Open the link of the Git instance. You will get a list of projects where
you are currently assigned at least as a project member. Click on the
`rhis-code` project. This project represents the base of the project development. There is another repository contains Ansible inventories which will fed the base project with
variables based on the surrounding data center location.

Click the `Clone` button at the top right corner to retrieve the
appropriate link. Copy the link which is labeled as `Clone with SSH`. Go
to your command line and type in the following:

    git clone "link that you have just copied"

Press enter and the repository will now be cloned to your computer.

## Explore the environment

### Show ongoing work

After you have cloned the repository, you can give yourself a quick
overview about work that is currently ongoing within the repository. Per
default, only the `main` branch will be cloned to your computer. If you
want to access the work of your colleagues, enter and execute:

    git fetch --all

Now you can execute

    git branch -r

and get a list of all of the branches that are currently in progress and
not merged into the master yet.

## Make changes

### Create a branch

If you want to contribute changes and additions to the repository, you
have to open up your own branch based on the current `devel` branch. To
ensure you have the latest changes on the `devel` branch present on your
local copy, type in the following commands:

    git checkout devel
    git pull

Based on the latest changes, you can create your own branch with the
following command. Be sure to follow the branch naming conventions.
Otherwise the your changes won’t be accepted later on.

    git checkout -b "name of your branch"

The command fulfills two steps in one. At first git is going to create
the branch you have requested and this branch will also be checked out
directly so that you don’t have to switch to the branch manually.

You can now modify the contents of the project within your
repository.

### Track changes

The tracking of your modifications is essential. Otherwise you can’t
publish them into the `devel` branch. You can get a list of changed or
untracked files with

    git status

Adding of new or modified files requires you to execute

    git add .

Keep in mind that this command adds all of your changes to the current
set of changes. If you want to exclude some of the files, you have to
add them manually via

    git add "file name"

### Commit changes

To add your changes into the git tree, you have to bundle them with a
commit message. This step can be done by executing

    git commit -m "your commit message"

Be sure to follow the guidelines on how to write proper commit messages.
Your changes might be rejected by one of the reviewers if you don’t
follow these constraints. You are able to change the message of your
commits later on via the `git rebase` command. Since this operation is
very error prone, always try to follow the guidelines in the first shot.

1.  Prefix relevant parts of commit messages with one `Feature:` or
    `Hotfix:` so that we can filter for it and generate
    half-automatically release notes.

    -   Feature: for any new feature, tell what needs to be done to
        profit from it.

    -   Bugfix: if it’s a bug fix.

### Publish changes

You can now push your changes to the remote repository. This operation
will publish your work to be accessible by all of the other colleagues.
Per default the remote is called `origin`. Feel free to modify it if you
have renamed the repository or added multiple ones:

    git push origin "name of your branch"

## Squash commits

Squashing commits means you take multiple commits and squash them into
one. This is typically best done before creating a merge request such
that the branch is clean and has just one commit, even if you created a
number of commits before creating the MR. It is also useful in case you
want to change history of your branch, for example if you pushed a large
file and then deleted it. If you don’t squash your commits, the file
will stay in the git history, even if it isn’t on your branch. If you
squash your commits, the file will never be pushed to git, because the
changes cancel each other out (commit 1 added a big file, commit 2
removed the big file → squashing the two commits means there’s no file
in the branch).

### Before squashing

It is good to create a local backup branch:
`git checkout -b local-bkp; git checkout -`

The command will create a new branch and return you to your branch.

### Squashing

1.  Find how many commits are there on your branch, for example using
    `git log --oneline`.

2.  Issue interactive rebase: `git rebase -i HEAD{tilda}$num_of_commits`
    where `$num_of_commits` is a number of commits you want to squash.
    If you want to squash 3 commits, it would be
    `git rebase -i HEAD(tilda)3`.

3.  In the next screen, keep the first line as is and change the first
    word of the next lines from `pick` to `squash`:

        # original state
        pick bd52ec1 Ignore Vim swap files
        pick f185eb8 managed_os: Add new feature to the role to set hostname on server
        pick f4dcf78 managed_os: minor changes based on MR feedback

        # Change all commits to squash except for the first one
        pick bd52ec1 Ignore Vim swap files
        squash f185eb8 managed_os: Add new feature to the role to set hostname on server
        squash f4dcf78 managed_os: minor changes based on MR feedback

        # After the above is done, save and exit your editor, e.g. :wq or :x in VIM

4.  In the next screen, change your commit messages. Delete all
    non-commented files and input a new commit message, which will be
    the new commit message for your squashed commits.

### After squashing

At this point, you have changed your history. Check the git diffs to see
whether you have a commit with changes that you wanted. For example, use
`qgit` on Fedora to see visual representation of your diffs.

If you want to start again, you can restore the branch to your original
state: `git reset --hard local-bkp`.

If the state is as desired, you can now push your changes into your
branch.

To push, execute: `git push origin +$branch_name`. This will issue a
force push. For example, if your branch is `feature-xyz`, issue
`git push origin +feature-xyz`.

If you created a backup branch, you can now safely delete it:
`git branch -D local-bkp`.

### Merge changes

Merge requests (pull requests) are the only way of adding your work into
the `devel` branch. Therefore you have to create a merge request on the
version control system. This request will be reviewed and approved by at
least another person to ensure a good level of code quality.

Open the start page of the version control system, select the this
project and click on `Pull Requests` on the left side of the page. The
newly loaded page allows you to open a `New Pull Request` at the top
right corner. There you have to select the source branch and target
branch. The source branch represents the changes that you have pushed
previously into the remote repository. As target branch the `devel`
branch should already be selected. Fill out the required fields in the
next window and give your changes a proper description and title. If you
are finished submit the merge request and wait on approval.

### Cleanup

When you can merge the request after you got approval, you can safely
delete the source branch on the remote repository. This can be done by
opting in the responsible checkbox during the merge process. Cleanup can
also be done on your local copy. You can delete a completed branch
locally with

    git branch -d "branch name"
