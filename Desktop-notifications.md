While [[being logged in|twitch.tv-login]], Streamlink Twitch GUI will periodically check the list of followed channels. As soon as a followed channel starts broadcasting, a desktop notification will be shown.

Notification behavior and click actions can be configured in the settings menu.


### Notification filtering

Notifications can be individually enabled or disabled in the settings menu of each channel. This will override the global setting and works in conjunction with the filtering setting (show all except disabled ones / ignore all except enabled ones).

To temporarily disable the notification system, click the entry in the application's tray icon menu. The paused state will be indicated by a teal colored icon in the titlebar and will not be saved between application restarts.


### Notification types

Several notification types are available, depending on the operating system. When choosing the "automatic selection" option, native methods are being preferred and all methods are being tested until rich notifications are being used as a last option.

#### Toast notifications (Windows)

Native notifications on Windows 8 and Windows 10, provided by SnoreToast. To be able to see toast notifications, "banner notifications" need to be enabled in the system settings / control center. Another requirement is a startmenu shortcut linking to the application. Streamlink Twitch GUI automatically creates a start menu shortcut if it is missing.

#### Native notifications (MacOS)

Streamlink Twitch GUI uses Chromium's (new and experimental) native notification implementation on MacOS, which uses in the system's notification center.

#### Freedesktop notifications (Linux)

Implementation of the freedesktop notification specification. Uses gdbus as a helper executable due to restrictions of the NW.js build system. Click actions are supported, but need to be supported by the notification server as well.

#### Growl notifications

Third party notification service for Windows, MacOS and Linux.

#### Chromium rich notifications

Chromium's custom, non-native notifications which are rendered by the application itself.
