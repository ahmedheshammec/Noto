
install HTTrack by running the following command in your terminal:

```zsh
brew install httrack
```

Example: To download the website at https://ss64.com/mac/ for offline access using **HTTrack**, Run the following HTTrack command to download the site:

```zsh
httrack "https://ss64.com/mac/" -O ~/Desktop/ss64_mac_offline
```

**Wait for HTTrack to complete the download**. It will download the website content to the specified folder.

Once finished, you can open the downloaded website from the `~/Desktop/ss64_mac_offline` folder by opening the `index.html` file in a browser for offline access.