The configuration of Livestreamer is a mix between your Livestreamer config file (located in your home folder) and the used command line parameters. In the GUI you're able to override some of these parameters and also add custom ones if you like to do so. Most of the parameters are hidden behind the `advanced settings`, so please make sure to enable these first at the top of the settings menu.

**Executable location**  
If Livestreamer has been installed in a different location other than the default, you need to select the executable path here, so the GUI can find it.

**Custom parameters**  
See the Livestreamer manual for a list of all available parameters. Some parameters will be overridden by the GUI, though.

**Stream type**  
By default, the GUI will choose the `HTTP streaming` method for you, which is supported by most of the video players. In some cases you may want to choose a different method, eg. if you want to reduce the streaming delay.  
By choosing `HTTP` or `RTMP`, Livestreamer will act as a relay between Twitch and your videoplayer. It will do all the data fetching and buffering and also transforms the stream into the selected streaming protocol.  In my experience, the `RTMP` has a shorter streaming delay than `HTTP`, but is not supported by every player.  
When selecting `HLS`, Livestreamer will just forward the HLS-Stream URL over to the videoplayer (Twitch streams are being broadcasted in the `HLS` protocol). This method has the shortest delay, but you won't be able to customize the buffering and it doesn't play very well with the GUI, since closing the player via the GUI isn't going to work.
