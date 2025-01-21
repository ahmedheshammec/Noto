### :: Change FPS ::
to change FPS of a video type: 

```bash
ffmpeg -i <input> -filter:v fps=fps=30 <output>
```

### :: Change Video Size ::
to change video size using H.264 type: 

```bash
ffmpeg -i input.mp4 -s 640x360 -c:a copy output.mp4
```

where:: -s:: stand for scale , ::-c:a copy::  is only used when the input and output format are the same. 
also note that the size must be divided by two in order for this to work. 
**Common Resolutions: 
3840 x 2160  (4k) 
1920 x 1080 (1080p)
1280 x 720 (HD) 
852 x 480 (480p) 
640 x 360 (360p) 
320 x 240 (240p) 
256 x 144 (144p) 
::another way:: to change the size of the file is: 

```bash
ffmpeg -i input.mp4 -filter:v scale=-1:480 -c:a copy output.mp4
```

where ::v:: stand for video and ::480:: stand for the resolution. 
::a third way:: you can change the size of the file: 

```bash
ffmpeg -i input.mp4 -vf scale=320:240 output.mp4
```

in some cases, ffmpeg will set the Sample Aspect Ratio to compensate for the ratio change. You have to manually set the SAR value to 1:1 to make the players display it in the way you want. For example:

```bash
ffmpeg -i input.mp4 -vf scale=320:240,setsar=1:1 output.mp4
```

### :: Compress The Video Size ::
to compress the video size type: 

```bash
ffmpeg -i input.mp4 -c:v libx264 -crf 30 -c:a copy output.mp4
```

the ::crf:: value represent the amount to compress: 
0 = no compression (lossless). 
46 = highest compression (bad quality). 
a good medium value is between (24 to (30)
 
### :: Convert Video To Gif  ::
convert video to Gif the right way: 

```bash
ffmpeg -i input.mp4 -vf 'fps=20,scale=trunc(oh*a/2)*2:720:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse' -loop 0 output.gif
```

fps = frames per seconds 
2:720 = the video size (720p, 480p, .. etc). 
-loop 0 = loop forever , if you change 0 to -1 it won't loop at all , if you change to something like 3 it means it will loop 3 times then stop looping. 
### :: Media Info ::
To Get Media Info 

```bash
ffmpeg -i <video or audiofile> -hide_banner
```

### :: Change Audio Sample Rate ::
Change Audio Sample Rate from 48000 Hz to 441000 Hz 

```bash
ffmpeg -i <Input File> -ar 44100 <output File>
```


### :: Check File for Audio Codec ::
to see if the video file has audio stream or not

```bash
ffprobe -v error -select_streams a:0 -show_entries stream=codec_name -of default=noprint_wrappers=1:nokey=1 video.mp4
```

### :: Mix Video And Audio Together ::
To Mix Video and Audio together

```bash
ffmpeg -i <audio file> -i <video file> <output file>
```

if you encountered an issue with the previous command try this one: 

```sh
ffmpeg -i video.mp4 -i audio.m4a -map 0:v -map 1:a -c:v copy -c:a aac -ac 2 output.mp4
```

### :: Trim ::
Trim Even to Milliseconds

```bash
ffmpeg -i input.mp4 -ss 00:00:00.000 -to 00:00:37.500 output.mp4
```
plaintext
Trim a m4a file using start and stop times: 

```
ffmpeg -i <audio file> -vn -ss 00:00:20 -to 00:00:30 -c copy <output file>
```

PS: in the above example we trim the last 10 seconds of 30 sec audio file
-vn    for no video reversed
-an   for no audio reversed

### :: How to Fix Preview Not Showing Thumbnails of Mp4 Files after Converting using FFMpeg ?  ::
add this to the middle of the code: 

```bash
-pix_fmt yuv420p
```
### :: Combine Videos With Same Codec Together ::
to combine videos with same codec together: 

```bash
ffmpeg -i "concat:input1.ts|input2.ts|input3.ts" -c copy output.ts
```

if you get an Error Message like this: 'FFMPEG (libx264) “height not divisible by 2” add this command to your code: 

```bash
-vf "pad=ceil(iw/2)*2:ceil(ih/2)*2"
```

### :: Convert Image Sequence into a video file using ffmpeg ::
open the terminal or command prompt in the directory that has the sequence inside and type the following command: 

```bash
ffmpeg -r 30 -i filename_%04d.jpg -pix_fmt yuv420p output.mp4
```

::-r:: stands for the frame rate.  
::30:: stands for frames per second. 
::filename_:: stands for the file name without the digits so in this case, the file name is something like: filename_0001.jpg
::%04d:: stands for the four digits at the end of the file name. 
::-pix_fmt yuv420p:: to output the video to all popular devices and fix the preview in Mac OS. 
::output.mp4:: is the name of the video that will be created using FFmpeg. 
### Ok, but what about a video with Alpha Channel? 
FFMPEG with Quicktime Animation (RLE) or FFVHUFF/HUFFYUV will do.

	- ffmpeg -i yoursequence%d.png -vcodec qtrle movie_with_alpha.mov
	- ffmpeg -i yoursequence%d.png -vcodec ffvhuff movie_with_alpha.avi
	- ffmpeg -i yoursequence%d.png -vcodec huffyuv movie_with_alpha.avi

You will get video files with transparency(alpha channel) preserved.
This also works. - ffmpeg -i yoursequence%d.png -vcodec png movie_with_alpha.mov

### :: How to Transcode to Apple ProRes 422?  ::**

use the following flag: 

```bash
-c:v prores_ks -profile:v 3
```

❖ c:v prores_ks: This sets the video codec to ProRes. prores_ks is often recommended as it gives more control and compatibility over the output.
❖ profile:v 3: This specifies the profile for ProRes 422. Here, 3 corresponds to ProRes 422 HQ. If you want to use standard ProRes 422, you can use 2.
### :: How to Convert .mov to Gif and Control Speed (FPS) and File Size? ::
you can use this command: 

```bash
ffmpeg -i test.mp4 -vf fps=5 test.gif
gifsicle -O3 --lossy=300 -o optimized.gif test.gif
```

change the lossy value and fps value to manipulate the file size. 
### :: How to Remove Audio from a Video File Using FFMPEG?  ::
Use The Following Command: 

```bash
ffmpeg -i input.mp4 -c:v copy -an output.mp4
```

The ::-c:v:: copy option tells FFMPEG to copy the video stream without re-encoding it. The -an option tells FFMPEG to remove all audio streams from the output file.
### :: How to Get Colorful Progress Bar During the Conversion ::
first to install it 

```bash
sudo npm install --global ffmpeg-progressbar-cli
```

::Usage::: replace `ffmpeg`   with `ffmpeg-bar`  inside your scripts.
Example

```bash
ffmpeg-bar -i input.mp4 -pix_fmt yuv420p output.mp4
```

for more info: 
https://github.com/sidneys/ffmpeg-progressbar-cli
Note: i tried to use `ffmpeg-bar`  with merging subtitles to movie file but it didn't work, so i used another tool with is `ffpb`  ffmpeg progress bar, and can be installed as follows: 

```bash
pip install ffpb
```

Usage: 

```bash
ffpb -i input.mp4 -pix_fmt yuv420p output.mp4
```

Github Page: https://github.com/althonos/ffpb

###  :: How to Concatenate Two Videos Using FFMPEG ::
her's the syntax: 

```bash
ffpb -i input1.mp4 -i input2.mp4 -filter_complex "[0:v:0][0:a:0][1:v:0][1:a:0]concat=n=2:v=1:a=1[outv][outa]" -map "[outv]" -map "[outa]" output.mp4
```

we replaced `ffmpeg` with `ffpb` to show the progress bar during the concatenation progress. 
Let's break down the command step by step:
`ffmpeg`: It refers to the FFmpeg software, a powerful tool for handling multimedia files.
`-i input1.mp4 -i input2.mp4`: These are the input files you want to process. Here, we have two input files named "input1.mp4" and "input2.mp4".
`-filter_complex`: This option allows you to apply complex filtering operations. The filter_complex flag is followed by the filtergraph description enclosed in quotes.
`"[0:v:0][0:a:0][1:v:0][1:a:0]concat=n=2:v=1:a=1[outv][outa]"`: This is the filtergraph description. It performs a concatenation operation on the video and audio streams of the input files. 
-`[0:v:0]` and `[0:a:0]` refer to the video and audio streams of the first input file respectively.
-`[1:v:0]` and `[1:a:0]` refer to the video and audio streams of the second input file respectively.
-`concat=n=2:v=1:a=1` specifies that we want to concatenate two inputs (n=2) into one output. `v=1` and `a=1` means that we want to preserve the video and audio streams in the output respectively.
-`[outv]` and `[outa]` are the names given to the output video and audio streams of the concatenation operation.
`-map "[outv]" -map "[outa]"`: These options specify which streams to include in the final output. Here, we are mapping the output video stream `[outv]` and the output audio stream `[outa]`.
`output.mp4`: This is the name of the output file that will be generated.
In summary, the command takes two input video files, concatenates their video and audio streams, and produces a single output file named "output.mp4" with the combined streams.

### Another Way to Concatenate:

→ Create **`join.txt`** file that contains the exact paths of the files that you want to join. All files should be same format (same codec). The path name of all files should be mentioned one by one like below.

```
file /home/sk/myvideos/part1.mp4
file /home/sk/myvideos/part2.mp4
file /home/sk/myvideos/part3.mp4
file /home/sk/myvideos/part4.mp4
```

→ Now, join all files using command:

```sh
ffmpeg -f concat -i join.txt -c copy output.mp4
```

If you get an error something like below: 

```
[concat @ 0x555fed174cc0] Unsafe file name '/path/to/mp4'
join.txt: Operation not permitted
```

Add **`"-safe 0"`**:

```sh
ffmpeg -f concat -safe 0 -i join.txt -c copy output.mp4
```

Alternatively, you can use the following one-liner command to join all files in a directory.

```sh
ffmpeg -i "concat:audio1.mp3|audio2.mp3|audio3.mp3" -c copy output.mp3
```


### :: `How to Know if the video file is valid using FFmpeg?` ::
To determine if a video file is valid using FFmpeg, you can use the following command:

```bash
ffmpeg -v error -i <video_file>
```

FFmpeg will attempt to open and parse the video file. If the file is valid, no error message will be displayed. If the file is invalid or corrupted, FFmpeg will output an error message indicating the issue with the file.
### :: __`Convert Video to be Compatible with Apple Devices and in Preview`__ ::
use the following command: 

```bash
ffmpeg -i input.mp4 -pix_fmt yuv420p -c:v libx264 -c:a aac output.mp4
```

### :: __`How to Dynamically Change Width and Height of a Video by Half or Quarter`__ ::
use the following command: 

```bash
ffmpeg -i input.mp4 -vf scale=iw/2:ih/2 output.mp4
```

but to make sure the output dimentions are even numbers we will use the following command: 

```bash
ffmpeg -i input.mp4 -vf "scale=ceil(iw/2/2)*2:ceil(ih/2/2)*2" output.mp4
```


### :: __`How to Convert Video to Png Sequence Files`__ ::
Use the Following Command: 

```bash
ffmpeg -i input.mp4 frame-%04d.png
```


### :: __`How to Increase Audio Levels (Audio Gain) Using FFMPEG`__ ::
use the following command: 

```bash
ffmpeg -i input.mp3 -filter:a "volume=5dB" output.m4a
```


### How to Apply Audio Corssface at the Beginning and End of Audio Clip Using FFMPEG ? 
you can apply an audio crossfade at the beginning and end of an audio clip using `ffmpeg`. To achieve this, you can use the `afade` filter. Here's how you can do it:
**Applying Fade-In (at the beginning):**
To apply a fade-in effect to the start of an audio clip, you can use the following command:

```bash
ffmpeg -i input.mp3 -af "afade=t=in:ss=0:d=5" output.mp3
```

- `t=in`: Specifies that the fade is a fade-in.
- `ss=0`: Start the fade at the beginning of the audio.
- `d=5`: The duration of the fade effect in seconds.

**Applying Fade-Out (at the end):**
To apply a fade-out effect at the end of an audio clip, you can use this command:

```bash
ffmpeg -i input.mp3 -af "afade=t=out:st=10:d=5" output.mp3
```

- `t=out`: Specifies that the fade is a fade-out.
- `st=10`: Start the fade-out at 10 seconds from the beginning of the audio.
- `d=5`: The duration of the fade effect in seconds.
**Combining Fade-In and Fade-Out:**
To apply both a fade-in at the beginning and a fade-out at the end, you can combine the filters:

```bash
ffmpeg -i input.mp3 -af "afade=t=in:ss=0:d=5,afade=t=out:st=15:d=5" output.mp3
```

- This command applies a 5-second fade-in at the start and a 5-second fade-out starting at the 15-second mark.
You can adjust the `d` and `st` parameters to fit the specific duration of your audio clip.

**How to Pass an Output File to Multiple Commands in ZSH?**

```bash
ffpb -i "Hold On.m4a" -i lyrics.txt -map 0 -map_metadata 0 -c copy -metadata lyrics="$(cat lyrics.txt)" temp.m4a && \
AtomicParsley temp.m4a --artwork artwork.jpg --overWrite && \
mv temp.m4a lyrics.m4a
```


### How to Use ffprobe in a Way that Doesn't Suck?
First We Need to Install `jq` Which Is a Lightweight JSON Processor, We Can Install It via Homebrew Using the Following Command: 

```bash
brew install jq
```

Now that We Have `jq` Installed, We Can Pipe the Output Of `ffprobe` to `jq` To Parse and Display the Data as JSON.

```bash
ffprobe -i input.mp4 -print_format json -show_streams -show_format | jq '.'
```

❖ You'll Notice a Lot of Data Printed as Json as Well as the ffprobe Version Data
❖ To Enhance This I've Selected the Most Important Fields to Display From Stream 0 and 1 (Video and Audio) Such as Fps, Width and Height, ..etc. In Addition I Disabled the ffprobe Version Data.
❖ Final Command: 

```bash
ffprobe -v error -i input.mp4 -print_format json -show_streams -show_format | jq '.streams[] | if .codec_type == "video" then {width, height, codec_name, codec_long_name, r_frame_rate} elif .codec_type == "audio" then {codec_name, codec_long_name, sample_rate} else empty end'
```

❖ By Setting `-v error`  We Disable the Verboose Mode Which Displays the Version Data
❖ We Can Combine This with ZSH Snippet for Even Faster Results

```bash
# Get Media Info Using ffprobe
expand-ffprobe() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~ffprobe$' ]]; then

    # Modify the BUFFER to include the random number before the extension in the last ${i}
    BUFFER="i=  ; ffprobe -v error -i \$i -print_format json -show_streams -show_format | jq '.streams[] | if .codec_type == \"video\" then {width, height, codec_name, codec_long_name, r_frame_rate} elif .codec_type == \"audio\" then {codec_name, codec_long_name, sample_rate} else empty end'"
    CURSOR=2  # Move the cursor to the position
  fi
}
```


### FFPLAY

❖ **`ffplay`** is a command-line media player included with `ffmpeg`. 

❖ **`Purpose`:**  It displays audio and video files to your screen or connected output devices.

**Simple commands:**

```bash
ffplay <video file>
```

Plays the specified video file.

**Key features:** 

* Supports various video formats (MP4, AVI, MKV etc.)
* Customizable playback settings (speed, volume, filters)

Here’s a quick cheat sheet for **`ffplay`** commands and common flags. `ffplay` is a simple media player that uses FFmpeg libraries for playback.

#### Basic `ffplay` Usage

```bash
ffplay [options] input_file
```

#### Common Playback Controls (Keyboard Shortcuts)

- **Space**: Pause/Resume
- **Left/Right**: Seek backward/forward 10 seconds
- **Up/Down**: Seek backward/forward 1 minute
- **s**: move forward one frame
- **q, ESC**: Quit
- **f**: Toggle fullscreen
- **m**: Mute/unmute audio
- **+/-**: Increase/Decrease volume
- **p**: Frame step (pause video and go frame by frame)
- **a**: Cycle audio streams
- **v**: Cycle video streams
- **t**: Cycle subtitle streams
- **0-9**: Jump to specific percentage in the file

---

#### Useful `ffplay` Command-Line Flags

| **Flag**           | **Description**                                                    |
|--------------------|--------------------------------------------------------------------|
| `-autoexit`        | Automatically exit when the stream ends.                           |
| `-fs`              | Start in fullscreen mode.                                          |
| `-loop [count]`    | Loop playback `count` times (use `-1` for infinite loop).          |
| `-an`              | Disable audio.                                                     |
| `-vn`              | Disable video.                                                     |
| `-sn`              | Disable subtitles.                                                 |
| `-ss [time]`       | Start playback at a specific time (format `hh:mm:ss`).             |
| `-t [duration]`    | Play a specific duration of the file (format `hh:mm:ss`).          |
| `-vf [filter]`     | Apply video filters (e.g., `scale=1280:720`).                      |
| `-af [filter]`     | Apply audio filters (e.g., `volume=2.0` to double volume).         |
| `-volume [0-100]`  | Set volume level (default is 100).                                 |
| `-x [width] -y [height]` | Set the video window size manually (e.g., `-x 1280 -y 720`). |
| `-window_title [title]` | Set custom window title.                                      |
| `-noborder`        | Play video without a window border.                                |
| `-i [device]`      | Open input from a capture device (e.g., `-i /dev/video0`).         |
| `-f [fmt]`         | Force format (useful for raw data input).                          |
| `-showmode [mode]` | Set display mode (`video`, `waves`, `rdft`).                       |

---

#### Example Commands

- **Play a video with no audio:**

  ```bash
  ffplay -an video.mp4
  ```

- **Start playback 1 minute into the file and play for 30 seconds:**

  ```bash
  ffplay -ss 00:01:00 -t 00:00:30 video.mp4
  ```

- **Play a video in fullscreen:**

  ```bash
  ffplay -fs video.mp4
  ```

- **Apply a video filter to scale the video to 1280x720:**

  ```bash
  ffplay -vf scale=1280:720 video.mp4
  ```

This cheat sheet covers most of the common flags you’ll need when using `ffplay`. 

#### Useful Use Cases

↪ You Can Use `ffplay` As a Tiktok Clone (Player) with the Loop Flag to Play a Video or Audio and It Keeps on Looping Forever. 

```bash
ffplay -i video.mp4 -loop -1
```

#### MPV For Precise In/Out Timestamps

First Install It Using This Command: 

```bash
brew install mpv
```

you can run it using the following command: 

```bash
mpv video.mp4
```

useful keyboard shortcuts: 

`.`  ⟶ forward one frame

`,`  ⟶ backward one frame

`← → `  ⟶ seek 5 seconds forward / backwards

`shift + ← → `  ⟶ seek 1 second forward / backwards

❖ Click on the Timestamps at the Player Window to Show Milliseconds Timestamp

### How to show GUI when opening audio files? 

1- one-time solution: use the following command: 

```sh
mpv --force-window=yes <your_file>
```

2- permanent solution: 

→ create `mpv.conf` file in this location: `~/.config/mpv/`

```sh
touch ~/.config/mpv/mpv.conf
```

add the following line

```
force-window=yes
```

→ we can use `echo` to quickly add it like this: 

```sh
echo "force-window=yes" >> ~/.config/mpv/mpv.conf
```

→ then we can verify it using `cat` command: 

```sh
cat ~/.config/mpv/mpv.conf
```

→ now you can run `mpv` with audio files and GUI. 


### How to get keyboard shortcuts {comma & dot} to work in audio files with force window mode? 

→ create `input.conf` file using the following command: 

```sh
touch "/Users/ahmed/.config/mpv/input.conf"
```

and add the following lines to the file: 

```
ctrl+, seek -0.05 #alternative binding for audio

ctrl+. seek 0.05 #alternative binding for audio
```

→ Now in audio files we will use `⌃ + ,` or `⌃ + .` for precise seeking. 

### How to speed up a video using `ffmpeg`? 

use the following command: 

```sh
ffmpeg -i input.mp4 -filter:v "setpts=0.5*PTS" -an output.mp4
```

→ `0.5` makes double the speed so if the video is 10 seconds long the output will be only 5. 

→ To make the output video even faster decrease the value to something like 0.2. and vise versa.

→ The `-an` flag removes any audio streams from the video file. 

### Loop Video over Audio

Let's say we have a 20 sec 4K video let's call it `input.mp4` and we have 1 hour m4a audio file let's call it `input.m4a` . i want `ffmpeg` command that makes an output video of the two clips where the 20 sec video keeps looping over and over until the end of the m4a file

You can use the following `ffmpeg` command to loop the video (`input.mp4`) and combine it with the audio (`input.m4a`) to create an output video that matches the length of the audio:

```bash
ffmpeg -stream_loop -1 -i input.mp4 -i input.m4a -shortest -c:v copy -c:a aac output.mp4
```

