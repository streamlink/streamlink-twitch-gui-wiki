When choosing to use a custom chat application, there are several parameters which can be passed to the application. By default these parameters will be escaped before being passed through unless surrounded by quotes.

**Example**

Escaped: 
```
open irc://irc.twitch.tv/#{channel}
```

Becomes:
```
open irc://irc.twitch.tv#\c\h\a\n\n\e\l
```

Unescaped: 
```
open "irc://irc.twitch.tv/#{channel}"
```

Becomes:
```
open irc://irc.twitch.tv/#channel
```

# Parameters

## {url}

The full URL for the twitch chat page of the stream.

## {channel}

The streamer's channel name.

## {user}

Your twitch username.

## {token}

Your twitch access token