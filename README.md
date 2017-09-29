# Awesome Stuff

Random awesome hints, fixes and stuff. Also see [robotics-setup](https://github.com/ahundt/robotics_setup).

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


### iTerm2 Zsh Keyboard shortcuts

To be able to [skip to the next word with command left and command right](https://apple.stackexchange.com/a/263981/20386):


If you are using Zsh, like Oh My Zsh, in iTerm then go to: Preferences > Profiles > Keys sub-menu

Click the + sign to add a new command.

Add your shortcut such as command + left arrow then choose "Send Escape Sequence"
left: `[1;5D`
right: `[1;5C`


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

### [Find libraries if you have linking trouble](https://askubuntu.com/questions/32507/how-do-i-get-a-list-of-installed-files-from-a-package)

    dpkg-query -L ros-kinetic-opencv3

### How to find the versions of drivers you need

    sudo ubuntu-drivers devices
    
### [Get the display working with multiple nvidia GPUs](https://adler-j.github.io/2017/07/19/Dual-GPU-configuration-in-Ubuntu-1604-and-CUDA-80.html)

    sudo nvidia-xconfig -multigpu=on


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

[xonsh shell](http://xon.sh):

`source-bash eval "$(ssh-agent -s)" && ssh-add ~/.ssh/github_rsa`

Command line / Terminal
-----------------------

### Kill a process when `ctrl+c` doesn't work

`ctrl + \`

### "repair" broken/corrupted pdfs


```
pdf2ps file.pdf
ps2pdf file.ps
```

### Correct [python permission errors](http://stackoverflow.com/questions/21093002/error-could-not-create-usr-local-lib-python2-7-dist-packages-virtualenv-suppo)


    sudo chown -R $USER /usr/local/lib/python2.7

### [Make zsh your shell without root access](http://unix.stackexchange.com/questions/136423/making-zsh-default-shell-without-root-access)


```
export SHELL=`which zsh`
[ -z "$ZSH_VERSION" ] && exec "$SHELL" -l
```

