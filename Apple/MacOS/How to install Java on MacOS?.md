

```
brew install openjdk@17
```

→ Link Java correctly (IMPORTANT on macOS)

```
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk \
  /Library/Java/JavaVirtualMachines/openjdk-17.jdk
```

→ Then add it to your shell:

```
echo 'export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

→ Verify Java is installed

```
java -version
```

