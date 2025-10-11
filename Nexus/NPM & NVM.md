→ When you install a Node.js version via nvm install `<version>`, it also installs the matching npm version that comes bundled with that Node release.

→ You can install NVM using either **curl** or **wget**.
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

OR using wget:
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

→ After installation, **you must reload your shell** so that nvm becomes available.
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

→ if you're on homebrew you must change the NVM_DIR to homebrew's path: 
```bash
# configuring nvm
export NVM_DIR="$HOME/.nvm"
[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/opt/homebrew/opt/nvm/etc/bash_completion" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion"  # This loads nvm bash_completion
```

→ Verify installation
```bash
nvm --version
```

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

## Better Solution with ZSH Function

→ Use the following ZSH function: 

```bash
# ~/.zshrc  (or any file sourced by ~/.zshrc)
nv() {
  # ── current versions --------------------------------------------------------
  local cur_node cur_npm cur_nvm
  cur_node=$(node -v 2>/dev/null) || cur_node="—"
  cur_npm=$(npm -v 2>/dev/null)   || cur_npm="—"
  cur_nvm=$(nvm --version 2>/dev/null) || cur_nvm="—"

  # ── latest versions ---------------------------------------------------------
  local lat_node lat_npm lat_nvm
  lat_node=$(curl -s https://nodejs.org/dist/latest/ | sed -n 's/.*node-\([0-9.]*\)\.tar\.gz.*/\1/p')
  lat_npm=$(npm view npm version 2>/dev/null)
  lat_nvm=$(curl -s https://api.github.com/repos/nvm-sh/nvm/releases/latest | grep tag_name | cut -d'"' -f4)

  # ── pretty table ------------------------------------------------------------
  printf "\n%10s │ %15s │ %15s\n" "tool" "current" "latest"
  printf "%10s─┼─%15s─┼─%15s\n" "──────────" "───────────────" "───────────────"
  printf "%10s │ %15s │ %15s\n" "node" "${cur_node#v}" "$lat_node"
  printf "%10s │ %15s │ %15s\n" "npm"  "$cur_npm" "$lat_npm"
  printf "%10s │ %15s │ %15s\n" "nvm"  "${cur_nvm#v}" "${lat_nvm#v}"

  # ── upgrade hint ------------------------------------------------------------
  local hints=()
  [[ ${cur_node#v} != "$lat_node" ]] && hints+=("nvm install $lat_node && nvm alias default $lat_node")
  [[ $cur_npm != "$lat_npm" ]]       && hints+=("npm install -g npm@$lat_npm")
  [[ ${cur_nvm#v} != "${lat_nvm#v}" ]] && hints+=('curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/'"$lat_nvm"'/install.sh | bash')

  if (( ${#hints} )); then
    printf "\n💡  run:\n"
    printf "   %s\n" "${hints[@]}"
  else
    printf "\n✅  everything is up-to-date.\n"
  fi
}
```
