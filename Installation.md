## 1. Install Livestreamer

[Livestreamer](http://docs.livestreamer.io/install.html) has to be installed on your system in order to be able to launch streams. Please do this first!

**Windows**  
*Don't* install Livestreamer via [pip](https://pip.pypa.io/en/stable/), download the installer from the [Livestreamer releases page](https://github.com/chrippa/livestreamer/releases) instead.

**Linux**  
If you are using the Debian package of Livestreamer, please make sure that at least version `1.12.2` is installed, or else you will be seeing [this error message](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/78).  

*Gnome desktop environment*  
Please make sure that the `wmctrl` package is installed on your system to be able to get rid of the "Unknown" application name bug in the panel. See [#136](https://github.com/bastimeyer/livestreamer-twitch-gui/pull/136).

**OSX / Linux**  
OSX and many Linux distributions come with Python being preinstalled. Since early 2015, Livestreamer and its libraries require a Python version greater than `2.7.6`. See issue [#69](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/69) / [#90](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/90) if you're getting the `InsecurePlatformWarning: A true SSLContext object is not available` message.


## 2. Download the GUI

Archives of the [latest release](https://github.com/bastimeyer/livestreamer-twitch-gui/releases) are available for Windows, OSX and Linux. Download the archive that fits the architecture of your CPU and operating system. If you don't know, choose the `x32` one.

**Windows**  
A [chocolatey package](https://chocolatey.org/packages/livestreamer-twitch-gui) is available, too. See [#54](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/54).

**Linux**  
Packages are currently only available for [Arch Linux](https://aur.archlinux.org/packages/livestreamer-twitch-gui/). See [#58](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/58).

If you want to create and maintain a package that is not yet available for your package manager, you're very welcome to do so. Please open an issue ticket and let me know. Thank you!


## 3. Extract the archive

An installation is not required. Just extract the contents of the archive to a directory of your choice.

**OSX**  
In order to have the application listed in the launchpad, extract the archive to `/Applications` or `$HOME/Applications`.

**Linux**  
Extract the archive to `/opt`.


## 4. Launch the GUI

**Windows**  
Just start `livestreamer-twitch-gui.exe` or create a shortcut to your desktop, taskbar or startmenu.

**OSX**  
Launch `Livestreamer Twitch GUI.app`

**Linux**  
Simply run `start.sh`. There are also `add-menuitem.sh` and `remove-menuitem.sh` available for creating/removing menu shortcuts and application icons.