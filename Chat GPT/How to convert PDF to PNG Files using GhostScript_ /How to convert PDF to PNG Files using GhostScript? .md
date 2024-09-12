name the PDF input.pdf and type this command: 
```plaintext
gs -dNOPAUSE -dBATCH -sDEVICE=pngalpha -r300 -sOutputFile=output-%d.png input.pdf
```
Here’s what each option does:

	- -dNOPAUSE: This option prevents Ghostscript from pausing after each page.
	- -dBATCH: This option tells Ghostscript to process all pages without returning to the interactive prompt between each page.
	- -sDEVICE=pngalpha: This sets the output format to PNG with transparency (alpha channel).
	- -r300: This sets the resolution of the output file to 300 dots per inch (DPI).
	- -sOutputFile=output-%d.png: This sets the naming pattern for the output files. Ghostscript will replace %d with the page number.
❖ To Make the Png Images Doesn't Include the Alpha Channel We Can Set The `sDEVICE=ppm` Instead Of `pngalpha` 
With this command, Ghostscript will process the PDF and output each page as a separate PNG file named output-1.png, output-2.png, and so on, for each page of the PDF.

