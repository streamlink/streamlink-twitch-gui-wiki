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

  - #### Arch Linux, Antergos, Manjaro, etc. (AUR)

    [Stable][aur-streamlink-twitch-gui]

    ```bash
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui'
    cd streamlink-twitch-gui
    makepkg --install --syncdeps --cleanbuild
    ```

    [Development][aur-streamlink-twitch-gui-git]

    ```bash
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui-git'
    cd streamlink-twitch-gui-git
    makepkg --install --syncdeps --cleanbuild
    ```

  - #### Solus (EOPKG)

    [Stable][eopkg-streamlink-twitch-gui]

    ```bash
    sudo eopkg install streamlink-twitch-gui
    ```

  - #### Debian, Ubuntu/*buntu, Linux Mint, Elementary, etc. (DEB)

    No package+repository available yet due to build/license/traffic restrictions.  
    See the [TODO][todo-packages] list.  
    Help is very much appreciated.

  - #### Fedora, OpenSuse, etc. (RPM)

    No package+repository available yet due to build/license/traffic restrictions.  
    See the [TODO][todo-packages] list.  
    Help is very much appreciated.

  - #### Other packages

    Packages for other distros and package managers are welcome. Please open a new thread on the issue tracker if you want to help to create a new package. Thank you very much!

  - #### Archives

    This is a precise description of how to download the latest archive containing the prebuilt application from the Github releases page, how to extract it and how to set up application icons and shortcuts. You can also follow the procedure by performing the same tasks via your desktop environment's GUI, just read the comments above each command listed below.

    **Example on Ubuntu 18.04:**

    ```bash
    # Since this is not a regular installation via package management,
    # install- and runtime dependencies might need to be installed on
    # your system first in order to be able to follow this guide and to
    # be able to run Streamlink Twitch GUI. This depends on your distro
    # and the already installed packages. On Ubuntu 18.04, all necessary
    # packages should already be installed by default.

    # First, download the latest archive from the Github releases page:
    # https://github.com/streamlink/streamlink-twitch-gui/releases/latest
    # You can do this by using your web browser, curl, wget, etc.
    # Here, we're using curl and are downloading the file into the current
    # directory. Replace $VERSION with the latest version, eg. "v1.6.0".
    curl -JLO "https://github.com/streamlink/streamlink-twitch-gui/releases/download/$VERSION/streamlink-twitch-gui-$VERSION-linux64.tar.gz"

    # Make sure that /opt exists, where the archive will be extracted.
    # Any other path is fine, too, but you'll have to replace it in the
    # following commands as well. Using sudo may then not be required.
    sudo mkdir /opt

    # Extract the downloaded archive. Replace $VERSION again.
    sudo tar -xzvf "streamlink-twitch-gui-$VERSION-linux64.tar.gz" -C /opt

    # In order to install the app icons and to generate a menu shortcut,
    # simply run the also included "add-menuitem.sh" script. To uninstall
    # them later on, run the "remove-menuitem.sh" script.
    # Running the script(s) as root will perform the action system-wide.
    sudo /opt/streamlink-twitch-gui/add-menuitem.sh

    # You're done!
    # Now you can launch Streamlink Twitch GUI via the menu shortcut.
    # If you prefer starting it via the shell, create a soft link:
    sudo ln -s /opt/streamlink-twitch-gui/start.sh /usr/bin/streamlink-twitch-gui
    ```

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
[eopkg-streamlink-twitch-gui]: https://dev.solus-project.com/source/streamlink-twitch-gui/ "Streamlink Twitch GUI Solus package"
[todo-packages]: https://github.com/streamlink/streamlink-twitch-gui/blob/master/TODO.md#linux-packages
