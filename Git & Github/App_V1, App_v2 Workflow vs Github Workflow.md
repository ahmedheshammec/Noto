Your current workflow of organizing app versions in folders with markdown files for detailed documentation is useful, but GitHub and Git itself offer more modern and efficient ways to manage version control and documentation. You can achieve similar goals without duplicating your files into versioned folders.

Here are some better approaches you can use within GitHub and Git to manage versioning, bug tracking, and documentation:

### 1. **Git Tags for Versioning**
Instead of organizing versions by folders, you can use **tags** in Git to mark specific commits as version releases.

- **What are tags?**: Tags in Git are lightweight references that you can use to label important points in your repository's history (like a version release).
- **How to use tags**:
  - After making changes and committing them, you can tag the commit with the version name:

```bash
git tag v1.0
```

    This tags the current commit as `v1.0` (or any other version label you choose).
  - You can also add tags to specific older commits using:

```bash
git tag v1.0 <commit-hash>
```


  - After tagging, push the tags to GitHub:

```bash
git push origin v1.0
```


- **Benefit**: With tags, you can easily reference any version of the app without needing to create separate folders. You can switch between versions using Git:

```bash
git checkout v1.0
```


### 2. **Detailed Release Notes with GitHub Releases**
You mentioned that commit messages are too short for documentation. GitHub provides a feature called **Releases**, which works perfectly with Git tags and allows you to document each version comprehensively.

- **What are releases?**: A GitHub release is a more detailed and formal way to capture information about a version, allowing you to include:
  - A **version tag** (e.g., `v1.0`)
  - A **detailed changelog** with explanations of features, bug fixes, and issues.
  - **Binary files** if you want to attach builds of your app.

- **How to create a release**:
  - After pushing a tag (e.g., `v1.0`), you can create a release on GitHub through the web interface:
    - Go to your repository on GitHub.
    - Click on **Releases** in the right-hand sidebar.
    - Click on **Draft a new release**.
    - Choose the tag (e.g., `v1.0`).
    - Write a detailed description of the version, including features, bug fixes, and known issues, just like you would in your markdown file.

- **Benefit**: Releases on GitHub are visible to everyone and give you a more structured way to manage your versions without duplicating directories for each version. You can still have long-form documentation like you're doing now, but in the release notes section.

### 3. **Using Branches for Development Workflows**
Another common method for managing versions in GitHub is to use **branches** for different versions or features:

- **How it works**: 
  - You can create branches to work on specific versions or features (e.g., `feature/add-login`, `bugfix/crash-on-load`, `v2-development`).
  - Once the changes are ready, you merge them into the `main` branch or a release branch like `release/v2.0`.

```bash
git checkout -b v2-development
# Make changes
git commit -m "Add feature X"
git push origin v2-development
```

- **Benefit**: This workflow allows you to work on multiple features or bug fixes in parallel without affecting the stable version of your app. Once a version is ready, you can merge the branch into the main branch and tag it with the release version.

### 4. **Using GitHub Issues for Bug Tracking**
Instead of listing bugs and issues in markdown files, you can use **GitHub Issues** to track them in a more organized way. Each issue can have:
  - A detailed description.
  - Labels (e.g., `bug`, `enhancement`, `feature`).
  - Comments and discussions.
  - Status tracking (open, closed).

You can link issues to specific commits and pull requests, making it easy to track the progress of bug fixes or feature implementations.

### 5. **GitHub Projects for Advanced Workflow Management**
GitHub also provides a **Projects** feature, which acts as a Kanban-style board where you can organize issues, pull requests, and tasks into columns (e.g., To Do, In Progress, Done).

- **Use case**: You can create a project for each app version and organize your tasks, bugs, and features visually, tracking their progress from start to finish.

---

### Summary of Workflow Improvement:
1. **Use Git tags** to version your releases instead of creating new folders for each version.
2. **Create GitHub Releases** to document the version in detail with a changelog (replacing your markdown files).
3. **Use branches** to work on new features, bug fixes, or version updates independently.
4. **Use GitHub Issues** for bug tracking and linking issues to commits or pull requests.
5. **Use GitHub Projects** for managing the overall workflow in a visual format.

By combining these features, you can maintain the detailed documentation and organization you're used to, but with more efficient and modern tools that GitHub offers, without the need for separate folders for each version.

---
## Real Implementation

we have the following project (stored in a backup folder) we need to take to backup: 

├── Odoo 16
├── Odoo 17
└── Odoo | Jupyter

→ Create a new folder on the desktop called `Version Control` for example. 

→ Open the terminal inside that folder and do the following: 

```sh
# Creating The Repo on Github
gh repo create odoo-development --public --description "Odoo development modules and study notes"
✓ Created repository ahmedheshammec/odoo-development on GitHub
  https://github.com/ahmedheshammec/odoo-development
```

```sh
# Initializing Git
git init
Initialized empty Git repository in /Users/ahmed/Desktop/Version Control/.git/
```

```sh
# Connect to remote Repo using SSH
git remote add origin git@github.com:ahmedheshammec/odoo-development
```

```sh
# Create and switch to the branch odoo-16
git switch -c odoo-16
Switched to a new branch 'odoo-16'
```

→ now copy the contents of odoo 16 directory (from the backup folder) to the version control folder (that has git) 

```sh
# adding, commiting, and pushing odoo 16 files. 
git add .
git commit -m "Add Odoo 16 modules and README"
git push origin odoo-16
```

```sh
# Creating new branch for odoo 17
git switch -c odoo-17
git commit --allow-empty -m "initial commit"
git push origin odoo-17
```

→ now manually delete the old odoo-16 files and copy the contents of odoo 17 directory (from the backup folder) to the version control folder (that has git)  

```sh
# adding, commiting, and pushing odoo 16 files. 
git add -u
git add .
git commit -m "Add Odoo 17 modules and README"
git push origin odoo-17
```

---

### Creating Releases with Tags

```sh
❯ git checkout odoo-16
Switched to branch 'odoo-16'

# Create a tag (recommended before creating a release)
❯ git tag -a v16.1.0 -m "Odoo 16 Course Unti The End"

# Create the release
gh release create v16.1.0 \
    --title "Odoo 16 Module Release" \
    --notes "Initial release for Odoo 16 Course Untill The End of The Course" \
    --target odoo-16
    
# Terminal Output: https://github.com/ahmedheshammec/odoo-development-testing/releases/tag/v16.1.0
```

### How to Delete Releases, Tags, Commits

#### Releases

To see all releases in your repository:

```sh
gh release list
```

→ press `q` to exit.

To delete a specific release:

```sh
gh release delete <release-name> --yes
```

→ Replace `<release-name>` with the name of the release you created.

→ Somethimes when you delete a release by name it gives error `release not not found` so instead we delete the release by tag: 

first we find the tag list: 

```sh
git tag
```

then delte the release by tag: 

```sh
gh release delete "v16.2.0" --yes

# ✓ Deleted release v16.2.0
# ! Note that the v16.2.0 git tag still remains in the repository
```

#### Tags

To list all tags

```sh
git tag
```

To delete a tag locally:

```sh
git tag -d <tag-name>
```

**Remove a Tag Remotely**

To delete a tag from the remote repository:

```sh
git push origin --delete <tag-name>
```

**Example Workflow**

If you have a tag named v1.0, you can delete it locally and remotely like this:

```sh
git tag -d v1.0
git push origin --delete v1.0
```

### Commits

To see a list of commits:

```sh
git log --oneline
```

`--oneline` shows a concise list with one commit per line.

For a more detailed view:

```sh
git log
```

→ **Soft Reset** (keeps changes staged):

```sh
git reset --soft <commit-hash>
```

→ **Mixed Reset** (unstages changes but keeps them in the working directory):

```sh
git reset --mixed <commit-hash>
```

→ **Hard Reset** (removes changes completely):

```sh
git reset --hard <commit-hash>
```

→ Note: to commit-hash you want to put the is the one you want to roll back to not the one you delete. so it's probably the one before the last one you want to delete. 

`PS Notes`: 

- use the command ` git branch -a | cat` to display branches to your terminal instead of a viewer.
- When you run `git branch -a`, it doesn't show any branches if you haven't made any commits yet. but you can commit an empty branch by using the command: 

```sh
git commit --allow-empty -m "Initial commit on <new-branch-name>"
git push origin <new-branch-name>
```

- `git switch -c <branch_name>`  creates the branch and switch to it and if you removed -c it will switch to the branch if it's already created. and it's the same as git checkout but it's safer cuz it's focused on branch swithching. 

---

### Resetting a Branch

```sh
git clean -fd
git reset --hard
git add -u
git commit -m "Clean up untracked and deleted files"
git push 
```

---

### Git Aliases

→ Git allows you to define custom aliases for commands in your Git configuration file.

```sh
git config --global --edit
```

❖ This will open the edit file in Vim which you can quit by typing `:qa`

❖ Alternatively we can open it in vs-code with this command: 

```sh
code ~/.gitconfig
```

→ Add the following under the [alias] section (or create one if it doesn’t exist):

```sh
[alias]
    st = status
```



Alternatively, set the alias directly with the command: 

```sh
git config --global alias.cm "commit -m"
```

Once set, you can use the alias git ci to commit with a message:

```sh
git cm "commit message"
```

→ you don't need to restart the shell for changes to take effect.

→ my aliases: 

```sh
[alias]
	st = status
	cm = commit -m
	p = push
	tga = tag -a
	tg = tag
	ll = log --oneline
```

---

### Renaming your Repo Through Terminal

You can rename the repository using the GitHub REST API. If you want to use the API with the gh CLI:

```sh
# Changing Repo Name from odoo-development-testing to odoo-development
❯ gh api --method PATCH /repos/ahmedheshammec/odoo-development-testing \
-f name=odoo-development

# Update local repo to the new URL (HTTPS Method)
❯ git remote set-url origin https://github.com/ahmedheshammec/odoo-development

# Update local repo to the new URL (SSH Method)
git remote set-url origin git@github.com:ahmedheshammec/odoo-development.git

# Verify The Change
❯ git remote -v
origin  https://github.com/ahmedheshammec/odoo-development (fetch)
origin  https://github.com/ahmedheshammec/odoo-development (push)
```

→ When you rename your repo through Github REST API you should see something like this: 

```sh
{
  "id": 915194534,
  "node_id": "R_kgDONozCpg",
  "name": "odoo-development",
  "full_name": "ahmedheshammec/odoo-development",
  "private": false,
  "owner": {
    "login": "ahmedheshammec",
    "id": 62020780,
    "node_id": "MDQ6VXNlcjYyMDIwNzgw",
    "avatar_url": "https://avatars.githubusercontent.com/u/62020780?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/ahmedheshammec",
    "html_url": "https://github.com/ahmedheshammec",
    "followers_url": "https://api.github.com/users/ahmedheshammec/followers",
    "following_url": "https://api.github.com/users/ahmedheshammec/following{/other_user}",
    "gists_url": "https://api.github.com/users/ahmedheshammec/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/ahmedheshammec/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/ahmedheshammec/subscriptions",
    "organizations_url": "https://api.github.com/users/ahmedheshammec/orgs",
    "repos_url": "https://api.github.com/users/ahmedheshammec/repos",
    "events_url": "https://api.github.com/users/ahmedheshammec/events{/privacy}",
    "received_events_url": "https://api.github.com/users/ahmedheshammec/received_events",
    "type": "User",
    "user_view_type": "public",
    "site_admin": false
  },
  "html_url": "https://github.com/ahmedheshammec/odoo-development",
  "description": "Odoo development modules and study notes",
  "fork": false,
:
```

→ Press `q` to exit