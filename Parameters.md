## Parameter types

There are two different kinds of parameters:  
*launch* and *runtime* parameters  

Launch parameters are only recognized on the initial application start, while runtime parameters can be used to send actions to the already running application process. To be able to use runtime parameters, "Advanced settings" and "Command line actions" need to be enabled in the main settings menu. Due to current platform limitations, only one runtime parameter can be used at a time.

----

### Streamlink Twitch GUI parameters

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
| Windows | `%TMP%\streamlink-twitch-gui\logs` |
| macOS | `${HOME}/Library/Logs/streamlink-twitch-gui` |
| Linux | `${XDG_STATE_HOME:-${HOME}/.local/state}/streamlink-twitch-gui/logs` |

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
`--goto "/games/Dota%202"`  
`--goto "/channel/lirik"`  
`--goto "/search?filter=all&query=diablo"`  

----

### NW.js / Chromium parameters

Streamlink Twitch GUI is built on top of the NW.js platform, a Node.js powered version of Chromium. This means that all NW.js and Chromium related parameters can be used. These parameters are by definition launch parameters. More information about the available parameters can be found on the following sites. Please note that certain parameters either won't work or should not be used at all when launching NW.js applications.

- [NW.js documentation](https://docs.nwjs.io/en/latest/References/Command%20Line%20Options/)
- [Peter Beverloo's List of Chromium Command Line Switches](https://peter.sh/experiments/chromium-command-line-switches/)
- [NW.js/Chromium source code (nw83:/chrome/common/chrome_switches.cc)](https://github.com/nwjs/chromium.src/blob/nw83/chrome/common/chrome_switches.cc)
- [NW.js/Chromium source code (nw83:/content/public/common/content_switches.cc)](https://github.com/nwjs/chromium.src/blob/nw83/content/public/common/content_switches.cc)

#### User data directory

| OS | Custom path | Default path |
| :--- | :--- | :--- |
| Windows | `--user-data-dir=C:\path\to` | `%LOCALAPPDATA%\streamlink-twitch-gui` |
| macOS | `--user-data-dir=/path/to` | Config:<br> `${HOME}/Library/Application Support/streamlink-twitch-gui` <br>Cache:<br> `${HOME}/Library/Caches/streamlink-twitch-gui` |
| Linux | `--user-data-dir=/path/to` | Config:<br> `${XDG_CONFIG_HOME:-${HOME}/.config}/streamlink-twitch-gui` <br>Cache:<br> `${XDG_CACHE_HOME:-${HOME}/.cache}/streamlink-twitch-gui` |

Sets the path of the application's user data directory where config and cache files are stored. Can be an absolute or relative path. If the path contains a space character, then the whole parameter with its value has to be set in quotes. On macOS and Linux, config and cache files are usually separated into different directories. Setting the parameter overrides this behavior. More detailed infos [here](https://chromium.googlesource.com/chromium/src/+/master/docs/user_data_dir.md).

#### Chromium logging

| OS | Warning+Error logging | Verbose logging |
| :--- | :--- | :--- |
| Windows | `--enable-logging --log-level=1` | `--enable-logging --v=1` |
| macOS / Linux | `--enable-logging=stderr --log-level=1` | `--enable-logging=stderr --v=1` |

Useful when diagnosing issues with the Chromium part of NW.js. On Windows, log output is not written to `stderr`, but instead written as a file to `User Data\chrome_debug.log` inside the user data dir (see above). This file will contain [Unix-like line endings](https://en.wikipedia.org/wiki/Newline). More detailed infos [here](https://www.chromium.org/for-testers/enable-logging).
