Please follow the installation instructions for **both** applications:

- [**Streamlink**](#streamlink) (Command Line Interface)  
- [**Streamlink Twitch GUI**](#streamlink-twitch-gui) (Graphical User Interface)

---

## Streamlink

[Streamlink][streamlink-install] has to be installed on your system in order to be able to launch streams from the GUI. **Please do this first!**

### Windows

Either download the Streamlink installer from the [Streamlink website][streamlink-windows], or install Streamlink via [python-pip][python-pip].

*Please note that the [Visual C++ Redistributable package][vc-redist] needs to be installed on systems using a Windows version prior to 10.*

### MacOS and Linux

Either install Streamlink via [python-pip][python-pip], or visit the [Streamlink website][streamlink-install] for a list of available packages.

*Please make sure to use a Python version greater than `2.7.6`.*

---

## Streamlink Twitch GUI

### Windows

*Requires at least Windows 7.*  
*Windows XP and Vista are not being supported anymore.*

#### Installer

A Windows installer is available on the [Github releases page][streamlink-twitch-gui-releases].  
Automated upgrades are being worked on.

*Please note that the [Visual C++ Redistributable package][vc-redist] needs to be installed on systems using a Windows version prior to 10.*

#### Chocolatey

[`choco install streamlink-twitch-gui`](https://chocolatey.org/packages/streamlink-twitch-gui)

### MacOS

#### Homebrew Cask (MacOS)

[`brew cask install streamlink-twitch-gui`](https://caskroom.github.io/)

### Linux

#### AUR (Arch Linux, Antergos, Manjaro, etc.)

[`pacaur -S streamlink-twitch-gui`](https://aur.archlinux.org/packages/streamlink-twitch-gui/)  
[`pacaur -S streamlink-twitch-gui-git`](https://aur.archlinux.org/packages/streamlink-twitch-gui-git/)

#### DEB (Debian, Ubuntu/*buntu, Mint, Elementary, etc.)

Being worked on. See [the progress here][deb-rpm-packages].

#### RPM (Fedora, OpenSuse, etc.)

Being worked on. See [the progress here][deb-rpm-packages].


### Custom installation

Archives with prebuilt binaries of the [latest release][streamlink-twitch-gui-releases] are available for Windows, MacOS and Linux on the releases page of the repository on Github. Download the archive that fits the architecture of your CPU and operating system.

#### Windows

Simply extract the archive to any folder and run `streamlink-twitch-gui.exe` or create a shortcut to the desktop, taskbar or startmenu.

#### MacOS

In order to have the application listed in the launchpad, extract the archive to `/Applications` or `$HOME/Applications`.

#### Linux

After extracting the archive (preferably to `/opt`), run `./add-menuitems.sh` once for creating menu shortcuts / application icons and run `./start.sh` for launching the application.

**Debian, Ubuntu, Mint, etc.**

Additional dependencies: `xdg-utils`.

**Fedora, etc.**

Additional dependencies: `xdg-utils`.


[streamlink-install]: https://streamlink.github.io/install.html "Streamlink installation"
[streamlink-windows]: https://streamlink.github.io/install.html#windows-binaries "Streamlink Windows binaries"
[streamlink-twitch-gui-releases]: https://github.com/streamlink/streamlink-twitch-gui/releases "Streamlink Twitch GUI releases"
[python-pip]: https://pip.pypa.io/en/stable/ "Python pip"
[vc-redist]: https://www.microsoft.com/en-us/download/details.aspx?id=48145 "Visual C++ Redistributable"
[deb-rpm-packages]: https://github.com/streamlink/streamlink-twitch-gui/pull/319
