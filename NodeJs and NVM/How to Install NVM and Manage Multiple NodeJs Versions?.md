
### Important:

❖ It's Better to Remove Any Node Was Previously Installed by Brew Since Nvm Is Better and Doing Both Can Lead to Conflicts.

❖ First Install Node `nvm` Using `brew`: 

```zsh
brew install nvm
```

❖ Next We Need to Configure It on Our `.zshrc` File; Add the Following Lines and Source for Changes to Take Effects.

```zsh
# configuring nvm

export NVM_DIR="$HOME/.nvm"

[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh" # This loads nvm

[ -s "/opt/homebrew/opt/nvm/etc/bash_completion" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion" # This loads nvm bash_completion
```

❖ Now for some Useful Commands: 

1. **Install a Specific `Node.js` Version**:

```bash
nvm install <version>
```

Example:

```bash
nvm install 16.20.0
```

This command installs the specified version of Node.js. You can also use `nvm install node` to get the latest version.

2. **List Installed Versions**:

```bash
nvm ls
```

This command lists all the Node.js versions installed on your system, highlighting the active version.

3. **Use a Specific Node.js Version**:

```bash
nvm use <version>
```

Example:

```bash
nvm use 18.17.0
```

This command switches to the specified Node.js version for your current session.

4. **Check the Current Node.js Version**:

```bash
nvm current
```

This command shows the currently active Node.js version.

5. **Set Default Node.js Version**:

```bash
nvm alias default <version>
```

Example:

```bash
nvm alias default 14.21.3
```



5 more useful `nvm` commands:

1. **Uninstall a `Node.js` Version**:

```bash
nvm uninstall <version>
```

Example:

```bash
nvm uninstall 16.20.0
```

This command removes the specified version of Node.js from your system.

2. **List Available Remote Versions**:

```bash
nvm ls-remote
```

This command lists all the available Node.js versions that can be installed using `nvm`.

3. **Run a Specific Version Temporarily**:

```bash
nvm run <version> <file.js>
```

Example:

```bash
nvm run 14.21.3 app.js
```

This command runs a specified Node.js file using a specific Node.js version without changing the currently active version.

4. **Check the Latest LTS (Long-Term Support) Version**:

```bash
nvm ls-remote --lts
```

This command lists the latest LTS versions available for Node.js, which are often recommended for production.

5. **Reinstall Packages from One Version to Another**:

```bash
nvm reinstall-packages <version>
```

Example:

```bash
nvm reinstall-packages 16.20.0
```

This command reinstalls global `npm` packages from the specified version of Node.js into the currently active version, useful when switching versions frequently.