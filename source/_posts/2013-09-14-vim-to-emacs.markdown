---
layout: post
title: "Vim to Emacs"
date: 2013-09-14 12:54
comments: true
categories: Emacs
---
{% render_partial _partials/vim-to-emacs.markdown %}

## Why?
Mostly curiosity. As a long time Vim user I've heard lots of good and bad about this other ancient editor Emacs. As well as my curiosity I've rubbed up against a few rough edges lately mixing Vim and Tmux's modal modes and problems getting Vim plugin's working cross platform.

I decided to find out for myself, is Emacs is as good/bad as they say?

## Evil
I've tried Emacs before but quickly returned to Vim after becoming perplexed at the number of `Ctrl + x Ctrl + ?!?` keystrokes needed to do the simplest of actions. This time I'm trying the [Evil](http://www.emacswiki.org/emacs/Evil) package with gives Vim like editing within Emacs. The best of both worlds? Or too good to be true?

So far I'm very impressed with Evil, once this package was installed I was right at home. You really can't get way without learning some of the basic Emacs control keys but they are very small in number.

## Emacs Redux
Out of the box Emacs is not the most pleasant of experiences, just like Vim it is very raw until you tweak the config. Thankfully Emacs is ridiculously configurable you really can create an editor suited to your own personal tastes. Configuration is done via Emacs Lisp, a little overwhelming for beginners but I do look forward to learning the language. It's certainly looks a lot nicer than VIML!

I quickly realised hacking on my init.el conifg file with my limited knowledge was not the way to go. I eventually found the excellent [Emacs Redux](http://emacsredux.com/) blog and the [Prelude](https://github.com/bbatsov/prelude) configuration project. This project has allowed me to have a solid foundation as I find my feet in Emacs land.

## Initial Config
* [Evil](http://www.emacswiki.org/emacs/Evil)
* [Tomorrow Theme](https://github.com/chriskempson/tomorrow-theme)

I've also changed a few Prelude defaults which can be found in my [personal fork](https://github.com/justinramel/prelude).

## Conclusion
So far so good. I'm honestly surprised how quickly I've settled in with Emacs this time, there is lots here to like. I really don't feel like I'm deserting Vim, thanks to Evil all that Vim 'muscle memory' is coming along with me.
