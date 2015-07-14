## Default player

By default, Livestreamer will try to open the player defined in your [configuration file](http://docs.livestreamer.io/en/latest/cli.html#configuration-file). If you didn't change this file, the player will most likely be [VideoLAN Client (VLC)](https://www.videolan.org/).  
If VLC is not installed on your machine or was installed in a different folder other than the default one, you will need to choose a player in the GUI.

## Player configurations

Players can be started with custom parameters. This is useful if you'd like to control the player behavior or change the title of the window, etc. Make sure to enable the `advanced mode` at the top of the settings menu to be able to set player specific arguments. Also, please read the [`--player-args`](http://docs.livestreamer.io/en/latest/cli.html#cmdoption--player-args) parameter documentation and **don't forget to set the `{filename}` variable**.  
*Custom player parameters do only work if a custom player is set.*


### [VideoLAN Client](https://www.videolan.org/)
*VLC is a free and open source cross-platform multimedia player.*

- **Close the player window after playback** (see [#86](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/86))  
  `--play-and-exit`

- **Prevent single instance mode**  
  `--no-one-instance`  
  With the default settings of VLC, you're unable to watch multiple streams at once. Either disable *single instance* mode in the VLC settings, or use this parameter.

- **Custom player window title**  
  `--meta-title "{name} - {game} - {status}"`  
  See the dropdown in the GUI settings (blue button) for all available variables and make sure to use quotation marks.

- **Minimal UI**  
  `--qt-minimal-view`  
  Can also be toggled by pressing Ctrl+H.


### [MPV](http://mpv.io/)
*A free, open source, and cross-platform media player.*

- **Custom player window title**  
  `--title "{name} - {game} - {status}"`  
  See the dropdown in the GUI settings (blue button) for all available variables and make sure to use quotation marks.

- **No additional stream caching**  
  `--no-cache`  
  Livestreamer does all the caching (unless `--player-passthrough` is set to HLS), so we can reduce the stream delay.


### [Media Player Classic - Home Cinema](https://mpc-hc.org/)
*MPC-HC is an extremely light-weight, open source media player for Windows.*

- **Prevent single instance mode**  
  `/new`  
  Either enable *multi window mode* in the MPC settings, or use this parameter to be able to watch multiple streams at once.

- **Close the player window after playback** (see [#86](https://github.com/bastimeyer/livestreamer-twitch-gui/issues/86))  
  `/play /close`