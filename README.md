# Git Branching

## Learning Goals

- Explain the primary role of branching
- Explain creating a branch
- Explain adding and committing changes
- Explain pushing branches
- Identify local and remote branches
- Explain pulling branches
- Explain merging branches
- Explain deleting branches

## Introduction

We're faced with many choices in life; some of these choices are easier, more convenient, or "safer" than others: Move away from familiarity or experiment with moving away and residing in a brand new city? Choose the usual ramen dish, or try it extra spicy? Style your hair the same or try cutting it all off into a radically new look?

Consider a computer upgrade. We have the option of buying a new computer, a used computer, or maybe there's nothing "wrong" with our current computer&emdash;we want more storage space. 

The cheapest option is most likely to buy compatible new parts for our existing computer. However, we've never attempted tinkering with hardware in our computer before, and after buying all the tools and parts, we follow an instructional video to make the upgrades. In this case, we only have one computer to work on, and nowhere to test out opening up a computer and connecting new parts. We have to be careful not to damage anything else that makes the computer work.

Lukcily, with code we have a "sandbox", or a safe place, to experiment with different outcomes. With `git` and GitHub, we're given "branching" as an option so that we can _branch out_ from our original repo and any working code it contains, and make changes separately. If the code works out, we can keep it! If not, we can throw it out and start fresh. What a relief!

## Explain the Primary Role of Branching

Play off of this reference:
"Wouldn't it be great if you could try things out in "sandbox" and then throw it away, with no consequence, if it didn't work out? "Branches" in git allow exactly this. You can propose "parallel universes" of code that can be compared, discussed, tried out, and ultimately imported or thrown away."

<Go into a more specific real world applications of branching> 

## Explain Creating a Branch

<Go into details of how to create branches from an existing repo>

## Explain Adding and Committing Changes

<Go into details of how to add and commit to a branch>
- `git add .`
- `git add -p`
- any other relevant adding commands
- `git commit -m`
- any other relevant committing commands

<Explain importance of commit messages here>

## Explain Pushing Branches

<Go into details of how to push to a branch>

## Identify Local and Remote Branches

- local branches `git branch` lists all locals
- remote branch `git remote` lists all remotes
- remote tracking branch `git branch -r` lists all the remote-tracking branches
- local tracking branch 

A local branch is a branch that only you (the local user) can see. It exists only on your local machine.

A remote branch is a branch on a remote location (in most cases origin). You can push the newly created local branch `myNewBranch` to `origin`. Now other users can track it.

A _remote tracking branch_ is a local copy of a _remote_ branch. When myNewBranch is pushed to origin using the command, a remote tracking branch named `origin/myNewBranch` is created on your machine. This remote tracking branch tracks the remote branch `myNewBranch` on origin. You can update your remote tracking branch to be in sync with the remote branch using `git fetch` or `git pull`.

A _local tracking branch_ is a local branch that is tracking another local branch. This is so that you can push/pull commits to/from the other branch. Local tracking branches in most cases track a remote tracking branch. 

When you push a local branch to `origin` using the `git push` command with a -u option (as shown above), you set up the local branch `myNewBranch` to track the remote tracking branch `origin/myNewBranch`. 

```
fatal: The current branch myNewBranch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin myNewBranch
```

**This is needed to use git push and git pull without specifying an upstream to push to or pull from.**

## Explain Pulling Branches

<Go into details of how to pull a branch>

## Explain Merging Branches

<Go into details of how to merge a branch>


## Explain Deleting Branches

<Go into details of how to delete branch when work is merged or branch is stale>

## Conclusion

Branching allows developers to make edits to a code base while isolating their work from other work. While this is a very useful tool for working on your own code, in a collaborative environment, it is common for several developers to share and work on the same source code. Some developers will be fixing bugs, others will be implementing new features, etc. It's a standard practice to have a system in place for managing different versions of the same code base. It allows us to stay organized, work more freely, collaboratively, and better avoid set backs from making hard-to-undo mistakes.

## Resources

[3.1 Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
[Using branches](https://backlog.com/git-tutorial/using-branches/)