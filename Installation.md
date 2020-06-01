Please follow the installation instructions for **both applications**:

**Streamlink Twitch GUI** requires **Streamlink** to be installed on your system in order to be able to launch streams.

- [**Streamlink**](#streamlink) (Command Line Interface)  
  - [Windows](#windows)
  - [macOS](#macos)
  - [Linux](#linux)
  - [Via Python PIP](#via-python-pip)
  - [Building from source](#building-from-source)
- [**Streamlink Twitch GUI**](#streamlink-twitch-gui) (Graphical User Interface)  
  - [Windows](#windows-1)
  - [macOS](#macos-1)
  - [Linux](#linux-1)
  - [Building from source](#building-from-source-1)


---


## Streamlink

See the [Streamlink website][streamlink-install] for a list of additional installation methods.

- ### Windows

  - #### Installer

    **Stable**  
    Download the installer of Streamlink's latest stable release from the [Github releases page][streamlink-releases].  
    *This is the preferred method.*

    **Development**  
    Download the installer of Streamlink's latest nightly build from the [Streamlink website][streamlink-windows].  
    *This may cause issues in cases where Streamlink has introduced changes which Streamlink Twitch GUI doesn't know about yet.*

    Please note that the [Visual C++ Redistributable package][vc-redist] needs to be installed on systems using a Windows version prior to 10.

  - #### Portable

    Download one of the portable versions from the [Streamlink website][streamlink-portable].  
    *These are non-official side projects and may cause issues in combination with Streamlink Twitch GUI.*

  - #### Packages

    [Chocolatey][chocolatey-streamlink] - *The package manager for Windows*

    ```bash
    choco install streamlink
    ```

  Other available options can be found on the [Streamlink website][streamlink-install].

- ### macOS

  - #### Packages

    [Homebrew][homebrew-streamlink] - *The missing package manager for macOS*

    ```bash
    brew install streamlink
    ```

- ### Linux

  - #### Packages

    Visit the [Streamlink website][streamlink-install] to see a list of available packages for your Linux distribution.

- ### Via Python PIP

  This requires an already installed Python environment on your system and Python's package manager `pip` needs to be available. Using pip may not be the ideal solution on each system, as installing Python packages globally may conflict with the system's native package manager. Installing Python packages locally may require an upgrade of the user's `PATH` environment variable.

  ```bash
  # Option 1: install globally (system-wide)
  sudo pip install --upgrade streamlink
  # Option 2: install locally (current user)
  pip install --user --upgrade streamlink
  # Option 3: install development version locally (current user)
  pip install --user --upgrade 'git+https://github.com/streamlink/streamlink.git@master'
  ```

- ### Building from source

  See the [Streamlink website][source-streamlink].


---


## Streamlink Twitch GUI

- ### Windows

  *Requires at least Windows 7.*  
  *Windows XP and Vista are not supported.*

  - #### Installer

    A Windows installer is available on the [Github releases page][streamlink-twitch-gui-releases].

    Please note that the [Visual C++ Redistributable package][vc-redist] needs to be installed on systems using a Windows version prior to 10.

  - #### Packages

    [Chocolatey][chocolatey-streamlink-twitch-gui] - *The package manager for Windows*

    ```bash
    choco install streamlink-twitch-gui
    ```

  - #### Archives

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to a folder of your choice. Then simply execute `streamlink-twitch-gui.exe` or create a shortcut to the desktop, taskbar or startmenu.

- ### macOS

  - #### Packages

    [Homebrew cask][homebrew-streamlink-twitch-gui] - *The missing package manager for macOS*

    ```bash
    brew cask install streamlink-twitch-gui
    ```

  - #### Archive

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to `/Applications` or `$HOME/Applications`, so that the app can be accessed from the launchpad.

- ### Linux

  - #### Arch Linux, Manjaro, etc. (AUR)

    [Stable][aur-streamlink-twitch-gui]

    ```bash
    # install via your AUR helper of choice, eg. yay
    yay -S streamlink-twitch-gui

    # install via makepkg
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui'
    cd streamlink-twitch-gui
    makepkg --install --syncdeps --cleanbuild
    ```

    [Development][aur-streamlink-twitch-gui-git]

    ```bash
    # install via your AUR helper of choice, eg. yay
    yay -S streamlink-twitch-gui-git

    # install via makepkg
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui-git'
    cd streamlink-twitch-gui-git
    makepkg --install --syncdeps --cleanbuild
    ```

  - #### Solus (EOPKG)

    [Stable][eopkg-streamlink-twitch-gui]

    ```bash
    sudo eopkg install streamlink-twitch-gui
    ```

  - #### Other packages

    Due to build- and license restrictions and/or traffic limitations, `deb` packages for Debian, Ubuntu/*buntu, Linux Mint, Elementary, etc. and `rpm` packages for Fedora, OpenSuse, etc. can't be created at the moment. An experiment with custom package repositories [was done in late 2016][custom-package-repo-experiment], but unfortunately it didn't work out properly.

    If you want to help with the creation of a package for your distro, or even better, a Flatpak, Snap or AppImage package, then please open a new thread on the issue tracker. Thank you very much!

  - #### Archives

    Regular archives (gzipped tarballs) of the latest release can be found on the [Github releases page][streamlink-twitch-gui-releases].

    Download the archive that is matching your system's architecture (eg. "linux64" for x86_64 systems) and extract it to any directory you want. After extracting, execute the included `add-menuitem.sh` shell script once, so that app icons and menu entries get installed (`remove-menuitem.sh` will remove them). This can be done as a regular user, or as root, so that app icons and menu entries get installed system-wide.

    Then simply run the `streamlink-twitch-gui` executable or use the newly added menu entry to launch the application.

- ### Building from source

  See the "Building and developing" section of the [contribution guidelines][source-streamlink-twitch-gui].


[streamlink-install]: https://streamlink.github.io/install.html "Streamlink installation"
[streamlink-windows]: https://streamlink.github.io/install.html#windows-binaries "Streamlink Windows binaries"
[streamlink-portable]: https://streamlink.github.io/install.html#windows-portable-version "Streamlink portable on Windows"
[streamlink-releases]: https://github.com/streamlink/streamlink/releases "Streamlink Windows installer"
[streamlink-twitch-gui-releases]: https://github.com/streamlink/streamlink-twitch-gui/releases "Streamlink Twitch GUI releases"
[vc-redist]: https://www.microsoft.com/en-us/download/details.aspx?id=48145 "Visual C++ Redistributable"
[pypi-streamlink]: https://pypi.org/project/streamlink/ "Streamlink Python package"
[source-streamlink]: https://streamlink.github.io/install.html#source-code "Building Streamlink"
[source-streamlink-twitch-gui]: https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#developing-and-building "Building Streamlink Twitch GUI"
[chocolatey-streamlink]: https://chocolatey.org/packages/streamlink "Streamlink chocolatey package"
[chocolatey-streamlink-twitch-gui]: https://chocolatey.org/packages/streamlink-twitch-gui "Streamlink Twitch GUI chocolatey package"
[homebrew-streamlink]: https://formulae.brew.sh/formula/streamlink "Streamlink homebrew package"
[homebrew-streamlink-twitch-gui]: https://github.com/Homebrew/homebrew-cask/blob/master/Casks/streamlink-twitch-gui.rb "Streamlink Twitch GUI homebrew cask"
[aur-streamlink-twitch-gui]: https://aur.archlinux.org/packages/streamlink-twitch-gui "Streamlink Twitch GUI AUR stable package"
[aur-streamlink-twitch-gui-git]: https://aur.archlinux.org/packages/streamlink-twitch-gui-git "Streamlink Twitch GUI AUR development package"
[eopkg-streamlink-twitch-gui]: https://dev.getsol.us/source/streamlink-twitch-gui/ "Streamlink Twitch GUI Solus package"
[custom-package-repo-experiment]: https://github.com/streamlink/streamlink-twitch-gui/pull/319
