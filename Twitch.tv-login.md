### Login

Two login methods are being supported:

#### Username / password

This is the default method and will open the system's default web browser with a login form on the Twitch.tv website. After a successful validation, an OAuth token (secret login key) will be generated which will then be stored and used for future logins.

While logging in, a local webserver is being started in the background, so that Streamlink Twitch GUI is able to receive the result of the login attempt from the web browser. On Windows this will pop up a firewall message and should be accepted.

If JavaScript has been disabled, the second method needs to be enabled first (see below). The OAuth token can then manually be copied from the browser's address bar and pasted into the GUI.

#### OAuth token login

This method needs to be enabled first by activating the advanced settings in the main settings menu. It enables Twitch.tv logins by using an OAuth token directly, which can be useful if the same account is being used on multiple devices, since using the password method will invalidate the previously generated access token.


### While being logged in

Being logged in also enables [[desktop notifications|desktop-notifications]].
