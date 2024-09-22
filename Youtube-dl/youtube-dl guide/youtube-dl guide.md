
to download the best video with the best quality type: 

```bash
yt-dlp -f bestvideo+bestaudio 'your_youtube_link'
```

to download the best audio type: 

```bash
yt-dlp -f bestaudio 'your_youtube_link'
```

to download a specific resolution type: 

```bash
yt-dlp -f "best[height=480]” 'your_youtube_link'
```

to download a playlist type: 

```bash
yt-dlp -i -f mp4 --yes-playlist 'your_playlist_link'
```

download numbered playlist whereas the videos be like 01.video_title.mp4 , 02.video_title.mp4, etc

```bash
yt-dlp -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]' --output "%(playlist_index)s.%(title)s.%(ext)s" --download-archive archive.txt "playlist_url"
```

and to convert the downloaded files with (-pix_fmt yuv420p) command we will use a bash script like this: 

```bash
#!/bin/bash

# Create a 'converted' directory if it doesn't exist
mkdir -p converted

# Loop through all files in the current directory
for file in *; do
    # Check if the file is not a directory
    if [ -f "$file" ]; then
        # Define the output file name (same as the original)
        output_file="converted/$file"

        # Use ffmpeg to convert the file and specify the output format
        ffmpeg -i "$file" -pix_fmt yuv420p "$output_file"

        # Remove the original file
        rm "$file"

        echo "Converted and removed: $file"
    fi
done
```
-------------------

here's a bash script that ask you for the playlist link and create a new directory with the playlist name automatically and download all as m4a 

```bash
#!/bin/bash

# Prompt for playlist URL
read-p"Enter playlist URL: "playlist_url

# Get the name of the playlist
playlist_name=$(yt-dlp--get-filename-o "%(playlist)s" "$playlist_url" |head-1)

# Check if playlist name was retrieved
if [ -z "$playlist_name" ]; then
echo"Failed to retrieve playlist name."
exit1
fi

# Create a new directory and enter it
mkdir-p"$playlist_name"
cd"$playlist_name"

# Download the playlist with error redirection
yt-dlp-f'bestaudio[ext=m4a]'--output"%(playlist_index)s.%(title)s.%(ext)s""$playlist_url" 2>/dev/null

```
-------------------

and here's another bash script that loops through all subfolders and convert m4a to mp3 and delete m4a after conversion.

```bash
#!/bin/bash

# Get the current directory (the directory from which the script is run)
main_dir=$(pwd)

# Loop through each subdirectory in the main directory
forsubdirin"$main_dir"/*; do
if [ -d "$subdir" ]; then
echo"Processing directory: $subdir"

# Loop through each .m4a file in the subdirectory
forfilein"$subdir"/*.m4a; do
# Check if file exists (to handle no .m4a files case)
if [ -f "$file" ]; then
# Construct the new .mp3 filename
newfile="${file%.m4a}.mp3"

# Convert m4a to mp3
ffmpeg-i"$file"-acodeclibmp3lame"$newfile"

# Delete the original .m4a file
rm"$file"
fi
done
fi
done

```

Download specific videos from playlist
or example, to download the 10th file from a playlist, run:

```bash
yt-dlp --playlist-items 10 <playlist_url>
```

to download multiple random files, just specify indices of the videos in the playlist separated by commas like below:
```bash
yt-dlp --playlist-items 2,3,7,10 <playlist_url>
```

ultimate  command 
```bash
yt-dlp -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]' --output "%(title)s.%(ext)s" --postprocessor-args "-c:v libx264 -pix_fmt yuv420p -c:a aac -strict experimental" 'your_youtube-link'
```

ultimate bash script to download single video from youtube with lib x264 and H.264
```bash
#!/bin/bash

# Ask for the video URL
read-p"Enter the video URL: "url

# Extract the title for the files
title=$(yt-dlp--get-filename-o "%(title)s" "$url")

# Download the best video
yt-dlp-f'bestvideo[ext=mp4]'--output"${title}_video.mp4""$url"

# Download the best audio
yt-dlp-f'bestaudio[ext=m4a]'--output"${title}_audio.m4a""$url"

# Check if the files exist
if [[ -f "${title}_video.mp4" ]] && [[ -f "${title}_audio.m4a" ]]; then
echo"Files found. Proceeding with merge."
else
echo"Files not found. Exiting."
exit1
fi

# Merge video and re-encode audio using ffpb
# Using H.264 video codec for better compatibility
ffpb-i"${title}_video.mp4"-i"${title}_audio.m4a"-c:vlibx264-c:aaac-b:a128k-pix_fmtyuv420p"${title}.mp4"

# Clean up: Remove the temporary video and audio files
rm"${title}_video.mp4"
rm"${title}_audio.m4a"
```

Limit the quality to 1080p 
```bash
yt-dlp -f 'bestvideo[ext=mp4][height<=?1080]+bestaudio[ext=m4a]' --output "%(title)s.%(ext)s" --postprocessor-args "-c:v libx264 -pix_fmt yuv420p -c:a aac -strict experimental" 'your_youtube-link'
```

download entire youtube channel
```bash
yt-dlp -f "bestvideo[height>=720][ext=mp4]+bestaudio[ext=m4a]" -ciw -o "%(title)s.%(ext)s" -v 'one of the following links'
https://www.youtube.com/c/{channelName} https://www.youtube.com/channel/{channelId} https://www.youtube.com/@{userName}
```

download youtube audio m4a
```bash
yt-dlp -f "bestaudio[ext=m4a]" --no-playlist --output "%(title)s.%(ext)s" '
```
### How to Fix No video formats found! Error and Use Cookies
### How to Fix Facebook Video Reels Error With yt-dlp 

to fix this we need cookies.txt file, and we can get it with two ways: 

❖ using chrome browser extension called `Get cookies.txt LOCALLY`  from this link: 
https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc

❖ or you can paste the following code in your console: 

```js
(() => {
    // Paste value of cookie's header obtained from network tab between the quotes,
    // or leave it as empty string.
    let COOKIE = '' || document.cookie;

    copy(
        '# Netscape HTTP Cookie File\n' +
        COOKIE.split(/; /g)
            .map(e => e.replace('=', '\t'))
            .map(e => window.location.hostname.replace('www.', '') + '\tFALSE\t/\tTRUE\t0\t' + e)
            .join('\n')
    )
})()
```

the Netscape-formatted cookies will be copied to your clipboard. Paste inside a cookie.txt file using the following command:

```bash
pbpaste > cookies.txt
```

And Reference It when You Download the File with the Following Flag ::--cookies:: ::./cookie.txt::.

❖ If that Didn't Work Go to This Link to Download the Loatest Release: 
https://github.com/yt-dlp/yt-dlp-master-builds/releases/

❖ And Download the Latest One for Mac It Will Be a File Called `yt-dlp_macos` This Will Download a Binary File to Install It Use the Following Commands: 

```bash
sudo cp yt-dlp_macos /usr/local/bin/ 
```

❖ This Will Copy the Binary File to the Bin Location of the Mac System but We Have to Give It Permissions to Run: 

```bash
sudo chmod +x /usr/local/bin/yt-dlp_macos 
```

❖ Now to Be on the Safe Side Check Which `yt-dlp` Is Recognized by the System Now Using the Following Command: 

```bash
which yt-dlp
```

❖ If You Find that `yt-dlp` Is Not a Command Recognized by the Shell or It's Linked to a Different Version We Can Fix This by Going To `.zshrc` File and Add the Following Line: 

```bash
alias yt-dlp="/usr/local/bin/yt-dlp_macos"
```

❖ Now Start a New Session and Check for the Version to See if It Matches the Final Build and Try Downloading Again Your Video.
### How to download HLS stream using `yt-dlp` ?

❖ Check the available formats:
❖ Use the -F option to list all available formats, then choose a specific one:

```bash
yt-dlp -F "URL"
yt-dlp -f FORMAT_CODE "URL"
```

#### How to Merge Audio and Video Files Together After Downloading Them Separately Using `ffmpeg`? 

Use the Following Command: 

```bash
ffpb -i video.webm -i audio.webm -c copy output.webm
```


### How to Fetch a Video Title Using `yt-dlp`? 

We Can Do This Using The `--get-title` Flag Like This: 

```zsh
yt-dlp --get-title https://youtu.be/bp2eev21Qfo
```


