→ Set the workflow to receive `folders` in `finder.app`

→ Set the image to `Quicklook` and the color to `Grey`

→ Add the following code in the Run Shell Script: 

```sh
#!/bin/bash

cd "$@"

find . -type f -name '*.eps' -exec /opt/homebrew/bin/gs -dSAFER -dBATCH -dNOPAUSE -dEPSCrop -sDEVICE=png16m -r600 "-sOutputFile={}.png" {} \;

osascript -e 'display notification "Coversion Successful" with title "Done!"'
```

