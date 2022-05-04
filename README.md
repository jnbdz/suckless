# suckless
All the suckless essentials (mostly git modules).

## Install
```bash
sudo apt-get install autoconf build-essential xutils-dev
```

### Install on Debian distros (Kali, Debian, Ubuntu, etc)
For Debian based Linux distros you need to install `libxft-bgra` for the emojis to show.

#### win-kex (Kali in Windows WSL)
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

**Sources:**
- https://www.atlassian.com/git/tutorials/git-submodule
- https://stackoverflow.com/questions/29882960/changing-an-existing-submodules-branch
