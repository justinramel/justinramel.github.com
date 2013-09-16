---
layout: post
title: "Vim to Emacs - Ace Jump Mode"
date: 2013-09-15 23:19
comments: true
categories: Emacs
---
One of the things I miss from Vim is the wonderful [Easy Motion](https://github.com/Lokaltog/vim-easymotion) which allows you to jump quickly to any word in the buffer.

Thankfully Emacs has a very similar package [Ace Jump Mode](http://www.emacswiki.org/emacs/AceJump).

## Setup
Using Prelude setup was simple, create a file in the personal folder and it will be auto loaded when Emacs starts.

```
(prelude-require-package 'ace-jump-mode)

(require 'ace-jump-mode)
(define-key global-map (kbd "C-c SPC") 'ace-jump-mode)
```

I'm using the `prelude-require-package` function to make sure the `ace-jump-mode` package is available just in case this is a new machine where the package has not been installed.

I then require the `ace-jump-mode` package and bind a short cut key to `C-c SPC`.

Now when I press Ctrl + c followed by Space Emacs asks for a `Head Char:` which will then highlight all words that begin with that Char. Pressing that char jumps straight to that Char.

A screen cast is worth a thousand words:

{% youtube UZkpmegySnc %}
