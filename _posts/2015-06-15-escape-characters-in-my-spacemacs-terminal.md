---
layout:     post
title:      Escape Characters In My Spacemacs Terminal Emulator
date:       2015-06-15 12:32:18
summary:    I was disappointed by the terminal emulator in Spaceemacs because every line started with chars that were not properly escaped. This is an emacs issue specific to Mac OS X.
categories: development
---

The solution is simple; just type the following in your terminal (adjust for
your current version of Emacs):

```
tic -o ~/.terminfo /usr/local/Cellar/emacs-mac/emacs-24.5-z-mac-5.8/share/emacs/24.5/etc/e/eterm-color.ti
```

This solution is a slight modification of the answer found on [Stack
Overflow](http://stackoverflow.com/questions/8918910/weird-character-zsh-in-emacs-terminal).

The reason this works is because emacs-mac, the installation of Emacs recommended
in the [Spacemacs Docs](https://github.com/syl20bnr/spacemacs#os-x) does not
include eterm-color terminfo.

Both my color theme and zsh-syntax-highlighting were producing the escape
characters. I tried using `term`, `ansi-term`, and `multi-term` and they all
produced the same characters. The worst was that every line started with `4m`.

With this simple one-liner, my Spacemacs terminal emulator now works as
expected.
