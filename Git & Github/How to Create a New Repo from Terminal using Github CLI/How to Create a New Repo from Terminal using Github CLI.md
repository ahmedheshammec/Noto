First You Need to Install the Gh Cli: 

```bash
brew install gh
```

Now We Need to Authenticate with Github Cli

```bash
gh auth login
```

choose to authenticate with the browser and http, then copy the code from the terminal and paste it into the browser. 
❖ **Navigate to Your Directory**: Open a terminal and navigate to the directory that you want to initialize as a new Git repository.

❖ add `README.md` file

```bash
echo -e "# Title\n\nThis is a description under the title." >> README.md
```

❖ **Initialize Git**: If the directory is not already a Git repository, initialize it by running:

```bash
git init
```

❖ **Add and Commit Files**: Add and commit the files in your directory to the Git repository:

```bash
git add .
git commit -m "Initial commit"
```

❖ **Create a New Repository on GitHub**: Use the **gh repo create** command to create a new repository on GitHub. This command will prompt you for the repository name, description, visibility, and other options:

```bash
gh repo create your_repo_name --public
```

❖ Follow the prompts to create the repository. If you want to specify the name and description directly in the command, you can use the **--name** and **--description** options:

```bash
gh repo create --name my-new-repo --description "My new repository"
```

❖ Now let's go to the main branch

```bash
git branch -M main
```

❖ And add origin

```bash
git remote add origin https://github.com/your_repo_link_without_git
```

❖ Before Pushing The Changes We Want to Set the Remote Url to SSH

```bash
git remote set-url origin git@github.com:ahmedheshammec/<repo>.git
```

❖ Now let's push the changes: 

```bash
git push -u origin main
```

❖ That's it! you can check the remote using this command: 

```bash
git remote -v
```


::**Now some Useful Cli Commands:: 
show the current repos: 

```bash
gh repo list
```

show the repo in the web browser

```bash
gh repo view Illustrator-Scripts --web
```

#### Now What if You Have a Repo Link Created in the Browser and You Want to Merge It with a Local Folder?

In My Case I Wanted to Push the Local Noto Folder to the Noto Repo on the Cloud

**Step 1: Clone the existing remote repository**

```bash
git clone https://github.com/ahmedheshammec/Noto.git
```

**Step 2: Add your local Noto folder's content to the cloned repository**

```bash
cp -r /path/to/your/local/Noto/* /path/to/cloned/Noto/
```

**Step 3: Stage the changes**

```bash
git add .
```

**Step 4: Commit the changes**

```bash
git commit -m "Add notes from local folder"
```

**Step 5: Pull the latest changes from the remote repository (just in case)**

To ensure your local repository is up to date before pushing:

```bash
git pull origin main --allow-unrelated-histories
```

The `--allow-unrelated-histories` flag is needed because the remote repository and your local folder are considered two different histories (due to the pre-existing README file).

#### Now Important step

Before Pushing and Since We're Pushing a Large Number of Files to Github It's Better to Use SSH over HTTPS and This Needs a Little Bit of Setup

**change the remote URL to SSH like this:**

```bash
git remote set-url origin git@github.com:ahmedheshammec/Noto.git
```

**Generate an SSH key (if you don’t already have one)**

```bash
ssh-keygen -t ed25519 -C "ahmed.hesham8728@gmail.com"
```

↪ When prompted, accept the default file location by pressing Enter.

↪ You can also choose to add a passphrase for extra security or leave it blank

**Add the SSH key to the SSH agent**

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

If you used a different name for the key during generation, replace `id_ed25519` with your key's name.

**Add the SSH key to your GitHub account**

Now, you need to add the newly generated SSH key to GitHub:

→ Copy the SSH key to your clipboard:

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

If you named the key differently, replace id_ed25519.pub with your key’s name.

→ Go to your GitHub account:

- Navigate to **Settings > SSH and GPG keys**.
- Click on **New SSH key**.
- Paste your SSH key and give it a title (e.g., "MacBook SSH key").
- Save the key.

**Test the SSH connection**

Test the connection to GitHub to verify that the SSH key is working correctly:

```bash
ssh -T git@github.com
```

If successful, you should see a message like this:

```plaintext
Hi ahmedheshammec! You've successfully authenticated, but GitHub does not provide shell access.
```

Finally Push your changes

```bash
git push origin main
```

### How to only Fetch The `.git` Directory From Github if It Was Removed?

❖ First, Navigate to Your Project Directory Where the .git Folder Was Lost, and Reinitialize the Repository:

```zsh
cd /path/to/your/project
git init
```

❖ Add the Original Repository URL Back as the Remote Origin:

```zsh
git remote add origin https://github.com/your_repo.git
```

This Will Reattach to the Original Remote Repository

You Can Verify the Remote With:

```zsh
git remote -v
```

❖ **Fetch the Original** .git **Data (without Overwriting Files)**:

```zsh
git fetch origin
```

❖ **Restore the State of the Repository**:

```zsh
git reset --mixed origin/main
```

❖ **See the Status of the Files**: 

```zsh
git status
```

❖ **Stage Your Changes**: 

```zsh
git add <modified_file>
```

❖ **Commit your changes**: 

```zsh
git commit -m "Restored .git and resumed work"
```

❖ **Push the Changes**: 

```zsh
git push -u origin main
```

