first create 1024 x 1024 png file and name it 

```
input.png
```

Then Change Directory to the Png File Location and Copy Paste the Following Into the Terminal:

```
input_filepath="input.png"
output_iconset_name="output.iconset"
mkdir $output_iconset_name

sips -z 16 16     $input_filepath --out "${output_iconset_name}/icon_16x16.png"
sips -z 32 32     $input_filepath --out "${output_iconset_name}/icon_16x16@2x.png"
sips -z 32 32     $input_filepath --out "${output_iconset_name}/icon_32x32.png"
sips -z 64 64     $input_filepath --out "${output_iconset_name}/icon_32x32@2x.png"
sips -z 128 128   $input_filepath --out "${output_iconset_name}/icon_128x128.png"
sips -z 256 256   $input_filepath --out "${output_iconset_name}/icon_128x128@2x.png"
sips -z 256 256   $input_filepath --out "${output_iconset_name}/icon_256x256.png"
sips -z 512 512   $input_filepath --out "${output_iconset_name}/icon_256x256@2x.png"
sips -z 512 512   $input_filepath --out "${output_iconset_name}/icon_512x512.png"

iconutil -c icns $output_iconset_name

rm -R $output_iconset_name
```

And Hit Enter

### source
https://www.codingforentrepreneurs.com/blog/create-icns-icons-for-macos-apps/

**`Code Snippet`**
https://liba.ro/61wsadyp7




