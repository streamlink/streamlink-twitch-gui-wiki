With the GUI you're able to login into your Twitch.tv account and see all of your followed channels or games. It also lets you follow/unfollow channels or games while being logged in.  
To do this, click on any of the menus in the "My" section or click the user icon at the top.  

### Login

You can choose between two login methods:

**Username / password**  
This is the default method and will open a new window with a login form on the Twitch.tv website. After a successful validation, this will generate an OAuth token (secret login key) which the GUI will then store and use for future logins. This token is also being used by Livestreamer to authenticate your account while launching streams.  
If you want to use the same Twitch.tv account on another device, you need to use the second login method, or otherwise you will be logged out each time you're accessing your account on another device, since username/password logins always generate a new login token.

**OAuth token login** (requires advanced settings)   
This method lets you log in to your account by using the same OAuth token generated in a previous login. Please enable the advanced settings first at the top of the settings menu to do so.  
While being logged in, you can access your OAuth token by clicking on the user button at the top. Use this token on any other device to login into your account.


### Desktop notifications

While being logged in, the GUI will repeatedly check your followed channels. As soon as a new stream has started, it will raise a desktop notification for you. Go to the settings menu to customize the notifications behavior or the notification click action.  
Desktop notifications can be configured for each followed channel. Go to a channel page and click the channel settings button to override notifications for specific channels.

**Windows 8+**  
Notifications will be shown as [toast notification](https://ux.stackexchange.com/questions/11998/what-is-a-toast-notification). A requirement for this is a start menu shortcut to the application. The GUI will try to create a shortcut on each start when using Windows 8+, so you're able to use this feature.

**Windows 7**  
Notifications will be shown as balloon tooltip at the application's tray icon.

**Linux**  
Notification click actions are not supported on Linux.