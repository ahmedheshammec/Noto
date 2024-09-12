to achieve maximum results, start by using ::pdf squeezer app:: on the mac and if you want to squeeze it even more, this method uses ghostscript to compress the pdf file; you can install ghostscript using homebrew. 
to check if ghostscript is installed; open terminal and type: 
```plaintext
gs -h
```
If Ghostscript is installed you will see Ghostscript help information. If you see an error then Ghostscript is not installed.
Now open terminal in the folder that contains the pdf, we will start by ::converting the pdf to ps format:: which will make a ps file that is larger than the original file. 
```plaintext
pdf2ps -dLanguageLevel=3 myfile.pdf
```
this will create a ps file larger that the original pdf file. 
now we will convert the ps file to pdf file, for that; type:
```plaintext
ps2pdf -dPDFSETTINGS=/ebook myfile.ps
```
 Or, to avoid deleting your original **myfile.pdf**, you might put:
```plaintext
ps2pdf -dPDFSETTINGS=/ebook -sOutputFile=myshrunkenfile.pdf myfile.ps
```
the ::-dPDFSETTINGS=/ebook:: option can be changed to the following presets: 
| ### **-dPDFSETTINGS** Option | ### **Description** |
| -dPDFSETTINGS=/screen | Has a lower quality and smaller size. (72 dpi) |
| -dPDFSETTINGS=/ebook | Has a better quality, but has a slightly larger size (150 dpi) |
| -dPDFSETTINGS=/prepress | Output is of a higher size and quality (300 dpi) |
| -dPDFSETTINGS=/printer | Output is of a printer type quality (300 dpi) |
| -dPDFSETTINGS=/default | Selects the output which is useful for multiple purposes. Can cause large PDFS. |
￼
if you get the error message: Fontconfig warning: ignoring UTF-8: not a valid region tag
you can solve it by typing this command: 
```plaintext
export LC_CTYPE="en_US.UTF-8"
```
and then rerun the Ghostscript command. 
**How to EXTREMELY Compress the PDF?** 
First we need to extract images from the pdf using this GhostScript Command: 
```plaintext
gs -dNOPAUSE -dBATCH -sDEVICE=pngalpha -r300 -sOutputFile=output-%d.png input.pdf
```
Here’s what each option does:

	- -dNOPAUSE: This option prevents Ghostscript from pausing after each page.
	- -dBATCH: This option tells Ghostscript to process all pages without returning to the interactive prompt between each page.
	- -sDEVICE=pngalpha: This sets the output format to PNG with transparency (alpha channel).
	- -r300: This sets the resolution of the output file to 300 dots per inch (DPI).
	- -sOutputFile=output-%d.png: This sets the naming pattern for the output files. Ghostscript will replace %d with the page number.

With this command, Ghostscript will process the PDF and output each page as a separate PNG file named output-1.png, output-2.png, and so on, for each page of the PDF.
now we need to lower the quality of each image to 70%, we will use simple shell script for that: 
```plaintext
mkdir -p output_folder
for img in *.png; do
  convert "$img" -quality 70 "output_folder/${img%.png}.jpg"
done
```
we will run the script by permitting it: 
```plaintext
chmod a+x your_shell_script.sh
```
and execute the script: 
```plaintext
./your_shell_script.sh
```

Run this script in the directory where your PNG images are located. It will process each .png file and place the resulting .jpg files in the output_folder.
Now, create a PDF out of the new images and compress it again with PDF Squeezer. 


### how to do it on windows? 
❖ First You Need to Install Ghostscritp and Imagemagick and Add Them to System Variables. 
`**Note**` : the `gs` in unix = `gpcl6win64.exe` in windows
❖ You Can Check if Imagemagick Is Installed Usign This Command: 
```plaintext
convert.exe -version
```
❖ Now Let's Convert the Pdf to Separate Images
```plaintext
convert.exe -density 300 input.pdf -quality 90 output_prefix-%d.png
```
❖ Now We Need to Resize the Images We Will Use Bat Script for That
```plaintext
@echo off
setlocal enabledelayedexpansion

set "TARGET_WIDTH=900"

for %%f in (*.png) do (
    convert.exe "%%f" -resize !TARGET_WIDTH!x "resized_%%f"
)

echo Done resizing PNG images.

```
❖ Now Take the Resized Images, Put Them in New Folder and Let's Convert Them Back to a PDF
```plaintext
convert.exe -density 150 *.png output.pdf
```









