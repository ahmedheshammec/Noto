
First, turn off compression:
```plaintext
git config --global core.compression 0
```
Next, let's do a partial clone to truncate the amount of info coming down:
```plaintext
git clone --depth 1 <repo_URI>
```
When that works, go into the new directory and retrieve the rest of the clone:
```plaintext
git fetch --unshallow 
```
Now, do a regular pull:
```plaintext
git pull --all
```

