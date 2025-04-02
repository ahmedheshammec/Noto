* you can launch vs code by typing: 

```
code demo
```

`demo` Can Be Changed To Any File Name You Want. 

`F1`  >>> Apply Theme Or Execute Command.

`⌘ + K  then M`  >>> Change Language. 

`⌃ + ~` >>> Open Terminal

`⌘ +p` >>> search for files

`⌘+⇧+p` >>> Open The Command Palette

`⌘+c then ⌘+v`  >>> copy and paste lines without selecting

`⌘+x`  >>> remove one line

`⌥+⇧+up and down `  >>> repeat the line to the line below or before

`⌘ + j`  >>> fold / unfold the panels

`⌥+up or down` >>> move lines up or down in the hierarchy 

`⌘+d` >>> highlight the word and if you press ⌘+d again it will choose the next occurrence of that word

`⌘ +/`  >>> comment

`⌃+num` >>> switch between tabs

`⌘ +b`  >>> toggle the side bar 

`⌘ +\`  >>> split the editor

`⌥ +left click` >>> select multiple lines to edit them at the same time

`⌘ +⇧ +o` >>> get to variables and functions quickly

`⌘ + G` >>> open find and replace dialogue 

`⌃ + G` >>> go to line \[Helps with Debugging\]

`⌘ + ⇧ + X` >>> Open the Extensions view in VS Code 


### Select Between Tags

The Built-In Command Emmet: Balance (Outward) Does the Job but It Doesn't Have a Built in Shortcut but You Can Create Your Own From the Settings. (⇧ + ⌥ + E) Won't Make Any Conflicts.

:: __`HTML Emmet Abbreviations  Cheat Sheet`__ ::
This Emmet:

```
form#main>input#input[type=text]+input[type=submit value='Go']
```

will write code like this: 

```
<form id="main">
    <input id="input" type="text">
    <input type="submit" value="Go">
</form>
```

And This Emmet: 

```
form#main>input#main[type=text autocomplete=off]
```

will write code like this: 

```
<form id="main">
    <input type="text" id="input" autocomplete="off">
</form>
```

And This Emmet: 

```
button[onclick="confirmNavigation()"]{Open Google}
```

will write code like this: 

```
<button onclick="confirmNavigation()">Open Google</button>
```