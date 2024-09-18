to install `Homebrew` we need to install Xcode tools, open terminal and type: 

```zsh
xcode-select —-install
```

to install `Homebrew` go to their website 

```zsh
https://brew.sh/https://brew.sh
```

And Copy the Installation Code and Paste It in Terminal. 

Note: in M1 Mac Models, there’s additional steps after the install (you will find the steps in the terminal after the install is complete. 
you can type: 

```zsh
brew help
```

To Get Started 
to search `Homebrew` for formulae you can type: 

```zsh
brew search {input}
```

to search `Homebrew` for casks you can type: 

```zsh
brew search --cask {input}
```

to uninstall a package; simply type: 

```zsh
brew uninstall {input}
```

to list all packages that are installed type: 

```zsh
brew list
```

to see the info of a package and it’s dependencies type: 

```zsh
brew info {input}
```

to install adobe creative cloud for example type: 

```zsh
brew install adobe-creative-cloud —-cask
```

you can open the homepage of a cask like this: 

```zsh
brew home adobe-creative-cloud —-cask
```

#### Where Does `homebrew` Keeps All the Casks? 

In the Following Path: 

```plain
/opt/homebrew/Caskroom/
```

