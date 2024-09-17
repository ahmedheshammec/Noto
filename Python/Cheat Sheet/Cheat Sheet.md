### :: **how to check python version ?** ::

open terminal and type either of these commands: 

```zsh
python -V
python --version
```

:: __`How to Install a Specific Version of Python`__ ::

Using `Homebrew` Use the Following Command: 

```plaintext
brew install python@3.12
```
This Will Install Python 3.12

### :: How To Know Where Python Is Installed ? ::

Create A New Python File In Vs Code With The Following Code And Run It: 
```python
import sys
print(sys.prefix)
```

### :: If You Have Multiple Versions Of Python ::

to check all installed versions of python run this command in terminal 

```zsh
ls /opt/homebrew/bin/python*
```

this list all versions installed by `homebrew`
to uninstall old versions of python use: 

```zsh
brew uninstall python@3.10
```

to check where is the path of a certain python interpreter type: 

```zsh
which python3.12
```

the 3.12 is the version you want to check 
now to set the default python interpreter to 3.12 do the following

open the `.zshrc` file and add this line: 

```zsh
alias python="/opt/homebrew/Cellar/python@3.12/3.12.1/bin/python3.12"
```

after saving source the `.zshrc` file in terminal for changes to take effect and then type 

```zsh
python -V
```

now to check for updates first check the python version let's say the output was Python 3.12.1
to upgrade type: 

```zsh
brew upgrade python@3.12
```
### :: How to Choose Python Interpreter in Vs Code? ::

now to fix the interpreter in vs code; launch vs code and press ⌘ + ⇧ + p  to open the command palette and search for: `Python: Select Interpreter` command and choose it. This command allows you to select the Python interpreter for your workspace.
From the list of available Python interpreters, choose the path corresponding to Python 3.12, which should now be available. If you don't see it, you may need to choose "Enter interpreter path" and provide the path to the Python 3.12 interpreter (/opt/homebrew/Cellar/python@3.12/3.12.1/bin/python3.12).
 
### :: Install Package within Virtual Environment **`venv`** ::

First To Create The Virtual Environment Type: 

```zsh
python3.12 -m venv ~/myvenv
```

This will create a virtual environment named ﻿myvenv in the user's home directory.
After creating the virtual environment, you can activate it to start using it:

```zsh
source /path/to/venv/bin/activate
```

to get out of a `venv` you can use the following command: 
```zsh
deactivate
```

so the command should be like this: 
```zsh
source ~/myvenv/bin/activate
```

After activation, you can install the ﻿`ffpb` package or any other Python packages within the virtual environment using ﻿pip.

```plaintext
pip install ffpb
python3.12 -m pip install pipx
pipx install ffpb
```

::`Note`:: If you prefer to install packages system-wide and are confident about the consequences, you can override the environment restriction by passing the ﻿`--break-system-packages` flag to the ﻿pip command:

```plaintext
python3.12 -m pip install --break-system-packages ffpb
```
### :: What Is The Difference Between Pip `And` `pipx` If We Just Used Pip Install `ffpb` Would That Have Worked ? ::

The main difference between ﻿pip and ﻿`pipx` is their primary purpose and functionality.
	1.	::﻿`pip`: ﻿`pip`:: is the default package manager for Python and is used to install Python packages. It installs packages into the Python environment that is associated with the Python interpreter used to run the command. When you use ﻿pip install `ffpb`, the package will be installed within the Python environment where ﻿pip is being executed.
	2.	::﻿`pipx`: ﻿`pipx`:: is a separate tool that extends the functionality of ﻿pip. It focuses on installing and managing Python-based command-line applications in isolated environments. It creates separate virtual environments for each installed application, ensuring that the application's dependencies do not interfere with other packages in your system's Python environment. When you use ﻿pipx install ffpb, it installs ﻿`ffpb` in its own isolated environment, making it easy to manage and run as a standalone command-line application.

In your specific case, using ﻿pip install `ffpb` may or may not have worked, depending on how the package is designed and whether it incorporates any command-line executable scripts. If ﻿`ffpb` is designed as a Python library without a separate command-line interface, using ﻿pip alone would install the package, but you might not be able to run ﻿`ffpb` as a standalone command.
By using ﻿pipx install `ffpb`, you ensure that the ﻿`ffpb` package is installed in its own isolated environment and that the command-line interface is accessible globally in your terminal.
In summary, if you only needed to use ﻿`ffpb` as a Python library, ﻿pip install `ffpb` may be sufficient. However, if you specifically want to use ﻿`ffpb` as a standalone command-line application, ﻿`pipx` install `ffpb` is recommended to ensure its proper installation and accessibility.

### ::  **Can I Install Other Package To `myvenv` In The Home Directory ? Or Every Package Gets A New `Venv`? ** ::

In a virtual environment created using ﻿venv, you can install multiple Python packages without creating a new virtual environment for each package. Once you have created a virtual environment, you can activate it and use ﻿pip to install any desired packages in that environment. This allows you to keep all installed packages separate from the system-wide Python installation and other environments.
You can use the same virtual environment (﻿myvenv in your case) to install and manage multiple packages. When you activate the virtual environment, any packages installed within that environment will be available to use. However, packages installed in one virtual environment will not be accessible from other virtual environments or the system Python installation.
To install other packages in your existing virtual environment (﻿myvenv), follow these steps:

	1.	Activate the virtual environment:
	▪	macOS/Linux:

```plaintext
source /path/to/myvenv/bin/activate
```

	▪	Windows:

```plaintext
C:\path\to\myvenv\Scripts\activate
```

	2.	Once the virtual environment is activated, you can use ﻿pip to install additional packages. For example:

```plaintext
pip install package1
pip install package2
```

By installing the packages within the active virtual environment, they will be isolated from other Python environments and can be used alongside the ﻿ffpb package you installed earlier.
Remember to activate the virtual environment (﻿myvenv) whenever you want to work with the installed packages.

### :: **How To Install Psd-Tools Using Git?** ::
Here's how you can do it:
	1.	Clone the repository: Run the following command to clone the ﻿psd-tools repository locally:

```plaintext
git clone https://github.com/psd-tools/psd-tools.git
```

	1. Navigate to the cloned repository: Change your current directory to the cloned ﻿psd-tools repository:

```plaintext
cd psd-tools
```

	1. Install ﻿psd-tools3: Now, use ﻿pip to install the library from the cloned repository:

```plaintext
pip install .
```

This will install ﻿psd-tools3 directly from the local cloned repository.
### :: How to run Python Scripts Like Bash Scripts From Anywhere in the Terminal ::
Add a shebang line at the top of your Python script.

```plaintext
#!/usr/bin/env python3
```

Make the Script Executable 

```plaintext
chmod +x your_script.py
```


#### :: __`Handling Multiple Versions of Python Using Pyenv`__ ::

To Install `Pyenv` Use the Following Command: 

```zsh
brew install pyenv
```

And Add These Lines to Your Shell Configuration File (Like ~/.zshrc or ~/.bash_profile):

```zsh
# Pyenv

export PATH="$PATH:/opt/homebrew/Cellar/pyenv/2.4.12/bin/"

eval "$(pyenv init --path)"

eval "$(pyenv init -)"
```

Verify `pyenv` is working

```zsh
which python
```

Next Let's Install a Python Version Through `Pyenv`: 

```plaintext
pyenv install 3.7.9
```

And Let's Make It the Global System Wide Active Python Version: 

```plaintext
pyenv global 3.7.9
```

Now We've Set up Python but Didn't Set Pip, to Set up Pip You Can Use: 

```plaintext
python -m pip <your command>
```

This Ensures You're Using the Pip Associated with the Current Python Version
**Check `pyenv's` global version

```zsh
pyenv global
```

:: __`How to Remove All Currently Installed Pip Packages?`__ ::
use the following command: 

```plaintext
pip freeze | xargs pip uninstall -y
```

:: __`How to Install the requirements.txt File`__ ::

use the following command: 

```plaintext
python -m pip install -r <your requirement.tx file>
```




 





 