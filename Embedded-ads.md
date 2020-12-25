## Embedded ads

### History

In 2019, Twitch has started sporadically embedding ads directly into streams in addition to their regular advertisement program on their website which can only overlay ads. The embedded ads situation has been an ongoing thing since then and has been turned off and on several times throughout the months, also with variations between regions, and it has recently been pushed more and more aggressively with long pre-roll ads.

While this may be an annoyance for end-users who are used to using ad-blocker extensions in their web-browsers for blocking regular overlaying ads, applications like Streamlink face another problem, namely stream discontinuities when there's a transition between an ad and the regular stream content or another ad.

Since Streamlink does only output a single progressive stream from reading Twitch's segmented HLS stream, ads can cause issues in certain players, as the output is not a cohesively encoded stream of audio and video data anymore during an ad transition. One of the problematic players is VLC, which is known to crash on these stream discontinuities in certain cases.

Unfortunately, entirely preventing embedded ads is not possible unless a loophole on Twitch gets discovered which can be exploited. This has been the case a couple of times now and ad-workarounds have been implemented in Streamlink and various ad-blockers, but the solutions did only last for a couple of weeks or even days until Twitch patched these exploits.

### Ads filtering in Streamlink

To prevent stream discontinuities in Streamlink's output, the [`--twitch-disable-ads`](https://streamlink.github.io/cli.html#cmdoption-twitch-disable-ads) CLI parameter was introduced in Streamlink [`1.1.0`](https://streamlink.github.io/changelog.html#streamlink-1-1-0-2019-03-31) in early 2019, which filters out advertisement segments from Twitch's HLS streams and pauses the stream output until regular content becomes available again. The filtering logic has seen several iterations since then, with the latest big overhaul in Streamlink [`1.7.0`](https://streamlink.github.io/changelog.html#streamlink-1-7-0-2020-10-18) in late 2020.

Due to [breaking changes on the Twitch API in November 2019](https://github.com/streamlink/streamlink/issues/2680#issuecomment-557605851), authentication had to be removed in Streamlink [`1.3.0`](https://streamlink.github.io/changelog.html#streamlink-1-3-0-2019-11-22) / [`1.4.0`](https://streamlink.github.io/changelog.html#streamlink-1-4-0-2020-04-22), which means subscribing a channel won't help with preventing ads while using Streamlink.

### Ads filtering in Streamlink Twitch GUI

**As a Streamlink Twitch GUI user, to activate Streamlink's ads filtering, all you have to do is enabling the "Skip advertisements embedded into streams" checkbox in the streaming settings menu.**

The option is also available for individual channels in their respective channel settings menu, so you can override the global configuration.

----

For more details, please read the following issue threads, or search the issue tracker(s) for other/older threads:

- [Streamlink issue #3210](https://github.com/streamlink/streamlink/issues/3210)
- [Streamlink Twitch GUI issue #754](https://github.com/streamlink/streamlink-twitch-gui/issues/754)
