
→ Set the `Workflow receives current` to `Images` in `Finder.app`

→ From the side panel library choose `Run Shell Script` and add it to the right panel. 

→ in the `Run Shell Script` set the Pass input to `as arguments` 

→ Paste the following script and save it: 

```sh
#!/bin/bash
for f in "$@"; do
    # extract path from file variable 'f' and save it to 'pathname'.
    pathname=$(dirname "${f}") 
    
    # construct command
    cd "${pathname}"
	input_filepath="${f}"
	output_iconset_name="output.iconset"
	/bin/mkdir $output_iconset_name

	/usr/bin/sips -z 16 16 $input_filepath --out "${output_iconset_name}/icon_16x16.png"
	/usr/bin/sips -z 32 32 $input_filepath --out "${output_iconset_name}/icon_16x16@2x.png"
	/usr/bin/sips -z 32 32 $input_filepath --out "${output_iconset_name}/icon_32x32.png"
	/usr/bin/sips -z 64 64 $input_filepath --out "${output_iconset_name}/icon_32x32@2x.png"
	/usr/bin/sips -z 128 128 $input_filepath --out "${output_iconset_name}/icon_128x128.png"
	/usr/bin/sips -z 256 256 $input_filepath --out "${output_iconset_name}/icon_128x128@2x.png"
	/usr/bin/sips -z 256 256 $input_filepath --out "${output_iconset_name}/icon_256x256.png"
	/usr/bin/sips -z 512 512 $input_filepath --out "${output_iconset_name}/icon_256x256@2x.png"
	/usr/bin/sips -z 512 512 $input_filepath --out "${output_iconset_name}/icon_512x512.png"

	iconutil -c icns $output_iconset_name

	rm -R $output_iconset_name
	osascript -e 'display notification "Coversion Successful" with title "Done!"'
done
```

