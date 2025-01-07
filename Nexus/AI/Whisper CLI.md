Install Whisper using pip with the command: 

```sh
pip install git+[https://github.com/openai/whisper.git](https://github.com/openai/whisper.git)
```

Additionally, install `FFmpeg` via `Homebrew` using: 

```sh
brew install ffmpeg
```

Models location: 

```
~/.cache/whisper/
```

→ first convert the video to a wav file:

```sh
ffmpeg -i video.mp4 audio.wav
```

→ Next run whisper on your audio file:

```sh
whisper output_audio.wav --language English
```

→ This large-v3-turbo model supports Arabic out of the box and many more languages.

→ you can also run the command like this:

```sh
whisper input_audio.wav --model large-v3-turbo --language Arabic
```

→ there is other models like tiny, medium, .. etc. and the smaller the model the less accurate it is but on the other hand it doesn't drain computing resources as much as the big models.

→ you can download other models using a command like this:

```sh
whisper audio.wav --model medium --language English
```

