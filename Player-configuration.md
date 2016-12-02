## Default player

By default, Streamlink Twitch GUI uses the player which is defined in Streamlink's [config file][config-file]. If this file has not been changed, then [VideoLAN Client (VLC)][player-vlc] and its default configuration will be used.

This default configuration doesn't work very well with Streamlink Twitch GUI, though, and can cause issues when watching multiple streams at once. In order to avoid this, one of the available player presets should be used or custom parameters be set.


## Player presets

Using player presets is an easy way of automatically applying the required player settings for having the best possible viewing experience. Presets are available for multiple players on all operating systems and include a list of known player executable filenames and install locations, so that everything will work automatically for most users.

All presets can be individually configured and extended with custom player paths and parameters.


## Custom player parameters

Custom player parameters can be set if a player preset has been selected or if a custom player path has been set while not using a preset.

Streamlink's `{filename}` variable will automatically be appended to the parameters string if it is missing, which should be fine in most cases (see the [`--player-args`][player-args-param] Streamlink parameter documentation).

Several variables related to the stream being watched are available.  
**Please make sure to wrap variables in quotation marks (single or double).**  
If used incorrectly, Streamlink Twitch GUI will escape every character, which will not be interpreted correctly by every player.

Correct usage:  
`--paramA '{varA}' --paramB "{varB1} {varB2}" "--paramC={varC}"`

#### Parameters

- **{channel}**  
  The streamer's channel name
- **{status}**  
  The title of the broadcast
- **{game}**  
  Name of the game being played
- **{delay}**  
  Stream delay in seconds
- **{online}**  
  Timestamp of the start of the broadcast
- **{viewers}**  
  Number of viewers
- **{views}**  
  Overall channel views


## Player preset configuration

### [VideoLAN Client][player-vlc]
*VLC is a free and open source cross-platform multimedia player.*

- **Prevent single instance mode**  
  `--no-one-instance`  
  With the default settings of VLC, you're unable to watch multiple streams at once. Either disable *single instance* mode in the VLC settings, or use this parameter.

- **Close the player window after playback**  
  `--play-and-exit`  
  In its default configuration, VLC will ignore signals sent by Streamlink to close it.

- **Custom player window title**  
  `--meta-title "{name} - {game} - {status}"`  
  Set a custom player title.

- **Minimal UI**  
  `--qt-minimal-view`  
  Can also be toggled by pressing Ctrl+H.


### [MPV][player-mpv]
*A free, open source, and cross-platform media player.*

- **Close player**  
  `--keep-open=no`  
  Prevents stacking up empty player windows.

- **Custom player window title**  
  `--title "{name} - {game} - {status}"`  
  Set a custom player title.

- **Minimal UI**  
  `--no-border`  
  Removes decorations from the player window.

- **Fix potential issue with "Audio only" streams**  
  `--force-window`  
  If you're using the `--player-passthrough=HLS` Streamlink parameter, you need to set this player parameter as well, or else you'll need to kill the MPV process by yourself, since Streamlink won't do it when closing the stream via the GUI.

- **Seeking**  
  `--force-seekable=yes --hr-seek=yes --hr-seek-framedrop=yes`  
  Enables jumping forwards/backwards in the stream cache.

- **No additional stream caching**  
  `--no-cache`  
  Speed up stream launch time.


### [Media Player Classic - Home Cinema][player-mpc-hc]
*MPC-HC is an extremely light-weight, open source media player for Windows.*

- **Prevent single instance mode**  
  `/new`  
  Either enable *multi window mode* in the MPC settings, or use this parameter to be able to watch multiple streams at once.

- **Close the player window after playback**  
  `/play /close`  
  Prevents stacking up empty player windows.


[config-file]: https://streamlink.github.io/en/latest/cli.html#configuration-file "Streamlink config file"
[player-args-param]: https://streamlink.github.io/cli.html#cmdoption-a "--player-args parameter"
[player-vlc]: https://www.videolan.org/ "VideoLAN client"
[player-mpv]: http://mpv.io/ "MPV"
[player-mpc-hc]: https://mpc-hc.org/ "Media Player Classic - Home Cinema"
