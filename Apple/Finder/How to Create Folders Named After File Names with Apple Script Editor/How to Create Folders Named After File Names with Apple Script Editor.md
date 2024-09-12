1. open script editor and create a new script.
2. paste this code. 
```plaintext
tell application "Finder"
 set selected to selection
 set current_folder to item 1 of selected
 set mlist to every file of current_folder
 repeat with this_file in mlist
  set cur_ext to name extension of this_file
  set new_name to text 1 thru -((length of cur_ext) + 2) of (name of this_file as text)
  set new_folder to make new folder with properties {name:new_name} at current_folder
  move this_file to new_folder
 end repeat
end tell
```
1. select your folder in finder. 
2. from the script editor; run your script. 

