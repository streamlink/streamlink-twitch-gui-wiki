Streamlink Twitch GUI wiki repo
====

**THIS PAGE IS NOT PART OF THE WIKI**

[**Please go here if you're looking for the Streamlink Twitch GUI wiki.**][wiki]

----

This repository is shared between the actual wiki and [`streamlink-twitch-gui-wiki`][wiki-repo], which is meant for reviewing and submitting changes.

## Contributing

Found a mistake or got something useful to share? Then please open a pull request with your changes!

Thank you for helping improve the Streamlink Twitch GUI wiki!

#### Wiki documentation

See [Github's wiki documentation][gh-docs] for the available formats that can be used to write wiki pages.

#### Quickstart

1. Fork the repository onto your Github account
2. Clone your fork locally and add the `upstream` remote
   ```sh
   git clone 'git@github.com:YOUR_USERNAME/streamlink-twitch-gui-wiki.git'
   cd streamlink-twitch-gui-wiki
   git remote add upstream 'https://github.com/streamlink/streamlink-twitch-gui-wiki.git'
   ```
3. Get the latest changes from `upstream` if you've cloned a while ago
   ```sh
   git pull upstream master
   ```
4. Checkout a new branch and apply your changes
   ```sh
   git checkout -b new-branch
   $EDITOR file-to-be-edited
   git add file-to-be-edited
   git commit
   ```
6. Push the branch to `origin` (your fork) and open a pull request
   ```sh
   git push origin new-branch
   ```


  [wiki]: https://github.com/streamlink/streamlink-twitch-gui/wiki
  [wiki-repo]: https://github.com/streamlink/streamlink-twitch-gui-wiki
  [gh-docs]: https://docs.github.com/en/free-pro-team@latest/github/building-a-strong-community/about-wikis
