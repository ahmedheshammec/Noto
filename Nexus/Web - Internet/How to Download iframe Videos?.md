if you have a video url from the network requests like this: 

```
https://vk.com/video_ext.php?oid=848077136&id=456239422&hd=2
```

then you can download it via `yt-dlp` like this: 

```shell
yt-dlp "https://vk.com/video848077136_456239422"
```

VK video URLs follow a simple pattern:

```
https://vk.com/video{oid}_{id}
```

**Common video hosts you'll encounter:** VK, Dailymotion, Streamtape, Uqload, Vidspeeds, Fembed, Dood — yt-dlp supports most of them natively.

→ Quick way to find the iframe yourself (no browser automation needed):

```shell
# View page source and grep for iframe
curl -s "https://tye.ahwaktv.net/see.php?vid=9cfe827c5" | grep -o 'iframe[^>]*src="[^"]*"'
```