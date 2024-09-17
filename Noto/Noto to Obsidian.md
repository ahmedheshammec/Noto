```bash
file="content.md" ;extracted_name=$(head -n 1 "$file" | sed 's/^[[:space:]#]*//' ) ; mv "$file" "${extracted_name}.md" ; sed -i '' '1d' "${extracted_name}.md"
```

This Command Does the Following: 

❖ Stores the `content.md` in a Variable to Use Later in the Command

❖ Extracts the First Line in the Md File and Remove Any Leading White Space or # Mark and Store the Output in a Variable

❖ Renames the File From `content.md` To the New Name (First Line) We Extracted

❖ Removes the First Line From the Md File itself Cuz Obsidian Uses the Md File Name as a Title so This Way We Won't Have Duplicate Title Lines



The Bash Script that Automates This Process in a Main Directory: 

```bash
#!/bin/bash
# First Fix the Md Files Using the Find Command Before Running This Bash Script

# Check if a directory is provided as a parameter, if not use current directory
if [ -n "$1" ]; then
  target_dir="$1"
  cd "$target_dir" || { echo "Directory not found!"; exit 1; }
else
  target_dir=$(pwd)
fi

# Find all content.md files in the target directory and its subdirectories
find "$target_dir" -name 'content.md' | while read -r file; do
  # Extract the first line, clean it up, and use it as the new filename
  extracted_name=$(head -n 1 "$file" | sed 's/^[[:space:]#]*//')

  # Rename the file to the new name and remove the first line (the title)
  new_file_path="$(dirname "$file")/${extracted_name}.md"
  mv "$file" "$new_file_path"
  sed -i '' '1d' "$new_file_path"

  echo "Processed: $new_file_path"
done
```


## Adding Line Breaks in Obsidian for Readability: 

❖ Uniting All to Plain Text:

```
(```)\n(.+)(\n```$)
```

replaced with 

```
$1plaintext\n$2$3
```

the dollar sign represents the group `()` and the number refers to the number of group

❖ adding line breaks before and after the code block by searching for: 

```
(```(?:.|\n)*?```)
```

and replace it with: 

```
\n$1\n
```



