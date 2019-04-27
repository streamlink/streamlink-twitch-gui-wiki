## Parameter types

There are two different kinds of parameters:  
*launch* and *runtime* parameters  

Launch parameters are only recognized on the initial application start, while runtime parameters can be used to send actions to the already running application process. To be able to use runtime parameters, "Advanced settings" and "Command line actions" need to be enabled in the main settings menu. Due to current platform limitations, only one runtime parameter can be used at a time.

----

#### `--loglevel`, `-l`

| | |
| :--- | :--- |
| Parameter type | launch parameter |
| Accepted values | `none`, `error`, `debug` |
| Default value | `error` |

Defines the verbosity of log messages. Debug log messages, in addition to error log messages, may contain useful informations of the stream launch process, the chat application, desktop notifications, etc.

Please make sure to remove sensitive data when posting log messages on the issue tracker.

By default, log output is written to log files and stored for up to 7 days.

| OS | Log file path |
| :--- | :--- |
| Windows | `%TMP%\\streamlink-twitch-gui\\logs` |
| macOS | `${HOME}/Library/Logs/streamlink-twitch-gui` |
| Linux | `${XDG_DATA_HOME:-${HOME}/.local/share}/streamlink-twitch-gui/logs` |

----

#### `--no-logfile`

| | |
| :--- | :--- |
| Parameter type | launch parameter |

Disables writing log messages to files.

----

#### `--no-version-check`

| | |
| :--- | :--- |
| Parameter type | launch parameter |

Disables the internal new-version-check logic.

----

#### `--maximize`, `--max`, `--maximized`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |

Maximizes the application window.

----

#### `--minimize`, `--min`, `--minimized`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |

Minimizes the application window.

----

#### `--tray`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |

Hides the application window and creates an icon in the system tray. The icon will be removed after restoring the window if tray mode has been disabled in the settings.

----

#### `--reset-window`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |

Sets the window to its default position. This may be useful in cases where the out-of-boundaries detection didn't work correctly or when the screen configuration changed and the window became inaccessible.

----

#### `--launch`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |
| Accepted values | `{channel}` |

Launches a stream and uses the same configuration when launching it regularly via the GUI.

Example:  
`--launch "lirik"`

----

#### `--goto`

| | |
| :--- | :--- |
| Parameter type | launch+runtime parameter |
| Accepted values | `{route}`, `{url}` |

Performs a transition to a different menu or submenu. See the [application router](https://github.com/streamlink/streamlink-twitch-gui/blob/master/src/app/router.js) for all available route names or accepted URLs. Sub-routes need to be separated by a dot from their parent-route. Since certain routes require parameters (models), providing a URL is necessary. URLs always start with a forward slash and need to be [escaped](https://www.w3schools.com/tags/ref_urlencode.asp) properly.  

Examples:  
`--goto "user.followedStreams"`  
`--goto "communities.index.all"`  
`--goto "/communities/all"`  
`--goto "/games/Dota%202"`  
`--goto "/communities/community/speedrunning"`  
`--goto "/channel/lirik"`  
`--goto "/search?filter=all&query=diablo"`  
