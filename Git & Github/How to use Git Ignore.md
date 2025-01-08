**Ignore Untracked Files with `.gitignore`**

You can use a `.gitignore` file to tell Git which files and directories to ignore

→ Open your `.gitignore` file (or create one if it doesn’t exist) in the repository root:

```sh
code .gitignore
```

this will open `.gitignore` file in vs-code, but it won't be created until you save the file. 

→ Add the following rules to ignore everything except the `.zshrc` and `my-snippets.plugin.zsh` files: 

```zsh
# Ignore everything in the home directory
/*

# Allow specific files
!.zshrc
!my-snippets.plugin.zsh
!README.md

# Exclude the `.gitignore` file itself from being ignored
!.gitignore
```

→ next in your terminal do the following: 

```sh
git rm --cached -r .
git add .zshrc my-snippets.plugin.zsh README.md
```

→ Commit the changes: 

```sh
git commit -m "Set up .gitignore to track only .zshrc and my-snippets.plugin.zsh and README.md"
git push
```

