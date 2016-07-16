The configuration of Livestreamer is a mix between your Livestreamer config file (located in your home folder) and the used command line parameters. In the GUI you're able to override some of these parameters and also add custom ones if you like to do so. Most of the parameters are hidden behind the `advanced settings`, so please make sure to enable these first in the main settings menu.

#### Executable location

If Livestreamer has been installed in a different location other than the default or if the livestreamer installation directory is missing from your system's `PATH` environment variable, you need to select the executable path here, so the GUI can find it.

#### Custom parameters

See the Livestreamer manual for a [list of all available parameters](http://docs.livestreamer.io/cli.html#command-line-usage). Some parameters will be overridden by the GUI, though.

#### Stream type

By default, the GUI will choose the `HTTP` stream type for you. The reason for this is that it is supported by most of the video players. This is different from the default Livestreamer CLI usage, where the video data is passed to the player via `stdin`.  
In some cases you may want to choose a different stream type, eg. if you want to reduce the streaming delay. When choosing `HTTP` or `RTMP`, Livestreamer will act as a relay between Twitch and your videoplayer. It will do all the data fetching and buffering and the player will read the stream from there.  
When selecting `HLS` on the other hand, Livestreamer will just forward Twitch's HLS-Stream URL over to the videoplayer. This method has the shortest delay, but you won't be able to customize the buffering in the GUI and the player will need to do this on its own instead.  
Selecting the `HLS` stream type also changes the behavior of Livestreamer. Terminating the livestreamer process won't terminate the player process as well anymore, which means that you won't be able to close the player via the GUI.  
See [`--player-passthrough`](http://docs.livestreamer.io/cli.html#cmdoption--player-passthrough) for more informations.

#### HLS live edge + HLS segment threads

Here you can customize livestreamer's stream-fetching and -buffering behavior. Please have in mind, that these settings are disabled when choosing the `HLS` stream type (see above).  
See [`--hls-live-edge`](http://docs.livestreamer.io/cli.html#cmdoption--hls-live-edge) and [`--hls-segment-threads`](http://docs.livestreamer.io/cli.html#cmdoption--hls-segment-threads) for more informations.

#### Stream launch attempts

There are two Livestreamer parameters, which determine the behavior in case of stream launch errors.  
See [`--retry-open`](http://docs.livestreamer.io/cli.html#cmdoption--retry-open) and [`--retry-streams`](http://docs.livestreamer.io/cli.html#cmdoption--retry-streams) for more informations.