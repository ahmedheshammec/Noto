### How to Install

You can install it via homebrew like this: 

```shell
brew install ghostty
```

→ This will install both the cli and the cask 

### Where is the Config File?

In version 1.1.3 the config file is located in this location: 

```
/Users/ahmed/Library/Application Support/com.mitchellh.ghostty/config
```

### How to Choose Themes?

→ First Open Ghostty and type the following: 

```shell
ghostty +list-themes
```

→ This mode is just for previewing themes, when you find the theme you like copy it's name outside so we can add it later in the config file. 

→ To exit the theme list mode press the `esc` key. 
→ Some of my favourite Themes are: 

	↪ catppuccin-mocha
	↪ duskfox
	↪ Dracula+
	↪ electron-highlighter
	↪ Everblush
	↪ ForestBlue
	↪ Framer
	↪ Galaxy
	↪ GitHub-Dark-Default

→ To add the theme in the config add the following line: 

```
theme = GitHub-Dark-Default
```

→ Now you can `reload the config` through the terminal without restarting the terminal using the keys `⌘ + ⇧ + ,` 

### How to Customize Fonts?

→ First Open Ghostty and type the following: 

```
ghostty +list-fonts
```

→ Now add the following line to the config: 

```
font-family = MesloLGS NF
```

→ Reload the config using the keys `⌘ + ⇧ + ,` 
### How to Open Multiple Tabs on Ghostty? 

→ Use the keyboard Shortcut `⌘ + T`

### How to Make the Window Transparent?

→ Add the following lines to the config file: 

```
background-opacity = 0.7
background-blur-radius = 20
```

→ Reload the config using the keys `⌘ + ⇧ + ,` 
### How to Split Right and Down Like We Do in TMUX?

→ Add the following lines to the config file: 

```
keybind = cmd+f=new_split:down
keybind = cmd+d=new_split:right
```

→ Reload the config using the keys `⌘ + ⇧ + ,` 

→ Now `⌘ + D` will split right & `⌘ + D` will split down

### How to Make New Terminals Start in the Working Directory?

We need to enable shell integration, for example on our Mac we need to locate the zsh integration file of ghostty which we can find in this location: 

```
/Applications/Ghostty.app/Contents/Resources/ghostty/shell-integration/zsh/ghostty-integration
```

Next we need to source this file into our `.zshrc` file, Thus we will add the following line at the top of our `.zshrc` file: 

```
source /Applications/Ghostty.app/Contents/Resources/ghostty/shell-integration/zsh/ghostty-integration
```

→ Reload the config using the keys `⌘ + ⇧ + ,`  and try to split the current opened window to the right