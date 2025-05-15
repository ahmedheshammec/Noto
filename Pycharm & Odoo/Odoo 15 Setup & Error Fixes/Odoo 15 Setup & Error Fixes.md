### Debugging

Here's some useful terminal commands used in the debugging: 

→ **Redirect to a log**

```
pip install libsass==0.17.0 > log.txt 2>&1
```

→ **Copy log content to clipboard**

```
cat log.txt | pbcopy
```

→ **Uninstall a specific Package**

```
pip uninstall lxml==4.5.0
```

→ **List a Specific Package From Pip List**

```
pip list | grep "lxml"
```

### Best Workflow to Fix Setup Errors

1- start by creating a virtual environment then activate it using a recommended python version for the odoo server you want to run (Scroll Down for Code 👇)

2- Run the following command

```
pip install -e .
```

→ If you got errors running this command, switch to a different version of python until it gives you no errors. 

→ After running this command open `requirements.txt` and open the output of the `pip list` command **side by side** in vs-code. 

→ Go through each package in the requirements and see if it's installed in the pip list output, if it's not installed install it. 

→ After you're done with list try running the server with the **base** module using the following command: 

```
python odoo-bin -c odoo13-bahy.conf -d odoo13-bahy -i base
```

**PS** you might get some errors at this point related to some packages needs to downgraded to a compatible module. in this case delete the installed version, install the compatible one, and retry.

→ Now if you're successful running the base module try running the following command: 

```
python odoo-bin -c odoo13-bahy.conf -d odoo13-bahy
```

→ Now you're good to go 👍 🚀

---
❖ To delete every installed pip package on your environment run: 

```
pip freeze | xargs pip uninstall -y
```

❖ To Make Everything Run Smooth Create a Virtual Environment Inside Odoo Folder Using the Following Command: 

```
python -m venv .venv
```

❖ This Will Create a Hidden `Venv` File in the Odoo Odoo, Now We Need to Activate It

```
source .venv/bin/activate
```

❖ Now Let's Check that There's No Lists Installed Using the Following Command: 

```
python -m pip list
```

```
python -m pip install --upgrade pip setuptools wheel
```

❖ Next Let's Install the Requirements in the requirements.txt File Using the Following Command: 

```
pip install -r requirements.txt
```

or try the following command with different python versions: 

```
pip install -e .
```

Which Installs the current project in editable mode

→ You may need to install the following: 

```
pip install "lxml[html_clean]"
pip install lxml_html_clean
pip install gevent psycopg2-binary pillow reportlab python-ldap num2words xlwt
```

❖ Next Add the Following Lines in the Config Under the Debian Directory: 

```
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