
### Fix Markdown
```plaintext
find . -type f -name "*.md" -exec sed -i '' 's/```/```/g' {} +
```
### Explanation:
❖ The Part with the Three Backslashes `=>` Before the Middle Back Slash Is the Text We Want to Replace (in This Case Three Backticks and a Space) and the Part After the Middle Back Slash Is the Text We Want to Replace It with (in This Case only Three Backticks)
### Remove Asterisk
```plaintext
# for html files
find . -type f -name "*.html" -exec sed -i '' 's/**//g' {} +

# for md files
find . -type f -name "*.md" -exec sed -i '' 's/**//g' {} +
```
# **Delete All PDF Files - HTML Files - Images Files
**```plaintext
# For PDF Files 
find . -type f -name "*.pdf" -delete

# For PDF Files 
find . -type f -name "*.html" -delete

# For Images Files 
find . -type f -name "*.jpg" -delete
find . -type f -name "*.jpeg" -delete
find . -type f -name "*.png" -delete
```
### Convert Markdown to PDF (Not the Best Option)
```plaintext
find . -name "*.md" -exec mdpdf {} \;
```
❖ NodeJs Must Be Installed First
❖ Then Install the Mdpdf Usign the Following Command:
```plaintext
sudo npm install -g mdpdf
```
### install weasyprint (The best option)
```plaintext
pip install weasyprint
```
### basic usage
```plaintext
from weasyprint import HTML

# Load the HTML file
html = HTML('input.html')

# Convert to PDF and save it
html.write_pdf('output.pdf')
```
❖ Don't Forget to Give Permissions to the Python File Before Running It. 
```plaintext
chmod +x weasy.py
python weasy.py
```
❖ To Add Codeblock Styling You Must Add the Following to the Html in the Style Tag: 
```plaintext
pre {
    background-color: #f4f4f4;
    padding: 10px;
    border-radius: 5px;
    overflow-x: auto;
}

code {
    font-family: "Courier New", Courier, monospace;
    color: #d63384;
}
```
### adding the css to all html files
```plaintext
find . -name "*.html" -exec sh -c '
for file do
    sed -i "" "/<style>/a\\
pre {\\
    background-color: #f4f4f4;\\
    padding: 10px;\\
    border-radius: 5px;\\
    overflow-x: auto;\\
}\\
\\
code {\\
    font-family: \"Courier New\", Courier, monospace;\\
    color: #d63384;\\
}\\
" "$file"
done
' sh {} +
```
adjusting the python code to work with all html files not just input and output 
```plaintext
import os
from weasyprint import HTML

# Get all HTML files in the current directory
html_files = [f for f in os.listdir() if f.endswith('.html')]

# Convert each HTML file to PDF
for html_file in html_files:
    html = HTML(html_file)
    output_pdf = f"{os.path.splitext(html_file)[0]}.pdf"
    html.write_pdf(output_pdf)

print("Conversion completed.")

```
now running the python file in all sub-directories 
→ first we will move the script to `myscripts` folder where every script is added to the path variable. 
→ we will edit the python file to be like this: 
```plaintext
#!/usr/bin/env python3
# To Use the the Script Open the Terminal and Cd to the Main Directory and Then Type `weasy.py .`

import os
import sys
from weasyprint import HTML

def convert_html_to_pdf(directory):
    html_files_found = False
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files_found = True
                html_path = os.path.join(root, file)
                pdf_path = os.path.splitext(html_path)[0] + '.pdf'
                
                try:
                    html = HTML(filename=html_path)
                    html.write_pdf(pdf_path)
                    print(f"Converted: {html_path} -> {pdf_path}")
                except Exception as e:
                    print(f"Error converting {html_path}: {str(e)}")
    
    if not html_files_found:
        print(f"No HTML files found in {directory} or its subdirectories.")

if __name__ == "__main__":
    print(f"Arguments received: {sys.argv}")
    
    if len(sys.argv) != 2:
        print("Usage: weasy.py <directory>")
        sys.exit(1)

    directory = sys.argv[1]
    print(f"Directory argument: {directory}")
    
    if not os.path.isdir(directory):
        print(f"Error: {directory} is not a valid directory")
        sys.exit(1)

    print(f"Converting HTML files in {directory} and its subdirectories...")
    convert_html_to_pdf(directory)
    print("Script execution completed.")
```
❖ To Use the the Script Open the Terminal and Cd to the Main Directory and Then Type
```plaintext
weasy.py .
```
# **Bash Script to Extract Noto Export Folder
**```plaintext
#!/bin/bash

# Function to display usage information
usage() {
    echo "Usage: $0 <directory>"
    exit 1
}

# Check if a directory was provided as an argument
if [ -z "$1" ]; then
    echo "Error: No directory provided."
    usage
fi

# Check if the provided argument is a valid directory
if [ ! -d "$1" ]; then
    echo "Error: The provided path is not a valid directory."
    usage
fi

# Get the directory path from the argument
DIR="$1"

# Move all files and subdirectories one level up
mv "$DIR"/* "$DIR"/../

# Check if the move was successful
if [ $? -eq 0 ]; then
    # Remove the original directory
    rm -r "$DIR"
    echo "Files moved and directory '$DIR' deleted successfully."
else
    echo "Error: Failed to move files."
    exit 1
fi
```
# **ZSH Snippet Function 
**```plaintext
# Append CSS Snippet to HTML Files
append-css() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~noto_css$' ]]; then
    BUFFER=$'find . -name "*.html" -exec sh -c \'\nfor file do\n    sed -i "" "/<style>/a\\\\\npre {\\\\\n    background-color: #f4f4f4;\\\\\n    padding: 10px;\\\\\n    border-radius: 5px;\\\\\n    overflow-x: auto;\\\\\n}\\\\\n\\\\\ncode {\\\\\n    font-family: \\"Courier New\\", Courier, monospace;\\\\\n    color: #d63384;\\\\\n}\\\\\n" "$file"\ndone\n\' sh {} +'
  fi
}
```



