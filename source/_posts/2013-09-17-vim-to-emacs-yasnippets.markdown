---
layout: post
title: "Vim to Emas - YASnippet"
date: 2013-09-17 22:01
comments: true
categories: emacs
---
Another plugin I miss from Vim is [snipMate](http://www.vim.org/scripts/script.php?script_id=2540), I use this plugin to insert snippets of code while programming. Once again Emacs has me covered, [YASnippet](https://github.com/capitaomorte/yasnippet) offers the same functionality.

## Setup
Create a `yasnippet.el` in the `.emacs.d/personal` folder.

[personal/yasnippet.el](https://github.com/justinramel/prelude/blob/master/personal/yasnippet.el)

```
(prelude-require-package 'yasnippet)

(require 'yasnippet)
(yas-global-mode 1)
```

Here I make sure the `yasnippet` package is available then require the package and enable it globally.

## Personal Snippets
You can create your own personal snippets in the `.emas.d/snippets` folder. More details in this slightly outdated [guide](http://capitaomorte.github.io/yasnippet/).

## Ruby Snippets
I have also installed a set of ruby and rspecs snippets from bmaland's [repo](https://github.com/bmaland/yasnippet-ruby-mode). I simply cloned the repo into the personal snippest folder with name ruby-mode. Note the name is important it needs to match the Emacs mode where the snippets are used.

```
git clone git@github.com:bmaland/yasnippet-ruby-mode.git ~/.emacs.d/personal/ruby-mode
```
