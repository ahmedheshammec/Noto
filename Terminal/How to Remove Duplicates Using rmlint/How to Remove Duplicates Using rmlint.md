:: __`install rmlint`__ ::
you can install `rmlint` by running the following command:

```plaintext
brew install rmlint
```

:: __`Verify the installation`__ ::
After the installation is complete, you can verify that `rmlint` is installed correctly by checking its version:

```plaintext
rmlint --version
```

:: __`Basic Usage`__ ::
To run `rmlint` on a directory, simply specify the directory path: 

```plaintext
rmlint /path/to/directory
```

This command will scan the specified directory and its subdirectories for duplicate files and other types of lint

Here are some common options you can use with `rmlint`:
:: __`Output to a log file`__ ::

```plaintext
rmlint /path/to/directory -o log
```

This will create a log file (`rmlint.json`) with the results.
:: __`Interactive mode`__ ::

```plaintext
rmlint -i
```

This option will open an interactive shell where you can review and act on the results
:: __`Delete duplicates automatically`__ ::

```plaintext
rmlint --delete
```

This will delete the duplicate files found by `rmlint`. Use this option with caution

:: __`Generating shell scripts`__ ::

```plaintext
rmlint /path/to/directory -o sh:script.sh
```

This will generate a shell script (script.sh) that you can review and execute to handle duplicates and other lint

:: __`Dry run mode`__ ::

```plaintext
rmlint --dry-run /path/to/directory
```

This will perform the scan without making any changes, useful for seeing what `rmlint` would do.
❖ Here are some advanced options and usage scenarios

:: __`Scan multiple directories`__ ::

```plaintext
rmlint /path/to/dir1 /path/to/dir2
```

:: __`Exclude specific directories`__ ::

```plaintext
rmlint /path/to/directory --exclude /path/to/directory/exclude
```

:: __`Only find duplicates`__ ::

```plaintext
rmlint --types=duplicates /path/to/directory
```

:: __`Handle multiple types of lint:`__ ::

```plaintext
rmlint --types=duplicates,emptydirs /path/to/directory
```

This will find both duplicate files and empty directories.
:: __`Specify output formats`__ ::

```plaintext
rmlint /path/to/directory -o json:output.json,pretty
```

This will output the results in both JSON format and a human-readable format.
### Example Workflow
:: __`Scan for duplicates and review`__ ::

```plaintext
rmlint /path/to/directory -o sh:script.sh
```

This scans for duplicates and creates a shell script for handling them.
:: __`Execute the script`__ ::

```plaintext
sh script.sh
```

