## Parameter types

There are two different kind of parameters: launch and runtime parameters (`L` and `R`).  
Launch parameters are only recognized on the initial application start, while runtime parameters can be used to send actions to the already running application process. To be able to use runtime parameters, please make sure to enable the "Command line actions" option first in the GUI settings menu (requires advanced settings). Due to platform limitations, only one runtime parameter can be used at a time.

#### --loglevel

Type: `L`  
Alias: `-l`  
Accepted values: `none`, `error`, `debug`  
Default: `error`

Defines the kind of log output messages. By default, only error messages will be logged. Debug messages can contain useful informations of the stream launch process, chat applications, notifications, etc.  
Log files are being stored for up to 7 days in the `$TMPDIR/streamlink-twitch-gui/logs` directory.

#### --no-logfile

Type: `L`

Disables writing log messages to files.  
Log files are being stored for up to 7 days in the `$TMPDIR/streamlink-twitch-gui/logs` directory.

#### --no-version-check

Type: `L`

Disables the internal new-version-check logic.

#### --max

Type: `L+R`  
Aliases: `--maximize`, `--maximized`

Maximizes the application window.

#### --min

Type: `L+R`  
Aliases: `--minimize`, `--minimized`

Minimizes the application window.

#### --tray

Type: `L+R`

Hides the application window and creates an icon in the system tray. The icon will be removed after restoring the window if tray mode has been disabled in the settings.

#### --reset-window

Type: `L+R`

Sets the window position to default. This may be useful in cases where the out-of-boundaries detection didn't work correctly or when the screen configuration changed and the window became inaccessible.

#### --launch

Type: `L+R`  
Accepted values: `{channel}`

Launches a stream and uses the same configuration when launching it regularly via the GUI.

Example:  
`--launch "lirik"`

#### --goto

Type: `L+R`  
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
