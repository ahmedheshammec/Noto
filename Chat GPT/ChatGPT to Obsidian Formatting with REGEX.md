### One Line Code Blocks

Find the Following: 

```
(^\s+)(```.+\n)(\s+)(.+\n)(\s+)(```)
```

And Replace It with This: 

```
\n$2$4$6\n
```

### Multi-Line Code Blocks

Find the Following: 

```
(\s\s)(```.+\n)((?:(\s)+.+\n)+?)(^\s.+)(```)
```

And Replace It with the Following: 

```
$2$3$6
```

This Removes White Spaces From Before the Backticks

Next Step Is to Search for the Following: 

```
^\s+
```

But Before We Replace We Need to Select the Code Block and Click the Button `Find in Selection` And Then Replace with Nothing