# Git: Working with Local Branches

## Learning Goals

- Demonstrate creating a branch
- Demonstrate adding and committing changes
- Demonstrate pushing branches

## Introduction

We're faced with many choices in life; some of these choices are easier, more
convenient, or "safer" than others.

Consider a computer upgrade. Imagine we want to add a new, bigger hard drive.
However, we've never attempted tinkering with computer hardware before. And our
only teacher is some video on YouTube. Also, we _really_ don't want to break
our computer because it's expensive to replace and it's got all our favorite
cat videos on it.

We might choose to "do nothing" because the risk is so great. Because of the
_risk_ we might not want to _try new things_.  Our _freedom_ to try new things
is being held back by _fear_.

The same can be true in code: if we somehow barely get our code working, we
might be afraid to go as far as we ought in order to create clean,
maintainable, understandable code because we're afraid we'll break it.

Git lets you experiment on uncertain code until it works and then bolt that
working code onto your historical working code. If your experiment blows up,
you can simply throw it away without damaging your working code. Git lets us go
from working code to working code, from success to success. We create "parallel
universes" for safe experimentation which can be integrated ("merged") or
thrown away using _branches_.

## Demonstrate Creating a Branch

Branching allows us to branch out _from_ the original code base and isolate our
new, experimental work from working code. Changes in the branch that we branched
_from_, or changes on _other_ branches, will not affect our branch unless we take
action to integrate those changes.

We'll get started by _branching_ on a local Git respository.

By default, we start on the `master` branch. To create a new branch from the branch
we are currently "on," we type the command:

```bash
git branch new-branch-name
```

This will create a local branch callled `new-branch-name`. If we type
`git branch`, we will see all the branches.

```shell
$ git branch
* master
  new-branch-name
```

You'll notice the `*` next to `master`. That's Git telling us that we're
still "on" master. If we make a new commit, it will go on `master`. We
need to get "on" `new-branch-name`. To do this we "check out" the
new branch like so: `git checkout new-branch-name`.

Running `git branch` confirms our "movement."

```shell
$ git checkout new-branch-name
$ git branch
  master
* new-branch-name
```

If we want to create a new branch _and_ move onto that branch in a single
command, we can use:

```bash
git branch -b new-branch-name
```

To switch to any branch that we're not currently on we use:

```bash
git checkout other-branch-name
```

As a shortcut, we can switch **back to the previous** branch using:

```bash
git checkout -
```

!["git branch"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/new%20branch.gif)

As we can see, we now have a copy of all of our original branch's progress in
our new branch.

Here's the log of commits on `master`. We'll learn more about the log later,
but right now it shows us that the last commit was commit `08c0087...` (Yep,
commits are named 128-character long strings made up of numbers and the letters
`a` through `f`).

!["git log on master"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/log1.png)

And on new branch, we see that the last commit was our friend `08c0087...`
They're identical!

!["git log on new branch"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/log2.png)

## Demonstrate Adding and Committing Changes

Now that we've created a new branch, which is our place to safely make changes,
let's make some modifications to this branch.

First, we're going to make changes in our `README.md` and save them.

> **REMEMBER**: To confirm that changes have been made, we can always check by using `git status`.

Now that the file has changed from its original state, we can _stage_ these changes,
which tells Git that we want to keep track of changes to this file.

!["git status"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20status.gif)

We made a few changes throughout the file and want to see what changed, so we
will review changes in "chunks" using `git add -p`. We can stage each change,
or pass over others that we don't want. 

!["git add -p"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20add%20p.gif)

If we know we want all the changes in a file we can add the whole file:

```bash
git add file-name
```

And if we know we want all the changes in all the files in our current directory, we can use:

```bash
git add .
```

> **QUESTION**: Why not ***always*** use `git add .`? When developing we often make more
> changes than we remember. We might make changes that weren't part of the fix or we might
> accidentally write our TODO list inside of a code file. Adding piece-by-piece gives us
> a chance to make sure we want to add everything Git knows has changed. We can use the
> other approaches when needed, but you might commit some junk. Developers say
> __"commit small, commit often."__ There are even more advanced Git tools that will help
> you debug your code and find mistakes and they work better with smaller, more-frequent
> commit histories.

Now that we have some staged changes ready for our branch, we will want to make a new
commit. To commit the changes that have been staged so far we use:

```bash
git commit -m
```

The `-m` flag allows us to add message along with the commit. These messages are
the best way to give context about a change to our future selves or other
developers. There are a number of rules that may be established depending on how
you're working, solo or collaboratively, but minimally, we want to limit the
message to 50 characters explaining what changed:

!["Git Commit with Message"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20commit.gif)

If we leave off the `-m` flag, Git will ask your operating system which editor
you have configured the shell to use to edit your commit messages. Git will
give you pre-filled text file to edit. When you save and quit from your editor,
vim will use this message as the commit.

When getting started, it's wisest to use `-m` but if you want to change Git's
editor, you'll use the following command:

```bash
$ git config --global core.editor "atom --wait"
```

Here we configured Git to use `atom` as the editor for commit messages.

## Demonstrate Pushing Branches

We've created a new branch, committed some changes, and now we should push this
branch up to our remote repo, a GitHub repo. The `git push` command takes
two arguments: The remote name, commonly `origin` and the branch name, commonly
`master`. The remote `origin` is the conventional name for the default remote.
Just like how `master` is the default name for the default branch.

If we have a branch that does not exist on the remote repository, we use:

```bash
git push -u origin new-branch-name
```

If the branch exists on the remote, as in we've used the previous command before,
we can simply use `git push`.

!["git push without flag"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20push.gif)
!["git push -u"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20push%20u.gif)

## Conclusion

Branching allows developers to make edits to a code base while isolating their
work from other work. We can create branches, back them up to remote locations,
and continue to work with them locally.

## Resources

[Pushing to a remote](https://help.github.com/en/articles/pushing-to-a-remote)
[Git Branch](https://www.atlassian.com/git/tutorials/using-branches)
[3.1 Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
[Using branches](https://backlog.com/git-tutorial/using-branches/)
