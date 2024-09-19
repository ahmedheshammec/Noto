apple music album art location on the mac can be found in this location: 

```zsh
/Users/Ahmed/Library/Containers/com.apple.AMPArtworkAgent/Data/Documents/artwork
```

::`Note`::: you can copy the album art directly from apple music by doing the following: 
* right click on the album art and click on Get info. 
* command + c to copy 
* open photoshop document with size 600 x 600 pixels. 
* command + v to paste and save the image as jpeg
* you can save the image using tools like pngpaste without the need of Photoshop. 

now let's merge the m4a file with the jpeg file, to do so we need to install `AtomicParsley`

```zsh
brew install atomicparsley
```

now the command to merge

```zsh
AtomicParsley /path/to/your/file.m4a --artwork /path/to/album_art.jpeg
```

to remove the artwork you can use the following command: 

```zsh
AtomicParsley input.m4a --artwork REMOVE_ALL -o output.m4a
```

to extract the artwork use the following command: 

```zsh
AtomicParsley input.m4a --extractPix
```

How to Add Lyrics and Artwork to m4a File?
How to Pass an Output File to Multiple Commands in ZSH?
```zsh
ffpb -i "Hold On.m4a" -i lyrics.txt -map 0 -map_metadata 0 -c copy -metadata lyrics="$(cat lyrics.txt)" temp.m4a && \
AtomicParsley temp.m4a --artwork artwork.jpg --overWrite && \
mv temp.m4a lyrics.m4a
```
How to Add a Parameter and Then Call It Back?
Let's Say We Have a File Called `input.mp3` And We Want to Convert It To `m4a` To Do This We Can Use the Following Command: 

```zsh
i="input" ; ffpb -i "${i}.mp3" "${i}.m4a"
```

Or We Can Write the Command as Follows: 

```zsh
i="input.mp3" ; ffpb -i $i "${i%.*}.m4a"
```

Here We Used `%.*` To Remove the Extension From the Filename and Append the New One `m4a`
❖ We Can Also Use Tab Key Autocompletion for Convenience as Follows:

```zsh
i=Sad\ Collection-Re.mp3 ; ffpb -i $i "${i%.*}.m4a"
```

:: __`Very Important Note`__ :: If We Want to Make a Function in Zsh Snippets We Will Have to Escape Parameters with Backslash, Here's an Example for the Function

```zsh
expand-m4a() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~m4a$' ]]; then
    BUFFER="i= ; ffpb -i \$i \"\${i%.*}.m4a"\"
    CURSOR=2  # Move the cursor to the position
  fi
}
```
