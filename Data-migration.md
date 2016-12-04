This guide describes the data migration process when coming from the old  
*Livestreamer Twitch GUI*.

**TL;DR**  
Don't copy the old config data.  
Just go through the settings menu and configure it manually. This shouldn't take more than two minutes.  
Please take a look at the new [[player presets|player-configuration]] and use these instead, so that bad default player configurations (in VLC) can be avoided.


## What has changed?

The application has been renamed, and along with it the name of the config (and cache) folder(s).

Also, a new NW.js version is being used, which uses a different data format and structure. NW.js automatically translates this data into the new format, but also keeps the old data.

Some internal settings have been changed. Most settings will be automatically transformed into the new format, but the old Streamlink or Livestreamer installation path settings won't be used.


## Data migration

### Windows

Go to the `%LOCALAPPDATA%` folder (or `C:\Users\%USERNAME%\AppData\Local`)  
and rename the `livestreamer-twitch-gui` folder to `streamlink-twitch-gui`

### MacOS

Go to the `$HOME/Library/Application Support` folder  
and rename the `livestreamer-twitch-gui` folder to `streamlink-twitch-gui`

Or run this bash script:

```bash
bash -c 'folder="${HOME}/Library/Application Support"; mv "${folder}/livestreamer-twitch-gui" "${folder}/streamlink-twitch-gui"'
```

### Linux

Go to the `$XDG_CONFIG_HOME` folder (or `$HOME/.config`)  
and rename the `livestreamer-twitch-gui` folder to `streamlink-twitch-gui`

Or run this bash script:

```bash
bash -c 'folder="${XDG_CONFIG_HOME:-${HOME}/.config}"; mv "${folder}/livestreamer-twitch-gui" "${folder}/streamlink-twitch-gui"'
```
