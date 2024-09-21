First, we need to know the encoding of the `srt` file, so we will install the 'file' command line tool like this: 

```plaintext
brew install file
```

after that, we will use the file command to know the encoding like this: 

```plaintext
file -i your_subtitle.srt
```

This command should return the character encoding information. Make sure it’s UTF-8.
If Not UTF-8: If the SRT file is not encoded in UTF-8, you can convert it to UTF-8 using a text editor or command-line tools like iconv. For example, to convert an SRT file from ISO-8859-1 to UTF-8:
to install iconv use this command: 

```plaintext
brew install libiconv
```

to convert your `srt` to `utf-8` use this command: 

```plaintext
iconv -f ISO-8859-1 -t UTF-8 "input.srt" > "output.srt"
```

Note: this method using iconv may not work, it didn't work for me. here's what worked: opening the `srt` file in vs code, clicking on the encoding, and choosing re-open with encoding. and click again on the encoding option again and saving it as `utf-8`
in Arabic subtitles you must remove all the "علامات الترقيم" from the `srt` file using vs code find and replace, otherwise you'll find weird output in the file after conversion
### :: `Now Let's Merge the Subtitle with the Movie Using This Command:` ::

```plaintext
ffpb -i movie.mp4 -vf "subtitles=subtitle.srt:force_style='FontName=GE Aridi Naskh,FontSize=20'" output.mp4
```

we replaced `ffmpeg` with `ffpb` to show the progress bar of the conversion. 
Fonts used in Translation for Arabic: 

```plaintext
GE Aridi Naskh,FontSize=24
Noto Naskh Arabic
```

if you encountered the following error: 
`Unsupported channel layout "6 channels" The channel layout "6 channels" is not supported.`
If you encounter the error message "Unsupported channel layout: 7 channels" when trying to add an audio file with 7 channels (such as 7.1 surround sound) to a video using FFmpeg, you can try down mixing the audio to a supported channel layout.
Here's an example command that down mixes the audio to stereo (2 channels) using FFmpeg:

```plaintext
ffmpeg -i video.mp4 -i audio.m4a -c:v copy -c:a aac -ac 2 -map 0:v:0 -map 1:a:0 output.mp4
```

in my case the movie.mp4 didn't have audio stream at all cuz i converted from mkv to mp4 and during the conversion i lost all audio which resulted the above error. 
you can use the ﻿-c:a copy flag in your command, which ensures that the audio stream is copied from the input file to the output file without any transcoding.
### :: `How to Convert subtitles from ".sub" to subviewer ".srt" format` ::

using `sub2srt` formulae, here's how to install it: 

```plaintext
brew install sub2srt
```

:: `Usage` ::

```plaintext
sub2srt input.sub output.srt
```

### :: __`Convert Ass to Srt Usign Ffmpeg`__ ::

```plaintext
ffmpeg -i input.ass output.srt
```
