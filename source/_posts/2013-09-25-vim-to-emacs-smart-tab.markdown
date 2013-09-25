---
layout: post
title: "Vim to Emacs - Smart Tab"
date: 2013-09-25 20:25
comments: true
categories: emacs
---
{% render_partial _partials/vim-to-emacs.markdown %}

The latest thing I'm missing from Vim is tab completion. I'd like to hit tab and have Emacs either insert a snippet or try to auto-complete the word based on what I just typed.

With lots of Googlizing I've managed to hack together a solution, it's not perfect (yet) but still meets most of my needs for now.

## Setup
Download `smart-tab.el` from [genehack](https://github.com/genehack/smart-tab) (or from [me](https://github.com/justinramel/prelude/blob/master/vendor/smart-tab.el)) and save it in to the `.emacs.d/vendor` folder.

Next create a `tab.el` in the `.emacs/personal` folder.

[personal/tab.el](https://github.com/justinramel/prelude/blob/master/personal/tab.el)

```
(require 'smart-tab)
(require 'yasnippet)

(cons 'yas/hippie-try-expand 'hippie-expand-try-functions-list)

(setq smart-tab-using-hippie-expand t)
(global-smart-tab-mode t)

```

Here I am using cons to push YASnippets to the front of the hippie expand list, this means snippets are found before trying to auto-complete words.

As I said this is not perfect, I can't auto-complete in the middle of a snippet process for instance but it's not a bad start.
