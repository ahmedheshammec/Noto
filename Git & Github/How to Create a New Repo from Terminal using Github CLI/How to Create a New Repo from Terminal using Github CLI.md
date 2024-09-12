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
❖ add R**EADME.md **file

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