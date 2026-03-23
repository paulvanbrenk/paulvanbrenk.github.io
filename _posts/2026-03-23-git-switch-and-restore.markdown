---
layout: post
title: "The Case Against git checkout"
date: 2026-03-23 10:00:00 -0500
categories: technology
---

I still see `git checkout` in a lot of examples, and I still type it
sometimes out of habit. But when I am moving between branches or undoing file
changes, I reach for `git switch` and `git restore` instead. At this point, I
think they are the better defaults, and I think `git checkout` is one of the
more confusing commands people still teach as normal Git.

## Why `git checkout` Feels Overloaded

`git checkout` does at least two different jobs. The
[docs](https://git-scm.com/docs/git-checkout) put it plainly:

> `git checkout` has two main modes: switch branches, and restore a different
> version of a file.

That one sentence captures the whole problem. It can move you to another
branch, and it can also replace file contents in your working tree.

These are all valid:

```bash
git checkout main
git checkout -- README.md
git checkout abc123 -- README.md
```

The problem is that these commands do not mean the same thing. Git reads the
arguments and works out which mode you probably meant. That usually works, but
it also means one of the most common commands in Git depends heavily on
context and punctuation.

I think that is bad command design. Branch movement and file restoration are
different operations. They should not share a name and rely on a separator
like `--` to make the intent legible.

## Why `git switch` Is Better for Branches

`git switch` has a narrower job. The
[docs](https://git-scm.com/docs/git-switch) describe it simply:

> Switch to a specified branch. The working tree and the index are updated to
> match the branch. All new commits will be added to the tip of this branch.

That is it. No file restoration mode. No ambiguity. The intent is obvious
as soon as you read the command.

```bash
git switch main
git switch -c feature/login
git switch --track origin/feature/login
```

When I see `git switch`, I know I am looking at branch state, not file state.
That makes shell history easier to scan and team examples easier to follow.
More importantly, it removes a category of ambiguity that never needed to
exist in the first place.

I also like that some sharper edges are more explicit. If I want a detached
`HEAD`, I have to say `--detach`. That is how it should work. Quietly
detaching `HEAD` because a name did not match a branch is not clever. It is
the kind of Git behavior that makes people feel like the tool is waiting for
them to slip up.

## Why `git restore` Is Better for Files

`git restore` covers the file side of the old `checkout` behavior. From the
[docs](https://git-scm.com/docs/git-restore):

> Restore specified paths in the working tree with some contents from a
> restore source. If a path is tracked but does not exist in the restore
> source, it will be removed to match the source.

The main gain is not that it can do something brand new. The gain is that the
command reads closer to what I actually mean, and I think that matters more
than Git culture sometimes admits.

```bash
git restore README.md
git restore --staged README.md
git restore --source=abc123 README.md
git restore --staged --worktree README.md
```

Restore this file. Restore the staged version. Restore from a specific commit.
Restore both the index and the working tree. The flags line up with the task.

Before `git restore`, I usually had to jump between `git checkout` and
`git reset` depending on whether I wanted to discard a change or unstage it.
That split is one of the reasons Git feels harder than it needs to for newer
users, and I do not think "that is just how Git works" is a very good defense
of it.

`git restore --staged` is the part I like most. It makes "unstage this file"
feel like a file operation instead of a history operation. I think it should
be the standard answer when someone asks how to unstage a file.

## Where `git reset` Still Fits

`git restore` does not replace `git reset` entirely. I still use `reset` when
I actually want to move a branch pointer or rewrite local history.

The git docs have a section called
["Reset, restore and revert"](https://git-scm.com/docs/git#_reset_restore_and_revert)
that lays out the distinction:

> - git-revert is about making a new commit that reverts the changes made by
>   other commits.
>
> - git-restore is about restoring files in the working tree from either the
>   index or another commit. This command does not update your branch.
>
> - git-reset is about updating your branch, moving the tip in order to add
>   or remove commits from the branch. This operation changes the commit
>   history.

And then the kicker:

> `git reset` can also be used to restore the index, overlapping with `git
> restore`.

Git still has overlap in its command surface. I just think this version is far
easier to explain than the older `checkout`-does-everything model, and easier
to explain usually means easier to use correctly.

## Why I Think It Matters

I do not think this is just cosmetic. `git checkout` still works, and I am not
arguing that it should disappear. But if I am writing documentation, teaching
Git, or leaving examples in a repo, I think using `checkout` as the default is
the wrong choice now.

A few things get better right away:

- There is less ambiguity between branches and files.
- Commands read closer to intent.
- Dangerous states like detached `HEAD` are more explicit.
- Unstaging a file does not require reaching for `git reset` as often.

That is enough for me. Tools I use every day should be easy to read six months
later, not just easy to type from muscle memory. Familiarity is a weak reason
to keep teaching a worse interface.

## Closing Thoughts

`git switch` and `git restore` are not revolutionary. They are just better
commands for the jobs most people were already doing with `checkout`. I think
that is reason enough to use them.

If you still use `git checkout` for everything, nothing breaks. But if I am
showing someone Git in 2026, I do not think `checkout` should be where I
start.
