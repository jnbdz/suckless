# suckless
All the suckless essentials (mostly git modules).

## Install
```bash
sudo apt-get install autoconf build-essential xutils-dev libxft-dev libxft2 libxinerama-dev libx11-xcb-dev libxcb-res0-dev fonts-linuxlibertine fonts-inconsolata fonts-symbola ttf-ancient-fonts-symbola fonts-noto
```

### Install the needed fonts
```bash
# 1. Download the latest version
wget https://github.com/eosrei/twemoji-color-font/releases/download/v13.1.0/TwitterColorEmoji-SVGinOT-Linux-13.1.0.tar.gz
# 2. Uncompress the file
tar zxf TwitterColorEmoji-SVGinOT-Linux-13.1.0.tar.gz
# 3. Run the installer
cd TwitterColorEmoji-SVGinOT-Linux-13.1.0
./install.sh
```
**Source:** https://github.com/eosrei/twemoji-color-font

```bash
# 1. Download the latest version
wget https://github.com/eosrei/emojione-color-font/releases/download/v1.4/EmojiOneColor-SVGinOT-Linux-1.4.tar.gz
# 2. Uncompress the file
tar zxf EmojiOneColor-SVGinOT-Linux-1.4.tar.gz
# 3. Run the installer
cd EmojiOneColor-SVGinOT-Linux-1.4
./install.sh
```
You might also need: https://raw.githubusercontent.com/LukeSmithxyz/voidrice/master/.config/fontconfig/fonts.conf

### Reload fonts in Debian
```bash
dpkg-reconfigure fontconfig fontconfig-config
```

### Install on Debian distros (Kali, Debian, Ubuntu, etc)
For Debian based Linux distros you need to install `libxft-bgra` for the emojis to show.

#### For win-kex (Kali in Windows WSL)
After you install `dwn` you will need to modify: `/usr/lib/win-kex/xstartup`

Here is an article I wrote on the subject: [How to change Window Manager (GUI) for win-kex](https://jeannicolasboulay.medium.com/how-to-change-window-manager-gui-for-win-kex-7b6a749f423b)

#### Install libxft-bgra
You might need to install it outside of the package manager. If the package manager has `libxft-dev` `libxft2` than you are golden!

You need to install `libxft-bgra` before `st` and `dwm`. If you want the emojs.

```bash
cd ./lib/libxft
# Make sure it is the right branch --> libXft-2.3.4-debian
git branch -a
# Install
sh autogen.sh --sysconfdir=/etc --prefix=/usr --mandir=/usr/share/man
```
### Install `dwm`
Inside the dwm source: 
```bash
sudo make install
```
### Install `st`
Same as `dwm`.

## Git
### Add module
```bash
git submodule add [url]
git add [...]
```
### Change branch for the module
```bash
git checkout -t [branch]
git add [add again the dir of the module]
git commit [...]
git push
```
Don't forget to update where you have clone the repo: 
```bash
git submodule update --recursive
```

### Add upstream
If you are working on the lib `libxft-bgra` you need to do this step.
```bash
git remote add upstream git@gitlab.freedesktop.org:xorg/lib/libxft.git 
git remote set-url --push upstream DISABLE
```
Then to verify that evrything was added correctly for the upstream: 
`git remote -v`

This is what you should see: 
```bash
origin  git@github.com:jnbdz/libxft.git (fetch)
origin  git@github.com:jnbdz/libxft.git (push)
upstream        git@gitlab.freedesktop.org:xorg/lib/libxft.git (fetch)
upstream        DISABLE (push)
```
To pull changes from the upstream (verify that you are in the right branch first):
```bash
git fetch upstream
git rebase upstream/master
```

**Sources:**
- https://gitlab.freedesktop.org/xorg/lib/libxft/ (repo page for libxft)
- https://www.atlassian.com/git/tutorials/git-submodule (basic of git modules)
- https://stackoverflow.com/questions/29882960/changing-an-existing-submodules-branch (instructions on how to change submodules branch in git)
- https://gist.github.com/0xjac/85097472043b697ab57ba1b1c7530274 (upstream & forking instructions)
- https://github.com/ra-c/libxft-bgra-debian (a version of libxft-bgra that runs on debian (it contains a patch file))
