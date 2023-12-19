While [[being logged in|twitch.tv-login]], Streamlink Twitch GUI will periodically check the list of followed channels. As soon as a followed channel starts broadcasting, a desktop notification will be shown.

Notification behavior and click actions can be configured in the settings menu.


### Notification filtering

Notifications can be individually enabled or disabled in the settings menu of each channel. This will override the global setting and works in conjunction with the filtering setting:
- show all except disabled ones (blacklist)
- ignore all except enabled ones (whitelist)

The notification system can be temporarily disabled in the context menu of the application's tray menu icon. The paused state will be indicated by a teal colored icon in the titlebar and will not be saved between application restarts.


### Notification types

Several notification types are available, depending on the operating system. When choosing the "automatic selection" option, all methods will be tested in descending order, hoping to find a working notification provider.


#### Toast notifications (Windows 8+)

Native notifications on Windows 8 and above, provided by [SnoreToast][snoretoast]. To be able to see toast notifications, "banner notifications" need to be enabled in the [system settings / control center][windows]. Another requirement is a special startmenu shortcut linking to the application which also includes the application ID. SnoreToast automatically creates this special start menu shortcut if it is missing.


#### Native notifications (macOS and Linux)

Uses Chromium's native notification implementation.

- macOS  
  Uses the system's [notification center][macos].  
  The notification type (banner or clickable alert) can be configured in the system's notification settings when selecting the Streamlink Twitch GUI app.
- Linux  
  Uses the [freedesktop notification standard][freedesktop-spec].  
  Depending on the system configuration, a custom notification server needs to be running. See the [Arch Linux Wiki][arch-wiki] for more informations.

This method may fall back to Chromium rich notifications (see below).


#### Growl notifications

Third party notification service for Windows, macOS and Linux. Needs to be running on the localhost and default port.


[snoretoast]: https://github.com/KDE/snoretoast
[windows]: https://support.microsoft.com/en-us/help/10761/windows-10-change-notification-action-settings
[macos]: https://support.apple.com/en-us/HT204079
[freedesktop-spec]: https://developer.gnome.org/notification-spec/
[arch-wiki]: https://wiki.archlinux.org/index.php/Desktop_notifications
