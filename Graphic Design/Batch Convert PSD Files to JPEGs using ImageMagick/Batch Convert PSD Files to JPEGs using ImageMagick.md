Here's a script that will convert all PSD files in a directory to JPEG files using ImageMagick:
```plaintext
#!/bin/bash

# set the path to the directory containing the PSD files
psd_dir="./"

# set the output directory for the JPEG files
jpeg_dir="./"

# loop through all PSD files in the directory
for file in "$psd_dir"/*.psd
do
  # flatten the PSD file and save it as a JPEG in the output directory
  convert "$file" -flatten "$jpeg_dir/$(basename "$file" .psd).jpeg"
done
```
To use the script, replace "/path/to/psd/files" with the actual path to the directory containing your PSD files, and replace "/path/to/output/directory" with the path to the directory where you want to save the JPEG files.
Make sure you have ImageMagick installed on your system. You can install it using your system's package manager or by downloading it from the ImageMagick website (https://imagemagick.org/).
To run the script, open a terminal and navigate to the directory where the script is saved. Then, make the script executable by running the following command:
```plaintext
chmod +x script.sh
```
Finally, run the script using:
```plaintext
./script.sh
```





