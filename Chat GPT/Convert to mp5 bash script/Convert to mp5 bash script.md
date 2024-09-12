
```plaintext
#!/bin/bash

mkdir -p output

for input in *.mp4; do
    base=$(basename "$input" .mp4)
    output="output/${base}_converted.mp4"

    ffmpeg -i "$input" \
           -vcodec libx264 \
           -acodec aac \
           -vb 800k \
           -minrate 800k \
           -maxrate 800k \
           -bufsize 1000k \
           -vf "scale=640:-2" \
           -profile:v baseline \
           -level 3.0 \
           "$output"
done

echo "Conversion completed."
```

