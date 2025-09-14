→ When you install a Node.js version via nvm install `<version>`, it also installs the matching npm version that comes bundled with that Node release.

→ To check the versions you have run those commands: 

```bash
nvm --version
npm --version
node --version
```

→ Check the latest available releases: 

```bash
curl -s "https://api.github.com/repos/nvm-sh/nvm/releases/latest" | grep tag_name
npm view npm version
nvm ls-remote | tail -5
```

→ Install the latest node version: 

```bash
nvm install 24.7.0
nvm use 24.7.0
nvm alias default 24.7.0
```