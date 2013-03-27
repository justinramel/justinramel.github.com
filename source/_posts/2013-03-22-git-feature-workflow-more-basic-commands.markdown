---
layout: post
title: "Git feature workflow - more basic commands"
date: 2013-03-22 23:46
comments: true
categories: git
---

##Switch on vim colour

Do your self a favour and switch on git colour it makes the command line output
much easier to read.

`git config --global --add color.ui true`

##Remote branches

Working as part of a team at some point you'll need to take a look at a team
mates branch, first they need to push their branch up to github.

`git push origin -u my-awesome-new-feature`

##Pull down a team mates branch

Don't know or can't remember the remote branch name?

`git branch -r`

Next you need to create a local branch that tracks the remote branch.

`git checkout --track origin/my-awesome-new-feature`

This command creates a local branch named my-awesome-new-feature which is
tracking the remote branch. Now when you push your changes the remote branch
will be updated.

- More info on [stackoverflow](http://stackoverflow.com/questions/9537392/git-fetch-remote-branch)

##Fix a conflict

When you have a conflict in a feature branch you'll not be able to auto merge
on github you'll need to merge the branch manually.

```
git checkout master
git merge my-awesome-new-feature
```

Fix any conflicts.

- Check out this
  [vimcast](http://vimcasts.org/episodes/fugitive-vim-resolving-merge-conflicts-with-vimdiff/)
  for a nice way to fix conflicts in vim using the [fugitive
  plugin](https://github.com/tpope/vim-fugitive).

> fugitive.vim: a Git wrapper so awesome, it should be illegal

Finally `git push` the merge up to github and you're done.
