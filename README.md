# Awesome Stuff

Random awesome hints, fixes and stuff. Also see [robotics-setup](https://github.com/ahundt/robotics_setup).

Awesome Lists
-------------

- [sindresorhus/awesome](https://github.com/sindresorhus/awesome) - A curated list of awesome lists on every topic, with particular detail for software, math and machine learning topics.
- [awesome-robotics](https://github.com/ahundt/awesome-robotics) - Awesome robotics related stuff.
- [awesome-tensorflow](https://github.com/jtoy/awesome-tensorflow) - Awesome TensorFlow experiments, libraries, and projects.
- [linux tips](https://github.com/shundhammer/huha-linux-tips/blob/master/doc/ubuntu-tips.md) - decent utilities and problem solving for ubuntu and linux (though not all suggestions seem secure)

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

### View user manual aka `man` files as a PDF in Preview

```
man -t command | open -f -a /Applications/Preview.app
```


Linux
-----

### OpenGL Crashing on Command Line Launch

OpenGL crashed you need to specify the display on which to run the program as follows: 

`DISPLAY=:0.0; sudo ./vrep.sh`

Check your specific machine (or google) for what display variable to use.

### [List your installed Ubuntu repositories](https://stackoverflow.com/a/12739281/99379)

    apt-cache policy |grep http |awk '{print $2 $3}' |sort -u

### [Search ubuntu packages on command line](https://askubuntu.com/a/160899/333984)

    apt-cache search keyword
 
To list all packages:

   apt-cache search .


### [Find libraries if you have linking trouble](https://askubuntu.com/questions/32507/how-do-i-get-a-list-of-installed-files-from-a-package)

    dpkg-query -L ros-kinetic-opencv3

### How to find the versions of drivers you need

    sudo ubuntu-drivers devices
    
### View your disk io

    sudo iotop -aoP
    
### View your disk usage

[QDirStat](https://github.com/shundhammer/qdirstat) is an excellent utility for plotting the files and folders that take up the most disk space on your machine.

    sudo add-apt-repository ppa:nathan-renniewaldock/qdirstat
    sudo apt-get install qdirstat
    
### [Get the display working with multiple nvidia GPUs](https://adler-j.github.io/2017/07/19/Dual-GPU-configuration-in-Ubuntu-1604-and-CUDA-80.html)

There are a lot of steps for this so follow the link above if the instructions below aren't clear.

    # figure out the pci bus slot of the device you want to display on (0, 1, 2 etc)
    nvidia-smi -a

look for a line like the following for the device you want to display on:

    PCI
        Bus                         : 0x03    

create a new gpu config file and edit it:

    sudo nvidia-xconfig -multigpu=on
    sudo vim /etc/X11/xorg.conf
    
Update xorg.conf "Device" section to look like the following, replacing the "2" below with the value you found in `nvidia-smi -a`:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:2:0:0"
EndSection
```

Save and exit then restart the computer.

    sudo reboot now


### Auto mounting drives at startup

[Adapted easy instructions](https://askubuntu.com/a/848542):

1. Open `Disks` Ubuntu application
2. Select the partition
3. click the "settings" cog wheel
4. click `Edit Mount Options`
5. change settings to mount at startup

More manual terminal instructions:

- `/etc/fstab` - https://help.ubuntu.com/community/Fstab
- [ntfs](https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions?noredirect=1&lq=1)

### [Ubuntu equivalent to MacOS quick look](http://www.omgubuntu.co.uk/2016/09/gnome-sushi-mac-quick-look-nautilus)

    sudo apt-get install gnome-sushi

Python
------

[pip install a local package folder](https://stackoverflow.com/a/24000174/99379) with pip such that changes are immediately available in the package.

    pip install -e . --user --upgrade

- [breathe](https://github.com/michaeljones/breathe) - C++ ReStructuredText and Sphinx bridge to Doxygen

- [py-spy](https://github.com/benfred/py-spy) - Sampling based profiling of python code from a separate process. View with [speedscope.app](https://www.speedscope.app) and follow the [importing form py-spy](https://github.com/jlfwong/speedscope/wiki/Importing-from-py-spy-(python)) instructions below.

```bash
    py-spy --record $PID --format speedscope -o profile.speedscope.json
```

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

### Attribution of Pair programming with git

https://github.com/A-Helberg/pair-up

### Create a torrent

[webtorrent desktop](https://webtorrent.io/desktop/)
[browser torrent](https://instant.io/)

First [install npm (node package manager) and then webtorrent](https://nodejs.org/en/download/package-manager/):

```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
npm install webtorrent webtorrent-cli webtorrent-hybrid -g
```
Then you can create your torrent:

`webtorrent create /path/to/file/or/folder/to/share/ -o /path/to/file/or/folder/to/share.torrent`

And seed it for others to download:

`webtorrent seed /path/to/file/or/folder/to/share.torrent`

### Copy files with progress bar

`rsync -ah --info=progress2 /copy/from/here /copy/to/here`

### See all locations of a specific filename

`whereis`

example: `whereis cmake`

To see the current default instead use `which`, ie `which cmake`.

### Compress a PDF

On macOS open the pdf with the "ColorSync Utility".

### Prepping a latex paper for submission to [ArXiV.org](arxiv.org) with bibtex

`pdflatex main.tex --shell-escape && bibtex main && pdflatex main.tex && bibtex main && rm -rf main.pdf && cp main.bbl sample.bbl`
