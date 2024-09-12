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