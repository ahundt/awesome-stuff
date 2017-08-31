# Awesome Stuff

Random awesome stuff

Awesome Lists
-------------

- [sindresorhus/awesome](https://github.com/sindresorhus/awesome) - A curated list of awesome lists on every topic, with particular detail for software, math and machine learning topics.
- [awesome-robotics](https://github.com/ahundt/awesome-robotics) - Awesome robotics related stuff.
- [awesome-tensorflow](https://github.com/jtoy/awesome-tensorflow) - Awesome TensorFlow experiments, libraries, and projects.

MacOS
-----

- [mac-setup](http://sourabhbajaj.com/mac-setup/) - Recommended tools and a how-to for installing a Development environment on Mac OS X aka MacOS [mac-setup github](https://github.com/sb2nov/mac-setup).

### Screenshots

**copy for pasting**

- Command+Control+Shift+3 - capture all screens
- Command+Control+Shift+4 - select bounding box
- Command+Control+Shift+4 the spacebar - select a window

**save to desktop**

- Command+Shift+3 - capture all screens
- Command+Shift+4 - select bounding box
- Command+Shift+4 then spacebar - select a window


**set screenshot format**

```
defaults write com.apple.screencapture type png
```

Options are png, jpg, gif, tiff, jpg

### Sourcetree

[Sourcetree](https://www.sourcetreeapp.com/) is a [Git](https://git-scm.com/) application for Windows + Mac

[fix `stree` command line utility](https://jira.atlassian.com/browse/SRCTREE-3172)

```
alias stree='/Applications/SourceTree.app/Contents/Resources/stree'
```


Linux
-----

### OpenGL Crashing on Command Line Launch

OpenGL crashed you need to specify the display on which to run the program as follows: 

`DISPLAY=:0.0; sudo ./vrep.sh`

Check your specific machine (or google) for what display variable to use.

Python
------

- [breathe](https://github.com/michaeljones/breathe) - C++ ReStructuredText and Sphinx bridge to Doxygen


Git
---

Global .gitignore:

`git config --global core.excludesfile ~/.gitignore`

ssh
---

Load and authorize your ssh key (such as for github):

`eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa`

See a `WARNING: UNPROTECTED PRIVATE KEY FILE!` perimssions error on you ssh key?

`chmod 600 ~/.ssh/id_rsa`
