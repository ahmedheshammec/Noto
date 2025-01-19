
To check if there’s a new version of yt-dlp without updating it, you can query both GitHub and PyPI directly from the terminal. Here are the commands for each:

**1. Check on GitHub:**
Use curl or gh (GitHub CLI) to query the latest release from the yt-dlp repository:

• **Using** curl:

```sh
curl -s https://api.github.com/repos/yt-dlp/yt-dlp/releases/latest | grep '"tag_name"' | awk -F '"' '{print $4}'
```

This command fetches the latest release tag from the GitHub API.

• **Using** gh **(GitHub CLI)**:

```sh
gh release view --repo yt-dlp/yt-dlp --json tagName -q .tagName
```

The `gh CLI` fetches the latest release tag directly from the repository.

  

**2. Check on PyPI:**
  
Use pip or query the PyPI JSON API to check the latest version:

• **Using** pip:

```sh
pip search yt-dlp | grep yt-dlp
```

This shows the latest version of yt-dlp available on PyPI.
  
• **Using** curl **to query the PyPI API**:
  
```sh
curl -s https://pypi.org/pypi/yt-dlp/json | jq -r .info.version
```

This fetches the latest version from the PyPI API (requires `jq` for JSON parsing).

**Combine Both Checks (Optional):**

You can combine both GitHub and PyPI checks in a single script for convenience:


```sh
#!/bin/bash

# Check GitHub latest release
github_version=$(curl -s https://api.github.com/repos/yt-dlp/yt-dlp/releases/latest | grep '"tag_name"' | awk -F '"' '{print $4}')
echo "GitHub latest version: $github_version"

# Check PyPI latest version
pypi_version=$(curl -s https://pypi.org/pypi/yt-dlp/json | jq -r .info.version)
echo "PyPI latest version: $pypi_version"
```

Save this script, make it executable, and run it to see both versions.
