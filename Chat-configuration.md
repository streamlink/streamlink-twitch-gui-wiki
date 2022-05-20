Streamlink Twitch GUI supports multiple different chat applications.


### Default browser

Attempts to open the chat in the system's default browser. Unlike the chat popup button from the Twitch website (which is something completely different), this will include the address bar, bookmarks bar, etc.


### [Chromium][chromium] / [Google Chrome][chrome]

Opens the chat in Chromium's or Google Chrome's so called "app mode". This removes all browser GUI elements and is similar to Twitch's chat popup.

A custom executable path needs to be set, if it can't be resolved via the included list of default install locations or via the system's `PATH` environment variable.


### [Chatty][chatty]

Uses the popular Java based chat application for Twitch. Please use a version greater than `0.8.2b2`, so single instance mode can be used.

Custom Java executable and `chatty.jar` paths need to be set, if they can't be resolved via the included list of default locations or via the system's `PATH` environment variable.

Since Twitch requires authentication for joining the chat, either the authentication option needs to be enabled (enabled by default), or custom auth data be set in Chatty itself.


### Chatty standalone (Windows)

The standalone version of Chatty that comes with a single executable.


### Custom application

Set a custom application path and parameters.

Several variables related to the stream being watched are available.  
**Please make sure to wrap variables in quotation marks (single or double).**  
If used incorrectly, Streamlink Twitch GUI will escape every character, which will not be interpreted correctly by every application.

Correct usage:  
`--paramA '{varA}' --paramB "{varB1} {varB2}" "--paramC={varC}"`

#### Variables

- **{url}**  
  The full URL for the twitch chat page of the stream
- **{channel}**  
  The streamer's channel name
- **{user}**  
  Your twitch username
- **{token}**  
  Your twitch access token


  [chromium]: https://www.chromium.org/Home
  [chrome]: https://www.google.com/chrome/browser/desktop/index.html
  [chatty]: https://chatty.github.io
