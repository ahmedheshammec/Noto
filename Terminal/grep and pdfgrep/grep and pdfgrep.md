you can install pdf grep using homebrew: 

```zsh
brew install pdfgrep
```

and see the version using this command: 

```zsh
pdfgrep --version
```

:: __`Basic Usage`__ ::
To search for a pattern in all files within a directory: 

```zsh
grep "search pattern" /path/to/directory/*
```

`grep` or `pdfgrep`

:: __`Recursive Search`__ ::

```zsh
grep -r "search pattern" /path/to/directory
```

:: __`Case-Insensitive Search`__ ::

To search for a pattern case-insensitively, add the -i option:

```zsh
grep -ri "search pattern" /path/to/directory
```

:: __`Including Line Numbers`__ ::
To include line numbers in the output, use the -n option

```zsh
grep -rn "search pattern" /path/to/directory
```

:: __`Searching for Whole Words`__ ::
To search for whole words only, use the -w option:

```zsh
grep -rw "search pattern" /path/to/directory
```

:: __`Filtering by File Extension:`__ ::
To search only within specific file types (e.g., .txt files), use the --include option:

```zsh
grep -r --include="*.txt" "search pattern" /path/to/directory
```

:: __`Excluding Certain Files`__ ::
To exclude specific files or directories from the search, use the --exclude or --exclude-dir options

```zsh
grep -r --exclude="*.log" "search pattern" /path/to/directory
grep -r --exclude-dir="backup" "search pattern" /path/to/directory
```

:: __`Output File Names Only:`__ ::
To display only the names of files containing the match, use the -l option:

```zsh
grep -rl "search pattern" /path/to/directory
```

:: __`Search in Binary Files:`__ ::
By default, grep skips binary files. To search within binary files, use the -a option (which treats binary files as text):

```zsh
grep -ra "search pattern" /path/to/directory
```

