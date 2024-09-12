
**To install it use this homebrew command
**```
brew install imagemagick
```****￼
**simple usage **::
::```
convert file.png file.jpg
```::::￼
**convert single psd to png**::
::::::first navigate to the file in terminal then type
```
convert 'file.psd[0]' file.png
```
the 
```
[0]
```
 is used to convert the file with the whole layers in it 
**convert single psd to jpg**
first navigate to the file in terminal then type
```
convert 'file.psd[0]' file.jpg
```

**Batch Convert to JPG
******first navigate to the file in terminal then type
```
convert '*.psd[0]' -set filename:base "%[basename]" "%[filename:base].jpg"
```
**Batch Convert PDF to PNG**
```plaintext
convert '*.pdf' -set filename:base "%[basename]" "%[filename:base].png"
```

**Batch Convert to PNG
**first navigate to the file in terminal then type
```
convert '*.psd[0]' -set filename:base "%[basename]" "%[filename:base].png"
```

the 
```
%
```
is to generate output file names based on what you specify. 

**Batch Convert HEIC to JPG**
```plaintext
magick mogrify -monitor -format jpg *.HEIC
```

Convert an Entire PDF to a Single image: 
```plaintext
convert -density 150 -antialias "input_file_name.pdf" -append -resize 1024x -quality 100 "output_file_name.png"
```

Make All Jpg And Jpeg Files Below 300 Kb And The Width Is 1200 Px 
```plaintext
magick mogrify -format jpg -define jpeg:extent=300KB -define jpeg:optimize-coding=true -define jpeg:compression-quality=70 -strip -resize 1200x *.jpeg *.JPG
```

Compress Image Size 
```plaintext
convert myimage.jpg -quality 80 compressed_myimage.jpg
```








