# Git: Working with Local Branches

## Learning Goals

- Demonstrate the primary role of branching
- Demonstrate creating a branch
- Demonstrate adding and committing changes
- Demonstrate pushing branches

## Introduction

We're faced with many choices in life; some of these choices are easier, more
convenient, or "safer" than others.

Consider a computer upgrade. We have the option of buying a new computer, a used
computer, or maybe there's nothing "wrong" with our current computer&mdash;we
want more storage space.

The cheapest option is most likely to buy compatible new parts for our existing
computer. However, we've never attempted tinkering with hardware in our computer
before, and after buying all the tools and parts, we follow an instructional
video to make the upgrades. In this case, we only have one computer to work on,
and nowhere to test out opening up a computer and connecting new parts. We have
to be careful not to damage anything else that makes the computer work.

It would be nice if we could test out our computer upgrading skills first.
Luckily, we _do_ have this option when coding!

If we had an identical computer that we could experiment on, we could worry less
about making any mistakes that could impact our working machine. This is the
exact concept of branching.

## Demonstrate the Primary Role of Branching

With code we have a "sandbox", or a safe place, to experiment with different
outcomes. With Git, we're given "branching" as an option so that we can _branch
out_ from our original repo and any working code it contains, and make changes
separately. If the code works out, we can keep it! If not, we can throw it out
and start fresh. What a relief!

> **Tip:** Branches can be merged into any one branch as long as they belong to
> the same repository.

## Demonstrate Creating a Branch

Branching allows us to branch out from the original code base and isolate our
work from working code, whether it's on a solo project or a collaborative
project.

Changes in the branch that we branched _from_, or changes on _other_ branches,
will not affect our branch unless we take action to integrate those changes.

To create a new branch from the branch we are currently on (in this case, it's
the default `master` branch), we type the command:

```bash
git branch new-branch-name
```

If we want to create a new branch _and_ move onto that branch in a single
command, we can use:

```bash
git branch -b new-branch-name
```

We can switch **back to the previous** branch using:

```bash
git checkout -
```

To switch to any branch that we're not currently on we use:

```bash
git checkout other-branch-name
```

!["git branch"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/new%20branch.gif)

As we can see, we now have a copy of all of our original branch's progress in
our new branch.

!["git log on master"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/log1.png)
!["git log on new branch"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/log2.png)

## Demonstrate Adding and Committing Changes

Now that we've created a new branch, which is our place to safely make changes,
let's make some modifications to this branch.

First, we're going to make changes in our `README.md` and save them. To confirm
that changes have been made, we can always check by using `git status`. Now that
the file has changed from its original state, we can _stage_ these changes,
which tells Git that we want to keep track of changes to this file.

["git status"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20status.gif)

We made a few changes throughout the file and want to see what changed, so we
will review changes in "chunks" using `git add -p`. We can accept each change,
or discard others that we don't want. 

!["git add -p"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20add%20p.gif)

We can use the same command to view changes across multiple files as well.

If we bulk add files, or know that we want to accept and track all changes that
have been made to any files, we can use:

```bash
git add .
```
This tells Git to track _all_ new changes.

Now that we have some tracked changes to our branch, we will want to make a new
commit. Typically, developers say __"commit small, commit often."__ This workflow
makes it easier to examine what changes have been made over time. we can always
perfect it later&emdash;that's a big reason why we have branches at our
disposal.

To commit the changes that have been staged so far we use:

```bash
git commit -m
```
The `-m` flag allows us to add message along with the commit. These messages are
the best way to give context about a change to our future selves or other
developers. There are a number of rules that may be established depending on how
you're working, solo or collaboratively, but minimally, we want to limit the
message to 50 characters explaining what changed:

!["Git Commit with Message"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20commit.gif)


## Demonstrate Pushing Branches

We've created a new branch, committed some changes, and now we should push this
branch up to our remote, which is the GitHub repo. The `git push` command takes
two arguments: The remote name, commonly `origin` and the branch name, commonly
`master`.

If we have a branch that does not exist on the remote repository, we use:

```bash
git push -u origin new-branch-name
```

If the branch exists on the remote, as in it's previously been pushed, we can
simply use `git push`.

!["git push without flag"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20push.gif)
!["git push -u"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20push%20u.gif)

## Conclusion

Branching allows developers to make edits to a code base while isolating their
work from other work. We can create branches, back them up to remote locations,
and continue to work with them locally. It's a standard practice to have a
system in place for managing different versions of the same code base. It allows
us to have a "safe space" for making edits without affecting the primary code
base.

## Resources

[Pushing to a remote](https://help.github.com/en/articles/pushing-to-a-remote)
[Git Branch](https://www.atlassian.com/git/tutorials/using-branches)
[3.1 Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
[Using branches](https://backlog.com/git-tutorial/using-branches/)
