
→ Setup Command: 

```bash
npm install -g @anthropic-ai/claude-code
```


→ Check the version you have: 
```bash
claude --version
```

→ Check the latest published version on npm: 
```bash
npm view @anthropic-ai/claude-code version
```

→ If the two numbers differ, update to the newest release with:
```bash
npm update -g @anthropic-ai/claude-code
```

→ you can still change models via other means.

```
claude --model claude-sonnet-4-20250514  
claude --model claude-opus-4-20250514  
claude --model claude-3-5-haiku-20241022
```

or

```
/model claude-sonnet-4-20250514  
/model claude-opus-4-20250514  
/model claude-3-5-haiku-20241022
```

### How to Run Two Accounts on the Same Machine?

→ You can do this on separate terminals or the different window on the same terminal. 

→ Create separate config directories:

```bash
mkdir ~/.claude-account1
mkdir ~/.claude-account2
```


→ Add aliases to your shell config file:

```bash
nano ~/.zshrc
alias claude-account1="CLAUDE_CONFIG_DIR=~/.claude-account1 claude"
alias claude-account2="CLAUDE_CONFIG_DIR=~/.claude-account2 claude"
```

→ Save and reload:

```bash
source ~/.zshrc
```

→ Now you can simply run `claude-account1` or `claude-account2` and authenticate with each account. 

