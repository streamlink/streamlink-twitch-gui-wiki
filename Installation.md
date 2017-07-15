Please follow the installation instructions for **both applications**:

**Streamlink Twitch GUI** requires **Streamlink** to be installed on your system in order to be able to launch streams.

- [**Streamlink**](#streamlink) (Command Line Interface)  
  - [Windows](#windows)
  - [MacOS](#macos)
  - [Linux](#linux)
- [**Streamlink Twitch GUI**](#streamlink-twitch-gui) (Graphical User Interface)  
  - [Windows](#windows-1)
  - [MacOS](#macos-1)
  - [Linux](#linux-1)

---

## Streamlink

- ### Windows

  You have a couple of options of installing Streamlink on Windows:

  - #### Streamlink installer (stable)

    Download the installer of Streamlink's latest stable release from the [Github releases page][streamlink-releases]. **(preferred method)**

  - #### Streamlink installer (development)

    Download the installer of Streamlink's latest nightly build from the [Streamlink website][streamlink-windows].

  - #### Streamlink portable

    Download the portable version from the [Streamlink website][streamlink-portable].

  - #### Chocolatey

    Install Streamlink via the [Chocolatey package manager][chocolatey]:  
    [`choco install streamlink`][chocolatey-streamlink]  
    
    *Please note:* The Streamlink Twitch GUI choco package already includes Streamlink as a dependency. See [below](#chocolatey-1).

  Other available options can be found on the [Streamlink website][streamlink-install].

  *Please note that when using the installers, [Visual C++ Redistributable package][vc-redist] needs to be installed first on systems using a Windows version prior to 10.*

- ### MacOS

  The simplest way of installing Streamlink is installing the Streamlink Twitch GUI homebrew cask. See [below](#homebrew-cask).  
  Other available options can be found on the [Streamlink website][streamlink-install].

- ### Linux

  Either install Streamlink via [python-pip][python-pip], or visit the [Streamlink website][streamlink-install] for a list of available packages.

  *Please make sure to use a Python version greater than `2.7.6`.*

---

## Streamlink Twitch GUI

- ### Windows

  *Requires at least Windows 7.*  
  *Windows XP and Vista are not supported.*

  - #### Installer

    A Windows installer is available on the [Github releases page][streamlink-twitch-gui-releases].  
    Automated upgrades are being worked on.

    *Please note that the [Visual C++ Redistributable package][vc-redist] needs to be installed on systems using a Windows version prior to 10.*

  - #### Chocolatey

    [`choco install streamlink-twitch-gui`](https://chocolatey.org/packages/streamlink-twitch-gui)

  - #### Custom installation

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to a folder of your choice. Then run `streamlink-twitch-gui.exe` or create a shortcut to the desktop, taskbar or startmenu.

- ### MacOS

  - #### Homebrew cask

    [`brew cask install streamlink-twitch-gui`](https://caskroom.github.io/)

  - #### Custom installation

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to `/Applications` or `$HOME/Applications`, so that the app can be accessed from the launchpad.

- ### Linux

  - #### AUR (Arch Linux, Antergos, Manjaro, etc.)

    [`pacaur -S streamlink-twitch-gui`](https://aur.archlinux.org/packages/streamlink-twitch-gui/)  
    [`pacaur -S streamlink-twitch-gui-git`](https://aur.archlinux.org/packages/streamlink-twitch-gui-git/)

  - #### DEB (Debian, Ubuntu/*buntu, Mint, Elementary, etc.)

    Being worked on. See [the progress here][deb-rpm-packages].  
    Help is very much appreciated.

  - #### RPM (Fedora, OpenSuse, etc.)

    Being worked on. See [the progress here][deb-rpm-packages].  
    Help is very much appreciated.

  - #### Other packages

    Packages for other distros and package managers are welcome and help is very much appreciated. Please open a new issue thread if you want to help to create a new package.

  - #### Custom installation

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to a folder of your choice (preferably to `/opt`). From the path of the application folder, execute the `add-menuitem.sh` bash script once for creating application icons and menu shortcuts (run as root to create those globally). Then run the `start.sh` bash script for launching the application. Depending on your distribution, the `xdg-utils` package may need to be installed first in order to create icons and shortcuts.

    Example on Ubuntu:  
    ```bash
    # download and extract the archive
    # replace ARCHIVE_DOWNLOAD_URL with the actual URL
    wget -O /tmp/streamlink-twitch-gui.tar.gz ARCHIVE_DOWNLOAD_URL
    # extract to /opt
    sudo tar -xzvf /tmp/streamlink-twitch-gui.tar.gz -C /opt

    # create icons and menu shortcut
    # install the xdg-utils dependency first
    sudo apt install xdg-utils
    # then globally create icons and menu shortcut
    sudo /opt/streamlink-twitch-gui/add-menuitem.sh

    # now either use the menu shortcut to start it, or
    # create a link to the start script for quick shell access (optional)
    sudo ln -s /opt/streamlink-twitch-gui/start.sh /usr/bin/streamlink-twitch-gui
    ```


[streamlink-install]: https://streamlink.github.io/install.html "Streamlink installation"
[streamlink-windows]: https://streamlink.github.io/install.html#windows-binaries "Streamlink Windows binaries"
[streamlink-portable]: https://streamlink.github.io/install.html#windows-portable-version "Streamlink portable on Windows"
[streamlink-releases]: https://github.com/streamlink/streamlink/releases "Streamlink Windows installer"
[streamlink-twitch-gui-releases]: https://github.com/streamlink/streamlink-twitch-gui/releases "Streamlink Twitch GUI releases"
[chocolatey]: https://chocolatey.org/ "Chocolatey package manager"
[chocolatey-streamlink]: https://chocolatey.org/packages/streamlink "Streamlink chocolatey package"
[chocolatey-streamlink-twitch-gui]: https://chocolatey.org/packages/streamlink-twitch-gui "Streamlink Twitch GUI chocolatey package"
[python-pip]: https://pip.pypa.io/en/stable/ "Python pip"
[vc-redist]: https://www.microsoft.com/en-us/download/details.aspx?id=48145 "Visual C++ Redistributable"
[deb-rpm-packages]: https://github.com/streamlink/streamlink-twitch-gui/pull/319
