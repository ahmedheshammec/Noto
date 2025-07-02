**Config Location On Mac**

```
/Users/ahmed/Library/Application Support/Claude/claude_desktop_config.json
```

create this directory on your mac: 

```
/Users/ahmed/Documents/Claude/
```

**Paste The Following Code in the JSON File**

```json
{
  "globalShortcut": "Shift+Alt+K",
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/Users/ahmed/Documents/Claude/"
      ]
    }
  }
}
```
