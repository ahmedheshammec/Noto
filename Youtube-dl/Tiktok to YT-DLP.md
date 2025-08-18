→ Install Mozilla Firefox and Install this Addon: 

https://addons.mozilla.org/en-US/firefox/addon/tiktok-to-ytdlp/

when you open the tiktok channel to download and click the extension put the name of the file that will contain the links as `TikTokLinks.txt` 

then after the script fetches all the links use the following command: 

```bash
yt-dlp -a TikTokLinks.txt -o "%(id)s.%(ext)s"
```
