### Mint

```bash
sudo apt update && sudo apt upgrade -y
sudo mintdrivers
sudo apt install mint-meta-codecs -y
sudo apt autoremove -y && sudo apt autoclean
sudo reboot
```


```bash
sudo apt update && sudo apt upgrade -y
sudo apt install zsh
zsh --version
chsh -s $(which zsh)
```


→ Install Git

```bash
sudo apt update
sudo apt install git
```

→ Install "Oh My Zsh"

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
which zsh
chsh -s $(which zsh) #change the default to be zsh
#Log out & log back in
echo $SHELL #verify after reboot
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

→ On Mint:
```bash
sudo nano /etc/apt/sources.list.d/pgdg.list
# Replace zena with noble
# deb http://apt.postgresql.org/pub/repos/apt noble-pgdg main
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

## Install PyCharm Community

```bash
sudo apt install flatpak -y

sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

flatpak install flathub com.jetbrains.PyCharm-Community -y

flatpak run com.jetbrains.PyCharm-Community
```