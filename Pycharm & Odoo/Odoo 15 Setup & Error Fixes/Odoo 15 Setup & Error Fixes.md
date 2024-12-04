❖ First Things First: The Python Version that Worked for Me Is Python@3.10.14
❖ To Make Everything Run Smooth Create a Virtual Environment Inside Odoo Folder Using the Following Command: 

```
python -m venv .venv
```

❖ This Will Create a Hidden Venv File in the Odoo Odoo, Now We Need to Activate It

```
source /Users/Ahmed/Documents/odoo15-15.0/.venv/bin/activate
```

❖ Now Let's Check that There's No Lists Installed Using the Following Command: 

```
python -m pip list
```

❖ Next Let's Install the Requirements in the requirements.txt File Using the Following Command: 

```
python -m pip install -r <path to the requiremtns file>
```

❖ Next Add the Following Lines in the Confing Under the Debian Directory: 

```
addons_path = /Users/Ahmed/Documents/odoo15-15.0/addons,/Users/Ahmed/Documents/odoo15-15.0/custom_addons
limit_memory_hard = 0
limit_memory_soft = 0
```

❖ Now Let's Launch the Server:

```
python odoo-bin -c /Users/Ahmed/Documents/odoo15-15.0/debian/odoo.conf
```

❖ If You Encountered a Problem Like This: `ValueError: current limit exceeds maximum limit`  Do the Following:
1. Open Terminal.
2. Type `sudo -i` and enter your password to switch to the root user.
3. Type `launchctl limit maxfiles` to check the current limit on the maximum number of open files.
4. Type `launchctl limit maxfiles 65536 200000` to set the limit to 65536 for the current session and 200000 for future sessions.
5. Type `launchctl limit maxproc` to check the current limit on the maximum number of processes.
6. Type `launchctl limit maxproc 2048 4096` to set the limit to 2048 for the current session and 4096 for future sessions.
7. Type `ulimit -n` to check the current limit on the maximum number of open file descriptors.
8. Type `ulimit -n 65536` to set the limit to 65536.
9. Type `exit` to switch back to your regular user account.
### 
### Installing Postgres@13
This Is the Version of Postgres that Is Specifically Mentioned in Odoo's Documentation and Is Known to Be Compatible and Stable with Odoo 15.
To Install Use the Following Command: 

```
brew install postgresql@13
```

To Check the Version of Postgres Currently Running Type:

```
psql --version
```


:: __`If I Have Postgres 16 and 13 How Can I Move Back and Forth Between the Two ?`__ ::
❖ First Let's Stop the Postgres 16 Service:

```
brew services stop postgresql@16
```

❖ Now Let's Start the Postgres 13 Service:

```
services start postgresql@13
```

next we need to link `psql` command to postgres13 not 16, we can set it manually like this: 

```
export PATH="/opt/homebrew/Cellar/postgresql@13/13.15/bin:$PATH"
```

But for Convenience We Will Add the Following Alieases to Our `.zshrc` File: 

```
# postgres aliases
alias use_postgres_13='export PATH="/opt/homebrew/Cellar/postgresql@13/13.15/bin:$PATH"'
alias use_postgres_16='export PATH="/opt/homebrew/Cellar/postgresql@16/16.2_1/bin:$PATH"'
```

Now You Can Use Any of the Aliases to Go Back and Forth Between Different Versions of Postgres.
also you can check the running postgres using the following command: 

```
psql --version
```

next you need to create role odoo in in the postgres and give it permission to create database.
if you encounter the following error: `OSError: [Errno 48] Address already in use ` you need to shut down the processes that uses 8069 port. 

:: __`Fixing X509_V_FLAG_NOTIFY_POLICY Error `__ ::
The problem is with cryptography and pyopenssl libraries.change requirements.txt as:
go to terminal and:
`pip uninstall pyopenssl`
`pip install pyopenssl==22.0.0`
`pip uninstall cryptography`
`pip install cryptography==37.0.0`