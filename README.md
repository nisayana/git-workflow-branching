# Git Branching

## Learning Goals

- Explain the primary role of branching
- Explain creating a branch
- Explain adding and committing changes
- Explain pushing branches
- Identify local and remote branches
- Explain getting updates from remote
- Explain merging branches
- Explain deleting branches

## Introduction

We're faced with many choices in life; some of these choices are easier, more
convenient, or "safer" than others.

Consider a computer upgrade. We have the option of buying a new computer, a used
computer, or maybe there's nothing "wrong" with our current computer&emdash;we
want more storage space.

The cheapest option is most likely to buy compatible new parts for our existing
computer. However, we've never attempted tinkering with hardware in our computer
before, and after buying all the tools and parts, we follow an instructional
video to make the upgrades. In this case, we only have one computer to work on,
and nowhere to test out opening up a computer and connecting new parts. We have
to be careful not to damage anything else that makes the computer work.

It would be nice if we could test out our computer upgrading skills first.
Luckily, we _do_ have this option when coding!

## Explain the Primary Role of Branching

If we had an identical computer that we could experiment, we could worry less
about making any mistakes that could impact our working machine. This is the
exact concept of branching.

With code we have a "sandbox", or a safe place, to experiment with different
outcomes. With `git` and GitHub, we're given "branching" as an option so that we
can _branch out_ from our original repo and any working code it contains, and
make changes separately. If the code works out, we can keep it! If not, we can
throw it out and start fresh. What a relief!

Branches can be merged into any one branch as long as they belong to the same
repository.

## Explain Creating a Branch

Branching allows us to branch out from the original code base and isolate our
work from working code, whether it's on a solo project or a collaborative
project.

Changes in the branch that we branched from, or other branches, will not affect
our branch without taking action to integrate other changes.

To create a new branch from the branch we are currently on (in this case, it's
the default `master` branch), we type the command `git branch new-branch-name`.

If we want to create a new branch _and_ move onto that branch in a single
command, we can use `git branch -b new-branch-name`.

We can switch back to the previous branch using `git checkout -`, or to any
branch that we're not currently on, we use `git checkout other-branch-name`.

< insert gif of creating a branch from master >

As we can see, we now have a copy of all of our original branch's progress in
our new branch.

< show img of identical logs >

## Explain Adding and Committing Changes

Now that we've created a new branch, which is our place to safely make changes,
let's make some modifications to this branch.

First, we're going to make changes in our `README.md` and save them. To confirm
that changes have been made, we can always check by using `git status`. Now that
the file has changed from its original state, we can _stage_ these changes,
which tells `git` that we want to keep track of changes to this file.

< gif of git status >

We made a few changes throughout the file and want to see what changed, so we
will review changes in "chunks" using `git add -p`. We can accept each change,
or discard others that we don't want. 

< gif of git add -p being used >

We can use the same command to view changes across multiple files as well.

If we bulk add files, or know that we want to accept and track all changes that
have been made to any files, we can use `git add .`. This tells `git` to track
ALL new changes.

Now that we have some tracked changes to our branch, we will want to make a new
commit. Typically, developers say "commit small, commit often". This workflow
makes it easier to examine what changes have been made over time. we can always
perfect it later&emdash;that's a big reason why we have branches at our
disposal.

To commit the changes that have been staged so far we use `git commit -m`. The
`-m` flag allows us to add message along with the commit. These messages are the
best way to give context about a change to our future selves or other
developers. There are a number of rules that may be established depending on how
you're working, solo or collaboratively, but minimally, we want to limit the
message to 50 characters explaining what changed:

< git commit with message >


## Explain Pushing Branches

We've created a new branch, committed some changes, and now we should push this
branch up to our remote, which is the GitHub repo. The `git push` command takes
two arguments: The remote name, commonly `origin` and the branch name, commonly
`master`.

If we have a branch that does not exist on the remote repository, we use `git
push -u origin new-branch-name`. If the branch exists on the remote, as in it's
previously been pushed, we can simply use `git push`.

< gif of git push >


## Identify Local and Remote Branches

We've gone through the steps of pushing our branches to GitHub, so let's clarify
some terminology around different types of branches and related commands before
proceeding.

### Local Branches

So far, we've seen examples of local branch operations. The git branch command
also works on remote branches. A local branch is a branch that only we (the
local user) can see. It exists only on _your_ computer.

we can see a list of all local branches on your computer with `git branch`.

### Remote Branches

A remote branch is a branch on a remote repository (in most cases origin). When
we push our local branch `new-branch-name` to `origin`, we and other users can
track it. 

We can see a list of all remotes with `git remote` (it will most likely only be
`origin`). More importantly, we can see a list of all remote branches of the
repository with `git branch -a`.

### Remote Tracking Branches

A _remote tracking branch_ is a local copy of a _remote_ branch. When
`new-branch-name` is pushed to origin using the command, a remote tracking
branch named `origin/new-branch-name` is created on your machine. This remote
tracking branch tracks the remote branch `new-branch-name` on origin. we can
update your remote tracking branch to be in sync, or up-to-date, with the remote
branch using `git fetch` or `git pull`. We will go more in depth a little later
on these commands.

### Local Tracking Branches

A _local tracking branch_ is a local branch that is tracking another local
branch. This is so that we can push/pull commits to/from the other branch. Local
tracking branches, in most cases, track a remote tracking branch. 

When we push a local branch to `origin` using the `git push` command with a `-u`
option (as shown previously), we set up the local branch `new-branch-name` to
track the remote tracking branch `origin/new-branch-name`. 

Otherwise, we will see this when we try `git push`:

```bash
fatal: The current branch new-branch-name has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin myNenew-branch-namewBranch
```

**Note:** This is needed to use `git push` and `git pull` without specifying an
upstream to push to or pull from.

## Explain Getting Updates From Remote

Getting updates to branches come into play when there are branches that live on
a remote repository. These branches can be ones that we are tracking locally, or
ones that have been created and pushed up from other computers. 

Previously, we mentioned that we can use commands the commands `git fetch` or
`get pull` to sync local tracking branches with remote tracking branches. On the
local tracking branch that we want to sync, either of these commands are used to
download new data from a remote repository. One of these actions must be taken
to do so. Your local tracking branch is only as up-to-date as the last time we
**explicitly** downloaded the data from the remote.

What is the difference between fetch and pull? 

< gif showing git fetch vs. git pull>

- `git fetch` **only** downloads new data from a remote repository. Fetch will
  never change anything on your local repository. Fetching is what you do when
  you want to great for seeing all the changes that happened in a remote
  repository since your last sync.
- `git pull` brings a local tracking branch up-to-date with its remote version,
  while also updating your other remote tracking branches. Pull not only
  downloads new data&emdash;it also directly integrates it into your current
  working copy files, so we should not have any uncommitted local changes before
  we pull. 

  **Note:** `git pull` performs a `git fetch` and a `git merge`. We will go into
  depth of what a merge is next.

## Explain Merging Branches

Merging allows us to take our branches and integrate them back into a single
branch. We can use `git merge other-branch-name` to integrate the changes from
one branch to the branch to the receiving branch (the branch we are currently
on).

So, if we want to take the changes we created on `new-branch-name` and merge
them back into the `master` branch now that we've confirmed the changes are safe
to integrate, we do so by using these commands:

```bash
git checkout master # This switches us back to the master branch
git merge new-branch-name # This integrates our new branch, new-branch-name, and its changes into master
```

As long as the `git` histories are still in sync, you will see no _merge
conflicts_, and now all the changes that were made on the branch
`new-branch-name` will be integrated into `master`. With work on this branch
completed and merged, we no longer need it. Any additional work moving forward
can be done on a new branch.

## Explain Deleting Branches

Since we've merged our changes master, we can safely delete our local version of
`new-branch-name`. A branch can be deleted by providing the `-d`/`–D` options
with the `git branch` command. Before deleting the `new-branch-name`, we should
be on another branch. Currently, we're still on `master`.

The `-d` option stands for `--delete`, which would delete the local branch only
if you have already _pushed_ and _merged_ it with your remote branches.

The `-D` option stands for `--delete --force`, which deletes the branch
regardless of its push and merge status. Be careful with the usage of this one,
however, this is useful when you have a branch with changes that you don't want
to merge (maybe you experimented with things here and decided to throw them
out).

To delete an obsolete local branch (that has been pushed and merged), we type
`git branch -d <branch-to-delete>`. To make sure this branch was successfully
deleted, we type `git branch`. It should no longer exist in the list of local
branches. 

<gif of git branch -d, git branch -D and git branch being used>

To delete the remote tracking branch, we can use `git push <remote_name (most
likely origin)> --delete <branch-name>`. To list all remaining remotes, again,
we can type `git branch -a`. It should no longer exist in the list of remote
branches. 

## Conclusion

Branching allows developers to make edits to a code base while isolating their
work from other work. We can create branches, back them up to remote locations,
and continue to work with them locally. While this is a very useful tool for
working on your own code, in a collaborative environment, it is common for
several developers to share and work on the same source code. Some developers
will be fixing bugs, others will be implementing new features, etc. It's a
standard practice to have a system in place for managing different versions of
the same code base. It allows us to stay organized, work more freely,
collaboratively, and better avoid set backs from making hard-to-undo mistakes.

## Resources

[Pushing to a remote](https://help.github.com/en/articles/pushing-to-a-remote)
[Git Branch](https://www.atlassian.com/git/tutorials/using-branches)
[3.1 Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
[Using branches](https://backlog.com/git-tutorial/using-branches/)
[What is the difference between ‘git pull’ and ‘git fetch’?](https://www.javacodegeeks.com/2018/09/git-pull-git-fetch.html)
[What's the difference between git fetch and git pull?](https://www.git-tower.com/learn/git/faq/difference-between-git-fetch-git-pull)
[git fetch](https://www.atlassian.com/git/tutorials/syncing/git-fetch)