# suckless
All the suckless essentials (mostly git modules).

## Install
```bash
sudo apt-get install autoconf build-essential xutils-dev
```

### Install on Debian distros (Kali, Debian, Ubuntu, etc)
For Debian based Linux distros you need to install `libxft-bgra` for the emojis to show.

#### For win-kex (Kali in Windows WSL)
After you install `dwn` you will need to modify: `/usr/lib/win-kex/xstartup`

Here is an article I wrote on the subject: [How to change Window Manager (GUI) for win-kex](https://jeannicolasboulay.medium.com/how-to-change-window-manager-gui-for-win-kex-7b6a749f423b)

#### Install libxft-bgra
You need to install `libxft-bgra` before `st` and `dwm`. If you want the emojs.

```bash
cd ./lib/libxft
# Make sure it is the right branch --> libXft-2.3.4-debian
git branch -a
# Install
sh autogen.sh --sysconfdir=/etc --prefix=/usr --mandir=/usr/share/man
```

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
- https://www.atlassian.com/git/tutorials/git-submodule (basic of git modules)
- https://stackoverflow.com/questions/29882960/changing-an-existing-submodules-branch (instructions on how to change submodules branch in git)
- https://gist.github.com/0xjac/85097472043b697ab57ba1b1c7530274 (upstream & forking instructions)
- https://github.com/ra-c/libxft-bgra-debian (a version of libxft-bgra that runs on debian (it contains a patch file))
