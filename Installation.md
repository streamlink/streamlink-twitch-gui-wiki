## PLEASE NOTE

**Streamlink Twitch GUI** requires **Streamlink** to be installed on the system in order to be able to launch streams.

Please follow the install instructions for **both applications**.


---


## Streamlink

Check the [Streamlink install documentation][streamlink-install] for a detailed list of all available installation methods on the supported operating systems.


---


## Streamlink Twitch GUI

- ### Windows

  *Requires at least Windows 10.*  
  *Older versions of Windows are not supported.*

  - #### Installer

    A Windows installer is available on the [Github releases page][streamlink-twitch-gui-releases].

  - #### Packages

    [Chocolatey][chocolatey-streamlink-twitch-gui] - *The package manager for Windows*

    ```bash
    choco install streamlink-twitch-gui
    ```

    [Scoop][scoop-streamlink-twitch-gui] - *A command-line installer for Windows*

    ```bash
    scoop bucket add extras
    scoop install streamlink-twitch-gui
    ```

    [Winget][winget-streamlink-twitch-gui] - *The Windows package manager*

    ```bash
    winget install streamlink-twitch-gui
    ```

  - #### Archives

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to a folder of your choice. Then simply execute `streamlink-twitch-gui.exe` or create a shortcut to the desktop, taskbar or startmenu.

- ### macOS

  - #### Packages

    [Homebrew cask][homebrew-streamlink-twitch-gui] - *The missing package manager for macOS*

    ```bash
    brew install --cask streamlink-twitch-gui
    ```

  - #### Archive

    Download the archive from the [Github releases page][streamlink-twitch-gui-releases] and extract it to `/Applications` or `$HOME/Applications`, so that the app can be accessed from the launchpad.

- ### Linux

  - #### AppImage

    <details>
    <summary>What are AppImages?</summary>
    AppImages are portable apps which are independent of the distro and package management. No root permissons are required for installing and no files need to be manually extracted from a compressed tarball, just set the executable flag on the AppImage file and run it, either from the command line shell or graphical file browser.

    Note: Check out [AppImageLauncher][appimagelauncher], which automates the setup and system integration of AppImages. AppImageLauncher may also be available via your distro's package management.
    </details>

    Download the AppImage which matches your system's architecture from the [Github releases page][streamlink-twitch-gui-releases] and optionally compare checksums.

    ```bash
    # make AppImage file executable
    # note that AppImage release file names include the release version
    chmod +x ./streamlink-twitch-gui-v123.45.67-x86_64.AppImage
    # run the app
    ./streamlink-twitch-gui-v123.45.67-x86_64.AppImage
    ```

  - #### Arch Linux, Manjaro, etc. (AUR)

    [`streamlink-twitch-gui-bin`][aur-streamlink-twitch-gui-bin]

    ```bash
    # install via your AUR helper of choice, eg. yay
    yay -S streamlink-twitch-gui-bin

    # install via makepkg
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui-bin'
    cd streamlink-twitch-gui-bin
    makepkg --install --syncdeps --cleanbuild
    ```

    [`streamlink-twitch-gui-git`][aur-streamlink-twitch-gui-git]

    ```bash
    # install via your AUR helper of choice, eg. yay
    yay -S streamlink-twitch-gui-git

    # install via makepkg
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui-git'
    cd streamlink-twitch-gui-git
    makepkg --install --syncdeps --cleanbuild
    ```

    [`streamlink-twitch-gui`][aur-streamlink-twitch-gui]

    ```bash
    # install via your AUR helper of choice, eg. yay
    yay -S streamlink-twitch-gui

    # install via makepkg
    git clone 'https://aur.archlinux.org/streamlink-twitch-gui'
    cd streamlink-twitch-gui
    makepkg --install --syncdeps --cleanbuild
    ```

    A mirror repo with branches of all the AUR packages can be found [here][aur-mirror-repo] where issues and pull requests can be submitted.

  - #### NixOS

    [`streamlink-twitch-gui-bin`][nixos-streamlink-twitch-gui-bin]

    ```bash
    nix-env -iA nixos.streamlink-twitch-gui-bin
    ```

  - #### Solus (EOPKG)

    [`streamlink-twitch-gui`][eopkg-streamlink-twitch-gui]

    ```bash
    sudo eopkg install streamlink-twitch-gui
    ```

  - #### Other packages

    Due to build- and license restrictions and/or traffic limitations, `deb` packages for Debian, Ubuntu/*buntu, Linux Mint, Elementary, etc. and `rpm` packages for Fedora, OpenSuse, etc. can't be created at the moment. An experiment with custom package repositories [was done in late 2016][custom-package-repo-experiment], but unfortunately it didn't work out properly.

    If you want to help with the creation of a package for your distro, or even better, a Flatpak, Snap or AppImage package, then please open a new thread on the issue tracker. Thank you very much!

  - #### Archives

    Regular archives (gzipped tarballs) of the latest release can be found on the [Github releases page][streamlink-twitch-gui-releases].

    Download the archive that is matching your system's architecture (eg. "linux64" for x86_64 systems), optionally compare checksums and extract it to any directory you want. After extracting, execute the included `add-menuitem.sh` shell script once, so that app icons and menu entries get installed (`remove-menuitem.sh` will remove them). This can be done as a regular user, or as root, so that app icons and menu entries get installed system-wide.

    Then simply run the `streamlink-twitch-gui` executable or use the newly added menu entry to launch the application.

- ### Building from source

  See the "Building and developing" section of the [contribution guidelines][source-streamlink-twitch-gui].


[streamlink-install]: https://streamlink.github.io/install.html "Streamlink installation"
[streamlink-releases]: https://github.com/streamlink/streamlink/releases "Streamlink releases"
[streamlink-twitch-gui-releases]: https://github.com/streamlink/streamlink-twitch-gui/releases "Streamlink Twitch GUI releases"
[source-streamlink-twitch-gui]: https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#developing-and-building "Building Streamlink Twitch GUI"
[chocolatey-streamlink-twitch-gui]: https://chocolatey.org/packages/streamlink-twitch-gui "Streamlink Twitch GUI chocolatey package"
[scoop-streamlink-twitch-gui]: https://scoop.sh/#/apps?q=streamlink&s=0&d=1&o=true "Streamlink Twitch GUI Scoop package"
[winget-streamlink-twitch-gui]: https://github.com/microsoft/winget-pkgs/tree/master/manifests/s/Streamlink/Streamlink/TwitchGui "Streamlink Twitch GUI winget package"
[homebrew-streamlink-twitch-gui]: https://formulae.brew.sh/cask/streamlink-twitch-gui "Streamlink Twitch GUI homebrew cask"
[aur-streamlink-twitch-gui-bin]: https://aur.archlinux.org/packages/streamlink-twitch-gui-bin "Streamlink Twitch GUI AUR binary package"
[aur-streamlink-twitch-gui-git]: https://aur.archlinux.org/packages/streamlink-twitch-gui-git "Streamlink Twitch GUI AUR development package"
[aur-streamlink-twitch-gui]: https://aur.archlinux.org/packages/streamlink-twitch-gui "Streamlink Twitch GUI AUR source package"
[aur-mirror-repo]: https://github.com/streamlink/streamlink-twitch-gui-aur "Streamlink Twitch GUI AUR mirror repo"
[nixos-streamlink-twitch-gui-bin]: https://search.nixos.org/packages?show=streamlink-twitch-gui-bin&query=streamlink "Streamlink Twitch GUI NixOS binary package"
[eopkg-streamlink-twitch-gui]: https://github.com/getsolus/packages/tree/main/packages/s/streamlink-twitch-gui "Streamlink Twitch GUI Solus package"
[custom-package-repo-experiment]: https://github.com/streamlink/streamlink-twitch-gui/pull/319
[appimagelauncher]: https://github.com/TheAssassin/AppImageLauncher
