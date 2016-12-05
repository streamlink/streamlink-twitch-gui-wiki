Streamlink Twitch GUI provides a list of different chat applications.

### Default browser

This will open the chat in the system's default browser. Unlike the chat popup button from the Twitch website (which is something completely different), this will include the address bar, bookmarks bar, etc.

### Chromium / Google Chrome

Choosing this method, Streamlink Twitch GUI will open Chromium or Google Chrome in the so called app mode. This removes all browser GUI elements and is similar to Twitch's chat popup.

Streamlink Twitch GUI includes a list of default install locations.

### Internet Explorer

This is the equivalent of the app mode of Chromium / Google Chrome. Requires the `msie-minimal.vbs` script, which is included in the Windows releases.

### Chatty

Uses the popular Java based chat application for Twitch. Please use a version greater than `0.8.2b2`, so single instance mode can be used.

Streamlink Twitch GUI includes a list of default Java install locations. The path to the Chatty .jar file needs to be set.

### Custom application

Set the custom application path and parameters.

Several variables related to the stream being watched are available.  
**Please make sure to wrap variables in quotation marks (single or double).**  
If used incorrectly, Streamlink Twitch GUI will escape every character, which will not be interpreted correctly by every application.

Correct usage:  
`--paramA '{varA}' --paramB "{varB1} {varB2}" "--paramC={varC}"`

#### Parameters

- **{url}**  
  The full URL for the twitch chat page of the stream
- **{channel}**  
  The streamer's channel name
- **{user}**  
  Your twitch username
- **{token}**  
  Your twitch access token