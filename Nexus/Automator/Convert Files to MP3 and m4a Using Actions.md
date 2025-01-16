
→ Open automator app and create a new action

→ Set the `Workflow receives current` to `files or folders` in `Finder.app`

→ Set Image to `Audio Output` (This is the Image of the Quick Action).

→ Set the Color to Grey

→ From the side panel library choose `Run Shell Script` and add it to the right panel. 

→ in the `Run Shell Script` set the Pass input to `as arguments` 

→ Paste the following script and save it: 

```sh
#!/bin/bash
for f in "$@"; do
    # extract path from file variable 'f' and save it to 'pathname'.
    pathname=$(dirname "${f}") 
    
    # get filename without extension
    filename="$(basename -- "${f%.*}")"
    
    # construct command
    /opt/homebrew/bin/ffmpeg -i "${f}" "${pathname}/${filename}.mp3"
	osascript -e 'display notification "Coversion Successful" with title "Done!"'
done
```

→ The Notification Won't work Unless you do the following first:

→ Open Apple Scripts App and Create a New Document. 

→ Add the following code: 

```sh
display notification "Hello World"
```

→ Now click on the play button in the top right corner of the apple scripts app. 

→ Now you should get asked to allow notifications from Apple Script App. Click Allow

→ Now we can get back to Finder and right Click on any video file and from the Quick Actions sub-menu choose our the action we created and Voila!

`PS` Automator quick actions are saved in the following path: 

```
/Users/ahmed/Library/Services/
```

→ Now we can create a new quick action to convert to m4a: 

```sh
#!/bin/bash
for f in "$@"; do
    # extract path from file variable 'f' and save it to 'pathname'.
    pathname=$(dirname "${f}") 
    
    # get filename without extension
    filename="$(basename -- "${f%.*}")"
    
    # construct command
    /opt/homebrew/bin/ffmpeg -i "${f}" "${pathname}/${filename}.m4a"
	osascript -e 'display notification "Coversion Successful" with title "Done!"'
done
```

