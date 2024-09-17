❖ This Error Usually Happens When You Try To Install A Python Package Like `ffmpeg` Using `homebrew` And It Installs A Newer Version Of Python With It. 

❖ To Fix This First You Need To Uninstall The Python Version That Was Downloaded Using `homebrew` And We Can Do This Using The Following Command: 

```zsh
brew uninstall --ignore-dependencies python@3.12
```

❖ Now We Need To Install `pyenv` Which Will Handle And Control All Python Versions To Install It Use The Following Command: 

```zsh
brew install pyenv
```

❖ Now Let's Install The Python Version Using `pyenv`:

```zsh
pyenv install 3.12.6
```

❖ To Check The Installed Versions Of Python Inside `pyenv` Use This Command:

```zsh
pyenv versions
```

❖ To Make This Version Global Use This Command

```zsh
pyenv global 3.12.6
```

→ This Sets Python 3.12.6 As The Default Version Used Across Your System

→ To Check The Python Version Now Active If It S The `pyenv` Version Or Not Run The Following Commands

```zsh
python -V
which python
```

→ You Should See An Output Like This 

```plaintext
Python 3.12.6
/Users/ahmed/.pyenv/shims/python
```

❖ To See All Python Versions Available For Installation Via `pyenv`, Run:

```zsh
pyenv install --list
```

❖ To Install The Latest Version Of Python 3 10 For Example Just Type

```zsh
pyenv install 3.10
```

`pyenv` Will Automatically Install The Latest Patch Release For Python 3 10 Which Means It Will Install The Highest Available Version Of Python 3.10.x.

### How To Set A Specific Python Version For A Project?

❖ Let S Say You Re Working With `odoo 17` Project And You Want When You Re Inside The `odoo 17` Folder The Python Version Is Set Automatically To Python 3 10 To Do This Go To The Project Folder And Type

```zsh
pyenv local 3.10.15
```

❖ This Creates A Python Version File In Your Project Directory When You're Inside That Directory Or Its Subdirectories The Python Version You Specified Will Be Used By Default

❖ When You Leave That Directory Your Global Python Version Will Be Used Again Unless You Set Another Local Version In The New Directory
