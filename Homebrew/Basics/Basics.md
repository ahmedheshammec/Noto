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


### How to show info about a specific cask?

Use the following command: 

```sh
brew info --cask <cask_name>
```

→ You will find a Github link search inside it for `homepage`

## How to Fetch the Source Install File to Use It Later?

use the following command: 

```zsh
brew fetch --cask {cask_name}
```

after the download process finishes it will be downloaded in the following directory: 

```
/Users/ahmed/Library/Caches/Homebrew/downloads/
```

to cleanup all files in the cache use the following command: 

```zsh
rm -r ~/Library/Caches/Homebrew/*
```

### 1. **Update `Homebrew` itself**

First, ensure that `Homebrew` is up to date by running:

```
brew update
```

This command fetches the latest version of `Homebrew` and updates the list of available formulae.

### 2. **Upgrade all installed formulae**

Once `Homebrew` is updated, you can upgrade all installed formulae (packages) to their latest versions using:

```
brew upgrade
```

This will upgrade all outdated packages to the latest versions available in the `Homebrew` repositories.

### 3. **Clean up old versions (optional)**

After upgrading, you may want to clean up old versions of installed formulae to free up disk space:

```
brew cleanup
```

This command removes older versions of installed formulae that are no longer needed.

**Fix Permission on Cleanup**

if you got an error like this: 

```
Error: Could not cleanup old kegs! Fix your permissions on: /opt/homebrew/Cellar/certifi/2024.8.30 /opt/homebrew/Cellar/[python@3.12](mailto:python@3.12) /3.12.6 /opt/homebrew/Cellar/yt-dlp/2024.8.6
```

We can fix it using the following command: 

```sh
sudo chown -R $(whoami):admin /opt/homebrew
```

