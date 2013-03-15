---
layout: post
title: "Git feature workflow - basic commands"
date: 2013-03-15 13:06
comments: true
categories: git
---
List of basic commands to use during feature branch workflow.

##Create feature branch

```
git checkout -b my-awesome-new-feature
```

> **NOTE:** The _-b_ parameter means branch, it saves us having to use two separate git commands. Without this option we'd need to branch then checkout.

Now do lots of work on the new feature...

##Find out what has changed

When finished working on the new feature find out what has changed.

```
git status
```

##Add changes to git

Either add each file manually using:

```
git add my-changed-file.txt
```

Or add all the files in the current directory.

```
git add .
```

Run `git status` one more time to get a list of everything that is going to be committed.

>**NOTE:** Accidentally added files can be removed using the command `git rm <filename>`

##Commit changes

Commit your changes with a *meaningful* message.

```
git commit -m "my awesome new feature, this changes everything!"
```

##Push changes

Push the new feature up to github so we can do a pull request.

```
git push origin -u my-awesome-new-feature
```

The new branch should now be visible on github and we can now issue a pull request.