Open it using the following command: 

```sh
open -a "Brave Browser.app" --args --disable-brave-update
```

→ Note that this only disable update check for this session only.

### Let's add this command to our ZSH Config

```sh
# Open Brave without Update Check

open-brave() {

local buffer="$BUFFER"

if [[ $buffer =~ '~brave$' ]]; then

BUFFER="open -a \"Brave Browser.app\" --args --disable-brave-update"

CURSOR=57 # Move the cursor to the position

fi

}
```

→ Don't forget to add `open-brave` to the wrapper function. 
