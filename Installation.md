*Please notice the difference between __Livestreamer__ and __Livestreamer Twitch GUI__*  
Below you can find instructions for both applications.

## Livestreamer

[Livestreamer](http://docs.livestreamer.io/install.html) has to be installed on your system in order to be able to launch streams. Please do this first!

### Windows

*Don't install Livestreamer via [`pip`](https://pip.pypa.io/en/stable/)*, download the **installer** from the [Livestreamer releases page](https://github.com/chrippa/livestreamer/releases) instead. The installer adds a local python environment for livestreamer and also adds the installation directory to your system's `PATH` environment variable, so the GUI is able to automatically find it. There are also some issues on Windows when using Livestreamer via `pip`.

### Linux

#### Debian, Ubuntu, Mint

If you are using the Debian package of Livestreamer, please make sure that at least version `1.12.2` is installed, or else you will be seeing [this error message](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/78).

### OSX and Linux

OSX and many Linux distributions come with Python being preinstalled. Since early 2015, Livestreamer and its libraries require a Python version greater than `2.7.6`. See issue [#69](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/69) / [#90](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/90) if you're getting the `InsecurePlatformWarning: A true SSLContext object is not available` message.

---

## Livestreamer Twitch GUI

Archives with prebuilt binaries of the [latest release](https://github.com/bastimeyer/livestreamer-twitch-gui/releases) are available for Windows, OSX and Linux on the releases page of the repository on Github. Download the archive that fits the architecture of your CPU and operating system. If you don't know, choose the `x32` one, although you will most likely be using the x64 architecture.

### Windows

Simply extract the archive to a folder of your choice and run `livestreamer-twitch-gui.exe` or create a shortcut to your desktop, taskbar or startmenu.

#### Chocolatey

See the chocolatey package [`livestreamer-twitch-gui`](https://chocolatey.org/packages/livestreamer-twitch-gui).

### Linux

Sadly, there are no `deb` or `rpm` packages available yet. This has different reasons and will hopefully be resolved soon.  
If you want to help with this issue or want to create and maintain a package that is not yet available for your package manager, please open an issue ticket and let me know. Your help will be very much appreciated!

#### Arch

See the AUR package [`livestreamer-twitch-gui`](https://aur.archlinux.org/packages/livestreamer-twitch-gui/).

#### Debian, Ubuntu, Mint

Please make sure to install the `x11-utils` and `xdg-utils` packages.  
After extracting the archive (preferably to `/opt`), run `add-menuitems.sh` once for creating menu shortcuts and application icons and `start.sh` for launching the application.

#### Fedora

Please make sure to install the `xorg-x11-utils` and `xdg-utils` packages.  
After extracting the archive (preferably to `/opt`), run `add-menuitems.sh` once for creating menu shortcuts and application icons and `start.sh` for launching the application.

### OSX

In order to have the application listed in the launchpad, extract the archive to `/Applications` or `$HOME/Applications`.