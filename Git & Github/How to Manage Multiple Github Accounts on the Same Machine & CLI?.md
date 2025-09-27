→ **Situation:** i had this main account: `ahmed.hesham8728@gmail.com` and i wanted to add my other business account `business.ahmedheshammec94@gmail.com` for testing purposes. 
→ I created an account for `business.ahmedheshammec94@gmail.com`, then i added a passkey for authentication. 

→ Now here's step by step Guide: 

**1- Generating a new SSH Key**

```bash
ssh-keygen -t ed25519 -C "business.ahmedheshammec94@gmail.com" -f ~/.ssh/id_ed25519_business
```

→ Since this account is my business account so i choosed the file to be named: `id_ed25519_business` to differ it from tmy main account that uses: `id_ed25519` 

**2- Add the new key to the SSH Agent**

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_business
```

**3- Add the new public key to GitHub**

→ First Copy the Key: 

```bash
pbcopy < ~/.ssh/id_ed25519_business.pub
```

→ Then paste it into **GitHub → Settings → SSH and GPG keys → New SSH key** for your business account.

**4- Configure `~/.ssh/config` (The Tricky Part)**

→ Create or edit the file:

```bash
code ~/.ssh/config
```

→ Added the following: 

```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/current_github_key
  IdentitiesOnly yes
```

**Notice**: we point to `~/.ssh/current_github_key` (a **symlink**) — that’s the trick.

**5- Create a Switch Script**
Make two small shell functions (you can put them in your `~/.zshrc` or `~/.bashrc`):

```bash
# Github Setup for Main & Business Accounts
gh_switch_main() {
  rm -f ~/.ssh/current_github_key
  ln -s ~/.ssh/id_ed25519 ~/.ssh/current_github_key
  ssh-add -D
  ssh-add ~/.ssh/id_ed25519
  echo "🔑 Switched to MAIN GitHub account"
}

gh_switch_business() {
  rm -f ~/.ssh/current_github_key
  ln -s ~/.ssh/id_ed25519_business ~/.ssh/current_github_key
  ssh-add -D
  ssh-add ~/.ssh/id_ed25519_business
  echo "🔑 Switched to Business GitHub account"
}

gh_whoami() {
  ssh -T git@github.com 2>&1 | grep "Hi "
}
```

→  Then reload your shell:

```bash
source ~/.zshrc   # or ~/.bashrc
```

**6- Usage**

→ Switch to main account:

```
gh_switch_main
```

→ Switch to business account:

```
gh_switch_business
```

→ Check which account is active:

```
gh_whoami
```

