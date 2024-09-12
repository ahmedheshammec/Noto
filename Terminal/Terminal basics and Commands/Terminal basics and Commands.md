
### :: **Basic Terms** ::
• shell = command line interpreter
• terminal = text input/output environment
• CMD = is the original shell for the Microsoft DOS operating system
• PowerShell = After CMD
### :: Navigation ::
to know where you are type

```bash
pwd
```

To Go Back type just like windows: 
```bash
cd ..
```

to make directory (i.e folder) type: 
```bash
mkdir "your folder name"
```

to quickly make multiple folders let's say 5
```bash
mkdir css js fonts imgs assets
```

if you want to make let's say folders named Day 1 , Day 2 .. Day 4 you can type: 
```bash
mkdir Day\ {1..4}
```
❖ the `\` backslash is there to escape the space

to make directory in the parent folder type: 
```bash
mkdir ../"your folder name"
```

to view the content of the directory you are at type: 
```bash
ls
```

to view all the content of a directory including the hidden files use
```bash
ls -all
```

or 
```bash
ls -a
```

to navigate use cd command just like windows: 
```bash
cd "your folder name"
```

to create .txt file type: 
```bash
touch "your text file name".txt
```

to open files  (like the txt file we just create it) using terminal type: 
```bash
open "your text file name".txt
```

**Move, Copy, Paste, Rename, Delete a file**
copy 
```bash
cp -r 
```
the -r refers to recursively (the directory with inside folders)

move
```bash
mv
```

to move all files into a parent folder 
```bash
mv * ../
```

to move all files from folder1  to folder2 for example (folder2 doesn't exist yet)
```bash
mkdir -p folder2 && mv folder1/* folder2/
```

rename
```bash
mv
```

delete files 
```bash
rm
```

to delete a directory type: 
```bash
rm -r "yoru directory name"
```

to copy file use this command: 
```bash
cp "your text file name".txt "new file name".txt
```

ps: you can use tab after typing cp to get the file name automatically just like windows. 
to rename type: 
```bash
mv "your old text file name".txt "your new text file name".txt
```

to copy a full directory with it's content type: 
```bash
cp -R "your directory name"/ "your new directory"
```

to force delete a directory type: 
```bash
rm -RF "your directory name"/
```

To clear the terminal window type: 
```bash
Clear
```

To Go to the Start of the Line
```bash
⌃+A
```

To Go to the End of the Line
```bash
⌃+E
```

To Move Between Words
```bash
⌥ + ← →
```

**Drag & Drop **
When you’re using “cd” command to navigate you can drag & drop your folders through finder directly to terminal window, it will automatically put the path to the folder for you. 

### :: add alias ::
add alias to md to make directories same as mkdir in mac os terminal 
if you're on zsh type: 
```bash
open -e ~/.zshrc
```
or 
```bash
nano ~/.zshrc
```
or 
```bash
code ~/.zshrc
```
this will open the .zshrc file

adding the alias: scroll to the end of the file and add: 
```bash
alias md='mkdir'
```

This line tells Zsh that whenever you type md, it should treat it as mkdir.
After editing the file in nano, you save it by pressing Ctrl + O, then Enter, and exit nano with Ctrl + X.

apply the chages to take effect by typing in your terminal: 
```bash
source ~/.zshrc
```

This command re-runs your .zshrc file, applying any changes you made.
To test if your alias works, try using md in the terminal to create a directory. For example:

```bash
md testDirectory
```
in windows you can type ipconfig to get your ip and other data, how can we do that on mac terminal? 
### :: **How to Activate 'Code' Command in ZSH to Create and Open Files with VS Code ** ::

	1.	Open your zsh configuration file in a text editor. The file is usually located at ﻿~/.zshrc.
	2.	Add the following line to the file: ﻿
	
```bash
export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

	1. Save the file and close the text editor.
	2. Run the command ﻿source ~/.zshrc to reload your zsh configuration.

After following these steps, the ﻿code command should work and allow you to open files in VS Code from the terminal while using the zsh shell.
### :: My ZSHRC File Aliases & Path Variables ::

```bash
aliasmd='mkdir'
aliaspip='pip3'
aliaspython='python3'
exportPATH=$PATH:/Users/Ahmed/Documents/Scripts
```
### :: How to Add Folder to Path Variable on Mac ::
To add a folder to the ﻿PATH variable on macOS, follow these steps:
	1.	Open Terminal, which you can find in the Utilities folder within the Applications folder, or by using Spotlight search.
	2.	In the Terminal window, type the following command and press Enter:
	
```bash
nano ~/.bash_profile
```

or 

```bash
code ~/.bash_profile
```
to open in vs code

	3.	This will open the ﻿.bash_profile file in the Nano text editor.
	4.	Within the Nano editor, add the following line at the end of the file:
	
```bash
export PATH="$PATH:/path/to/folder"
```

Replace ﻿/path/to/folder with the actual path of the folder you want to add.
	5.	Press Control + O to save the changes, then press Control + X to exit Nano.
	6.	Back in the Terminal, execute the following command to apply the changes:
	
```bash
source ~/.bash_profile
```

Now, the folder should be added to the ﻿PATH variable, and you should be able to use its executables or scripts from any Terminal window.
### :: IP Address and Location Information ::

```bash
curl ipinfo.io
```

This command will give you information such as your public IP address, the city and country you’re in, the name of your ISP, and more.

**Detailed IP Information:**
```bash
curl ip-api.com/jsonip-api.com/json
```

This provides detailed information about your IP, including latitude/longitude, timezone, and more.

**Just the Country:**
```bash
curl ipinfo.io/country
```

to copy the output of the terminal to the clipboard we will use **pbcopy** command 
```bash
some_command | pbcopy
```

For example, if you want to copy your public IP address to the clipboard, you can use:
```bash
curl ifconfig.me | pbcopy
```

there's this awesome website that has all terminal commands for windows, mac, linux and more 
https://ss64.com/

### :: how to list all folder sizes in the current directory ::

you can use this simple command to list all folders in the current directory: 

```bash
du -hd1 | sort -hr
```

if you want more advanced command that list all sub-directories and files you'll need to use ncdu (NCurses Disk Usage) by doing the following: 

```bash
brew install ncdu
```

Then you can run it in any directory:

```bash
ncdu
```
you can kill the command using ⌃ + C 

### :: Say Command ::

you can set the voice for spoken content in settings and open terminal and type: 

```bash
say "the words you want siri to say"
```

### :: Transfer / Upload Files Using Terminal ::

Since `transfer.sh` Is Down for Security Reasons; a Good Alternative Is `file.io` Which We Can Use with Curl to Upload and Get a Link. The Response Will Be Json so We Will Install `jq` And Pipe the Output to It so We Can Get a Readable Output

```bash
i="/your/file" ; curl --progress-bar --no-buffer -F "file=@$i" https://file.io | tee >(jq)
```

❖ We Can Also Create a ZSH Snippet for This as Follows: 

```bash
# Upload Files to File.io Using Curl and Tee
expand-upload() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~upload$' ]]; then
    BUFFER="i=  ; curl --progress-bar --no-buffer -F \"file=@\$i\" https://file.io | tee >(jq)"
    CURSOR=2  # Move the cursor to the position
  fi
}
```

❖ This Will Set the Cursor Right After the Equal Sign Allowing You to Type the First Letters of the File You Want to Download and Use the Tab Key to Get Zsh Completion (⚡)

### :: Ditto Command ::
Let's say you have 3 Folders Day 1, Day 2, Day 3 and you want to copy files from Day 1 & 2 to Day 3; to do that type: 

```bash
ditto 'Day 1' 'Day 3' | ditto 'Day 2' 'Day 3'
```
### :: Display Key Strokes ::

type: 
```bash
npx macos-key-cast
```

to kill the process press ⌃ +c

### :: Speed Test ::

open terminal and type: 
```bash
pip install speedtest-cli
```

after install you can type the command: 
```bash
speedtest-cli
```

you may need to add the python packages to your PATH: 
open ~/.zshrc using nano and add: 

```bash
export PATH="/Users/Ahmed/Library/Python/3.9/bin:$PATH"
```

Save and reload the terminal using 

```bash
source ~/.zshrc
```
### :: how to know the location / directory of every package you installed ::
just type `whereis` which is  a linux command: 
examples: 
```bash
➜  Desktop  whereis ffmpeg
ffmpeg: /opt/homebrew/bin/ffmpeg /opt/homebrew/share/man/man1/ffmpeg.1
➜  Desktop  whereis brew
brew: /opt/homebrew/bin/brew /opt/homebrew/share/man/man1/brew.1
➜  Desktop  whereis ffpb
ffpb: /opt/homebrew/bin/ffpb
➜  Desktop  whereis ef.sh
ef.sh: /Users/Ahmed/Documents/Scripts/ef.sh
➜  Desktop  whereis pip
pip: /opt/homebrew/bin/pip
```

### ::Executing Scripts From Specific Directory Without Copying::
if we have a folder that is already added to the path variables in your system and this folder contains a bunch of bash scripts; then we can make a little trick to run this script from anywhere without the need to copy the script file to location you want
we will add this simple code in the start of the script: 

```bash
location=$1
cd"$location"
```

so now all we have to do is to make the script executable just for one time in the script folder and when we run the script from anywhere in the drive we just give it the location which we want to execute the script from and the script will automatically jump into the directory you entered and execute the rest of the script

```bash
convert.sh 'user/document/folder/'
```

this is basically saying execute the convert.sh script in the directory `user/document/folder/`
### :: How To Upgrade Your Terminal Game :: 

First Install Oh My Zsh Through This Link: 
```bash
https://ohmyz.sh/
```

now we're gonna install the best theme which is `powerlevel10k` 
Github Link: https://github.com/romkatv/powerlevel10k#fonts

First Install The Fonts 
after that open terminal and paste this: 

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

after going with the install here's the last window
![image](351A41AC-C759-47A4-A9EF-584AEFEE9AA8.jpg)

if you want to re-choose your config just type in the terminal

```bash
p10k configure
```

and source the `zshrc` file for changes to take effect. 
now it's time to install `zsh-syntax-highlighting` 

Github Repo: https://github.com/zsh-users/zsh-syntax-highlighting

look for oh my zsh install in the `install.md` file and to activate the plugin edit the `zshrc` file. you'll see the git plugin already there; we just have to add the new one next to it 

```bash
plugins=(git zsh-syntax-highlighting)
```

like this and source the `.zshrc` file to reload and you should be good to go; open terminal and type: 
```bash
echo "Hello World"
```

### :: **Cat Command** ::

you can create a new file using the cat command like this: 

```bash
cat > demo.txt
```

you can now add text to the demo.txt file from the terminal, when you're done press control + D  twice to Exit. 

to append text to the file demo.txt 
```bash
cat >> demo.txt
```

now you're in edit mode again
to show the content of demo.txt in the terminal

```bash
cat demo.txt
```

to move all content from demo.txt to a new test.txt file for example 
```bash
cat demo.txt > test.txt
```

to clear the content of a file using cat 
```bash
cat /dev/null > filename.txt
```
### :: `How to Add Snippets to your Terminal for Single and Double Quotes` ::

* Open your ﻿.zshrc configuration file using a text editor:
* Add the following lines at the end of the file:

```bash
quote_double() {
    LBUFFER+='""'
    CURSOR=$((CURSOR-1))
}
zle -N quote_double

quote_single() {
    LBUFFER+="''"
    CURSOR=$((CURSOR-1))
}
zle -N quote_single

bindkey '"' quote_double
bindkey "'" quote_single
```

These lines define two functions, ﻿quote Double and ﻿quote_single, which handle the insertion of double quotes and single quotes, respectively. The ﻿zle -N command makes the functions available as widgets for binding. The ﻿bindkey commands bind the functions to the double quote (﻿") and single quote (﻿') keys.
Save the changes and exit the text editor.

To apply the changes, either restart your terminal or run the following command:

```bash
source ~/.zshrc
```

### how to make bash the default shell?
use this command: 
```bash
chsh -s /bin/bash
```

### How to Pass the Output of a Command to Another Command ? 

Let's Say We Want to Pass the `Pwd` Output to the `rename.sh` Script so that It Will Rename All the Files in the Current Working Directory; to Do This We Can Use a Simple Command Like This: 

```bash
rename.sh "$(pwd)"
```

### How to Use Multiple Line Commands in Zsh? 

❖**First Method**: Put the Commands in a Text Editor First Then Copy Paste Them to the Terminal

```bash
pwd
echo "Hello"
```

❖ **Second Method**: one line command 
```bash
zsh -c 'echo "Hello"; pwd; echo "World"' 
```

**Explanation:**
* **`zsh -c`**: This tells ZSH to execute the following command as a single unit.
* **`echo "Hello"; pwd; echo "World"`**:  This is your multi-line command, separated by semicolons (`;`). Each line will be executed in sequence. 

but what about something like loops; something like this: 

```bash
for (( i=0; i<=5; i++ )); do
    echo $i
    sleep 1
done
```

❖ We Can Use One Line Commands Like This: 
```bash
for (( i=0; i<=5; i++ )); do echo $i; sleep 1; done
```

❖ we can also use curly braces: 
```bash
{
for (( i=0; i<=5; i++ ))
do
    echo $i
    sleep 1
done
}
```

❖ First Type the Open Brace and Hit Enter, Then Type Each Line and Hit Enter, and at Last Type the Closing Brace and Hit Enter and the Command Will Work. 
❖ You Can Replace the Curly Braces with Parentheses 
❖ We Can Also Use Backslash with Semicolins 

```bash
❯ for (( i=0; i<=5; i++ )); do
for> echo $i; \
for> sleep 1; \
for> done
```

❖ Hit Enter After `do` And You Will See The `for>` In the Next Line.
❖ At the End of the Echo and Sleep Commands Add Semicolin and Space and the Backslash Then Hit Enter

The Output:
```bash
0
1
2
3
4
5
```

### How to Create Snippets in ZSH?
Here's an Example that Expands `~hello` and `~~goodbye` To a Full Text with Custom Cursor Position:

```bash
# Define the expansion function for ~hello
expand-hello() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~hello$' ]]; then
    BUFFER="hello have a nice day"
    CURSOR=6  # Move the cursor to the position after 'hello '
  fi
}

# Define the expansion function for ~goodbye
expand-goodbye() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~goodbye$' ]]; then
    BUFFER="goodbye have a great day"
    CURSOR=8  # Move the cursor to the position after 'goodbye '
  fi
}

# Create a wrapper function that calls both functions
expand-snippets() {
  expand-hello
  expand-goodbye
}

# Bind the wrapper function to a key combination, e.g., Ctrl+H
zle -N expand-snippets
bindkey '^H' expand-snippets  # Change this to your preferred key combination
```
### Explanation: 

❖ The `cursor` Starts the Count From Zero
❖ The `Wrapper Function` Is Used because We Bind Both Functions with the Same Key Combination `⌃+H` , So It Calls Both Functions and Then the if Conditions Kicks in and Correspond to the Right Buffer (Word You Typed in the Terminal)
❖ We Can Change The  `⌃+H` Bind Key to another Key as Follows:

```bash
bindkey '`' expand-snippets  # we are using backtick (the telda key)
```

❖ It's Recommended to Stay Away From the Tab Key Cuz It's Used to Auto-Complete File Names
❖ We Can Check Percisely the Cursor Position Number We Want by Copying the Command to a New Vs-Code Docoument and Look in the Bottom Right Corner You Will See Something Like `Ln 1, Col 20` and as You Move the Cursor the `Col 20` Will Change, but Vs-Code Starts Counting From 1 so Whatever Number Vs-Code Have We Should Subtract 1 From It to Get the Right Cursor Number.
❖ The Function Name Can't Be the Same as a Command Otherwise the Command Will Not Work

### Extra Steps I Take

❖ I Created a New ZSH File in My Home Directory with the Touch Command

```bash
touch my-snippets.plugin.zsh
```

And Sourced that File in The `ZSHRC` File by Adding the Following Line:

```bash
source /Users/Ahmed/my-snippets.plugin.zsh
```

`VIP Note`: It's Importat to Put the Full Path to the New ZSH File, Otherwise It Might Create Issues with Somehting Like the Cd App, Cuz It Will Create a New Terminal at a Different Location and Won't See the Sourced File

❖ The New File Will Contain All the Snippets

### Generating Five Random Digits in ZSH

```bash
RANDOM=$(( $(date +%s) % 32768 ))
randomNumber=$(printf "%05d" $((RANDOM % 100000)))
echo "${randomNumber}"
```

This seeds the `**RANDOM**` variable with the current time in seconds, ensuring that you get a different sequence of random numbers each time you run the script.

### How to Manipulate Files Naming in ZSH?

Let's Assume You Made a File Using the Touch Command: 

```bash
touch someFile.txt
```

We Can Store that File in a Variable and Then Manipulate the Output Later, but First Let's Try a Little Test to Extract Each Part of the File: 

❖ Let's Start with the File Name only without the Extension

```bash
i=someFile.txt ; echo ${i%.*}
```

This Will Extract only the File Name `someFile` And Print It in the Termianl

**Explanation**
**`%` The Percent Mark Tells Zsh to Remove From `{i}` The Variable Whatever Comes After the Percent Mark.
`.*` The Dot Represents the Dot in the File Extension and the Asterisk Plays as a Wild Card to Match Any Extension Comes After the Dot.

❖ Next Lets Extract the Extension only From the File:

```bash
i=someFile.txt ; echo ${i##*.}
```

this will print only txt to the terminal but what did we do in the echo command: 
`##` This Is a Special Character in Shell Commands that Acts as a "String-Slicing" Tool. It Tells the Shell to Remove Everything From the Beginning of the String (I) Until the First Occurrence of a Period (.)
**The **`*`** as a wildcard:** In this context, the asterisk acts like a "wildcard" that matches any character (including zero characters) *before* the period (.)
❖ We Can Add the Dot Manually to Be Printed on the Screen so the Output Will Be `.txt` Instead of Just `txt` 

```bash
i=someFile.txt ; echo ."${i#*.}"
```

❖ With These Tools You Can Easily Manipulate Files Naming

### If There's a File in Use What Command Can I Use to Show the Process That's Using that Folder or File? 
You can use the `lsof` (List Open Files) command to find out which process is using a specific file or folder. Here's how you can do it:

`To find the process using a specific file:`

```bash
lsof /path/to/file
```

`To find the process using a specific folder:`

```bash
lsof +D /path/to/folder
```

This command will list all processes that are using the specified file or folder. The output will include the process ID (PID), user, and command name associated with the process.

`To filter the output for easier readability, you can use:`

```bash
lsof /path/to/file | grep -i "filename"
```
or
```bash
lsof +D /path/to/folder | grep -i "foldername"
```

This command can be useful for identifying processes that may be locking a file or directory, preventing you from performing operations like deleting or moving it.

### How to Count How Many File with a Specific Extension in a Main Directory Recursively (Including Sub-Directories)?

```bash
find "$(pwd)" -type f -name "*.mkv" | wc -l
```
❖ This Will Count How Many Mkv Files Are There in that Main Directory Recursively and Print the Number in the Terminal. 

❖ We Can Combine This Logic in a Zsh Function Like This: 

```bash
# Count How Many File with a Specific Extension in a Main Directory Recursively
expand-count() {
  local buffer="$BUFFER"
  if [[ $buffer =~ '~count$' ]]; then
    BUFFER="find \"\$(pwd)\" -type f -name \"*.\" | wc -l"
    CURSOR=31  # Move the cursor to the position
  fi
}
```






