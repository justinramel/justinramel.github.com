---
layout: post
title: "vim tip: !mkdir %:h"
date: 2012-09-06 22:10
comments: true
categories: vim
---

I just subscribed to [Destroy All Software](http://www.destroyallsoftware.com/)
as well as the great content, I'm picking up lots of vim tips. I'm having to
pause the video a lot, [Gary](http://twitter.com/garybernhardt) is just too
damn fast. Any way I'm going to start writing these vim gems down in the vain
hope I'll remember some of them.

## Quickly creating a project structure

It's possible to setup a new project without leaving vim. Lets create a new dir
for a quick demo:

```
mkdir demo
cd demo
vim
```

From the vim command prompt we can create a new user model in the models dir
using the vim command `:n models/user.rb`

{% img images/vim-tip-1/new-file.png %}

Lets break this command down:

* __:n__             - n is short for new as in file
* __models/user.rb__ - the directory and name of our new file

This creates the new file in a vim buffer but when we go to write this file we
get an error `E212: Can't open file for writing`, this is because the directory
models does not exist.

{% img images/vim-tip-1/write-error.png %}

We can create this directory right from the vim command prompt with `!mkdir %:h`

{% img images/vim-tip-1/mkdir-command.png %}

Now the directory has been created we can write the new file from vim.

So what does the cryptic command `!mkdir %:h` actually mean? Let break it down:

* __:!__    - Execute {command} with the shell
* __mkdir__ - Make a directory shell command
* __%:h__   - The directory of the current file (in our case models\)

The full vim help text for `%:h`:

```
:h	Head of the file name (the last component and any separators
	removed).  Cannot be used with :e, :r or :t.
	Can be repeated to remove several components at the end.
	When the file name ends in a path separator, only the path
	separator is removed.  Thus ":p:h" on a directory name results
	on the directory name itself (without trailing slash).
	When the file name is an absolute path (starts with "/" for
	Unix; "x:\" for MS-DOS, WIN32, OS/2; "drive:" for Amiga), that
	part is not removed.  When there is no head (path is relative
	to current directory) the result is empty.
```

## Deeper folder structure

You can create deeper folder structures using the same technique with one extra
switch on the mkdir command.

```
:n specs/models/user_spec.rb
:!mkdir -p %:h
:w
```

The `-p` switch will create the intermediate directories for you. If you don't
use this switch the command will fail.

The full command line help for the `mkdir -p` switch:

```
-p	Create intermediate directories as required.  If this option is not
specified, the full path prefix of each operand must already exist.  On the
other hand, with this option specified, no error will be reported if a
directory given as an operand already exists.  Intermediate directories are
created with permission bits of rwxrwxrwx (0777) as modified by the current
umask, plus write and search permission for the owner.
```

I think that's as much as I need to know about `:!mkdir %:h` for now.
