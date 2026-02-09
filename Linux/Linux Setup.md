
```bash
sudo apt update
sudo apt install zsh
zsh --version
chsh -s $(which zsh)
```

→ Install "Oh My Zsh"

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

→ Install Build Dependencies

```bash
sudo apt update
sudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev \
libxml2-dev libxmlsec1-dev liblzma-dev python3-openssl git
```

→ Install pyenv

```bash
curl https://pyenv.run | bash
```

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

```bash
source ~/.zshrc
pyenv --version
```

### Postgres

```bash
sudo apt update
sudo apt install -y curl ca-certificates gnupg lsb-release
```

```bash
curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc \
  | sudo gpg --dearmor -o /usr/share/keyrings/postgresql.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/postgresql.gpg] \
http://apt.postgresql.org/pub/repos/apt \
$(lsb_release -cs)-pgdg main" \
| sudo tee /etc/apt/sources.list.d/pgdg.list
```

```bash
sudo apt update
sudo apt install -y postgresql-17 postgresql-client-17 postgresql-server-dev-17
```

```bash
sudo -u postgres createuser ahmed
sudo -u postgres psql -c "ALTER USER ahmed WITH SUPERUSER;"
sudo -u postgres createuser -s odoo
sudo -u postgres psql -c "ALTER USER odoo PASSWORD 'odoo';"
```


### Requirements

→ Run the following Outside any venv:

```bash
sudo apt update
sudo apt install -y \
  libsasl2-dev \
  libldap2-dev \
  libssl-dev
```

→ Now create the venv and install the requirements. 

### Running Odoo

```bash
sudo apt install -y wkhtmltopdf
```

### Setting Up Copy & Paste 

```bash
# Install xclip (most common/reliable)
sudo apt update
sudo apt install xclip xsel
```

→ in `.zshrc` 

```bash
# Add to ~/.bashrc
alias pbcopy='xclip -selection clipboard'
alias pbpaste='xclip -selection clipboard -o'
```

### Install VS-Code

```bash
# 1. Update package list
sudo apt update

# 2. Install prerequisites (you already did this)
sudo apt install software-properties-common apt-transport-https curl

# 3. Import Microsoft GPG key
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/microsoft-archive-keyring.gpg

# 4. Add VS Code repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list > /dev/null

# 5. Update package list again
sudo apt update

# 6. Install VS Code
sudo apt install code
```

