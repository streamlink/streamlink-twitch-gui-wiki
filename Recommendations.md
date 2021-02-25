Since I've been getting a lot of questions regarding the best possible viewing experience with Streamlink and Streamlink Twitch GUI, here is a list of my config recommendations.

----

## Streamlink configuration

- **Player input**

   Make sure to avoid the passthrough method, as its purpose is to only resolve the HLS stream URL and pass it to the player as launch argument, meaning that the player will do all the stream fetching on its own, which completely bypasses Streamlink.

- **Low latency streaming**

   Simply tick the checkbox in the streaming settings menu to enable low latency streaming ([`--twitch-low-latency`](https://streamlink.github.io/cli.html#cmdoption-twitch-low-latency) Streamlink parameter). This can also be done for individual channels in their respective settings menus.

   Unless you have a terrible internet connection, low latency streaming should always be enabled, even if the channel you're trying to watch is not streaming in low latency mode.

   When enabling low latency streaming, Streamlink's [HLS live edge value](https://streamlink.github.io/cli.html#cmdoption-hls-live-edge) will be reduced to at most 2. Reducing it further to 1 is not recommended.

   In addition to ticking the checkbox, **player specific configurations should be applied** and the player's own cache/buffer reduced to a minimum, so that true low latency streaming can be achieved. More about this down below.

   Low latency streaming obviously won't work if the passthrough player input method has been selected.

- **Filter out embedded ads**

   Since Twitch has been aggressively pushing advertisements embedded into the HLS streams, especially pre-roll ads which ruin most of the viewing experience while exploring new channels, I also recommend filtering out the ads via the checkbox in the streaming settings menu ([`--twitch-disable-ads`](https://streamlink.github.io/cli.html#cmdoption-twitch-disable-ads) Streamlink parameter).

   Filtering out ads may even be necessary when using players like VLC for example, as it causes discontinuities in Streamlink's output stream, which can cause issues in certain players and player configurations (eg. GPU acceleration). Unfortunately, this problem can't be solved by Streamlink.

   Filtering ads obviously won't work if the passthrough player input method has been selected.

## Player configuration

Instead of using VLC, which is the default player chosen by Streamlink, [**I strongly recommend using MPV**](https://mpv.io/), as it is the overall better player.

The problem with MPV however is that it gets configured via command line parameters or via config files, and this may turn off new or inexperienced users.

Since it doesn't make sense adding all available MPV parameters to the MPV player preset in Streamlink Twitch GUI, some parameters need to be set manually via the "custom parameters" field in the player settings menu or via MPV's config file.

Check the [MPV documentation](https://mpv.io/manual/master/) for the available parameters and how config files can be set up.

- **Player window behavior**

  - [`--no-border`](https://mpv.io/manual/master/#options-no-border)

    This will remove the player's window decorations, aka. its borders and title bar.

  - [`--no-keepaspect-window`](https://mpv.io/manual/master/#options-no-keepaspect-window)

    This adds letter-boxes around the content when it doesn't match the player-window's aspect ratio.

  - [`--window-maximized=yes`](https://mpv.io/manual/master/#options-window-minimized)

    This initially maximizes the player window, which results in a pseudo-fullscreen mode.

- **Playlist behavior**

  - [`--loop-playlist=inf`](https://mpv.io/manual/master/#options-loop-playlist)  
    [`--loop-file=inf`](https://mpv.io/manual/master/#options-loop-file)

    This allows reloading the stream by pressing <kbd>Enter</kbd> in case of buffering issues, which is quicker than restarting Streamlink.

- **Caching / Buffering**

  - [`--cache=yes`](https://mpv.io/manual/master/#options-cache)

    Player caching should always be enabled, especially while low latency streaming, to prevent (micro-)stuttering. Another benefit of having a player cache is being able to rewind.

  - [`--demuxer-max-bytes=750k`](https://mpv.io/manual/master/#options-demuxer-max-bytes)

    This reduces MPV's "forward-buffer" to a bare minimum, which is necessary to achieve true low latency streaming. The value of course depends on the connection quality to the Twitch servers and the stream's (constant) bitrate, which is currently usually **between 6000 kbit/s and 8000 kbit/s** for source streams.

    A value of `750k` roughly means `0.75` seconds (`(8000 / 8) * 0.75`), which is a good value for low latency streaming without running into buffering issues on stable connections. With these settings, Twitch's web player can be beaten by about 2 seconds.

  - [`--demuxer-max-back-bytes=1800M`](https://mpv.io/manual/master/#options-demuxer-max-back-bytes)

    This defines how much data MPV will keep in its "back-buffer" for being able to rewind. Adjust this to your needs. This does of course also depend on the stream's bitrate, as mentioned above.

    A value of `1800M` should be enough to keep half an hour of data in the buffer for 8000 kbit/s streams.
