

	1.	Open your zsh configuration file in a text editor. The file is usually located at ﻿~/.zshrc.
	2.	Add the following line to the file: ﻿
	
```bash
export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

	1. Save the file and close the text editor.
	2. Run the command ﻿source ~/.zshrc to reload your zsh configuration.

After following these steps, the ﻿code command should work and allow you to open files in VS Code from the terminal while using the zsh shell.