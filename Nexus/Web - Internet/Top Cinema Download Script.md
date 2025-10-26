 
```bash
yt-dlp \
--user-agent "Mozilla/5.0" \
--referer "https://vidtube.pro/" \
-o "Elite.S07E01.%(ext)s" \
"https://your-url"
```


```shell
yt-dlp "https://sbs1205-my.sharepoint.com/personal/funct_cons_sbs-me_com/_layouts/15/stream.aspx?id=%2Fpersonal%2Ffunct%5Fcons%5Fsbs%2Dme%5Fcom%2FDocuments%2FRecordings%2FPayment%20Integration%20Discussion%2D20250821%5F113953%2DMeeting%20Recording%2Emp4" \
--cookies cookies.txt \
--verbose \
--no-cache-dir \
--format bestvideo+bestaudio/best \
--merge-output-format mp4 \
-o "%(title)s.%(ext)s"
```
