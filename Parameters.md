## Launch Parameters

#### --loglevel

Alias: `-l`  
Default: `error`  
Accepted values: `none`, `error`, `debug`

#### --no-logfile

Disables writing log messages to files. Log files are being stored for up to 7 days in the `$TMPDIR/streamlink-twitch-gui/logs` directory.

#### --max

Maximizes the application window after launch.

#### --min

Minimizes the application window after launch.

#### --tray

Starts the application in tray mode. The tray icon will be removed after restoring the window if tray mode has been previously disabled in the settings.

#### --no-version-check

Disables the internal new-version-check logic.


## Runtime parameters

The following parameters can be used when trying to start a second instance of Streamlink Twitch GUI. The command line will be passed to the main application instance and handled accordingly. Please make sure to enable the "Command line actions" option first in the GUI settings menu (requires advanced settings to be enabled). Due to platform limitations, only one parameter can be used at a time.

#### --launch

Accepted values: `{channel}`

Launches a stream and uses the same configuration when regularly launching the stream via the GUI.

Example:  
`--launch "lirik"`

#### --goto

Accepted values: `{route}`, `{url}`

Performs a transition to a different menu or submenu. See the [application router](https://github.com/streamlink/streamlink-twitch-gui/blob/master/src/app/router.js) for all available route names or accepted URLs. Sub-routes need to be separated by a dot from their parent-route. Since certain routes require parameters (models), providing a URL is necessary. URLs always start with a forward slash and need to be [escaped](https://www.w3schools.com/tags/ref_urlencode.asp) properly.  

Examples:  
`--goto "user.followedStreams"`  
`--goto "communities.index.all"`  
`--goto "/communities/all"`  
`--goto "/games/Dota%202"`  
`--goto "/communities/community/speedrunning"`  
`--goto "/channel/lirik"`  
`--goto "/search?filter=all&query=diablo"`  

#### --reset-window

Sets the window position to default. This may be useful in cases where the out-of-boundaries detection didn't work correctly or when the screen configuration changed and the window became inaccessible.
