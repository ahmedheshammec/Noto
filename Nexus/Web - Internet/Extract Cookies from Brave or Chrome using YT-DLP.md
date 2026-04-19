
use this command: 

```bash
yt-dlp --cookies-from-browser brave --cookies cookies.txt --simulate "https://www.udemy.com/course/the-complete-javascript-course/" 2>/dev/null
```

then start the actual download using this command: 

```bash
yt-dlp --cookies cookies.txt \
  "https://www.udemy.com/course/the-complete-javascript-course/learn/lecture/22648393" \
  -o "%(playlist_index)s - %(title)s.%(ext)s"
```

