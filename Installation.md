Please follow the installation instructions for both applications:

- [**Streamlink**](#streamlink) (Command Line Interface)  
- [**Streamlink Twitch GUI**](#streamlink-twitch-gui) (Graphical User Interface)

---

## Streamlink

[Streamlink][streamlink-install] has to be installed on your system in order to be able to launch streams from the GUI. Please do this first!

### Windows

Either download the Streamlink installer from the [Github releases page][streamlink-releases], or install Streamlink via [pip][pip].

### MacOS and Linux

Either install Streamlink via [pip][pip], or visit the [Streamlink website][streamlink-install] for a list of available packages. Please make sure to use a Python version greater than `2.7.6`.

---

## Streamlink Twitch GUI

### Windows installer

An installer on Windows is available.  
Automated upgrades are being worked on.

### Packages

*Please note:*  
*Not all packages have been updated yet after the application's name change.*

#### Chocolatey (Windows)

[`choco install streamlink-twitch-gui`](https://chocolatey.org/packages/streamlink-twitch-gui)

#### AUR (Arch Linux, Antergos, Manjaro, etc.)

[`yaourt -S streamlink-twitch-gui`](https://aur.archlinux.org/packages/streamlink-twitch-gui/)  
[`yaourt -S streamlink-twitch-gui-git`](https://aur.archlinux.org/packages/streamlink-twitch-gui-git/)

#### DEB (Debian, Ubuntu/*buntu, Mint, Elementary, etc.)

Being worked on. See [the progress here][deb-rpm-packages].

#### RPM (Fedora, OpenSuse, etc.)

Being worked on. See [the progress here][deb-rpm-packages].

#### Homebrew Cask (MacOS)

[`brew cask install streamlink-twitch-gui`](https://caskroom.github.io/)


### Custom installation

Archives with prebuilt binaries of the [latest release][streamlink-twitch-gui-releases] are available for Windows, MacOS and Linux on the releases page of the repository on Github. Download the archive that fits the architecture of your CPU and operating system.

#### Windows

Simply extract the archive to any folder and run `streamlink-twitch-gui.exe` or create a shortcut to the desktop, taskbar or startmenu.

#### MacOS

In order to have the application listed in the launchpad, extract the archive to `/Applications` or `$HOME/Applications`.

#### Linux

After extracting the archive (preferably to `/opt`), run `add-menuitems.sh` once for creating menu shortcuts / application icons and run `start.sh` for launching the application.

**Debian, Ubuntu, Mint, etc.**

Additional dependencies: `xdg-utils`.

**Fedora, etc.**

Additional dependencies: `xdg-utils`.


[streamlink-install]: https://streamlink.github.io/install.html "Streamlink installation"
[streamlink-releases]: https://github.com/streamlink/streamlink/releases "Streamlink releases"
[streamlink-twitch-gui-releases]: https://github.com/streamlink/streamlink-twitch-gui/releases "Streamlink Twitch GUI releases"
[pip]: https://pip.pypa.io/en/stable/ "Python pip"
[deb-rpm-packages]: https://github.com/streamlink/streamlink-twitch-gui/pull/319
