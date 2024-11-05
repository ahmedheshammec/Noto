first create a `.profile` file using the touch command

```sh
touch .profile
```

Basic command: 

```sh
echo "alias ll='ls -la'" >> .profile
echo "alias tk='python tiktok.py'" >> .profile
```

**Reload the** .profile to apply the alias immediately:

```sh
source .profile
```

you can confirm your aliases in the `.profile` file by using the `cat` command

```sh
cat .profile
```

to show the line number with the cat command use the `-n` flag

```sh
cat -n .profile
```

now what if we want to delete or edit the `.profile` file. for that we will use the `ed` command: 

```sh
ed .profile
```

let's say we want to remove the third line from the `.profile` file; type the following and hit enter:

```sh
3d
```

❖ you can delete multiple lines: 

```sh
3,4d
```

❖ you can also print all the lines inside the `ed` command: 

```sh
,p
```

❖ to save press `w` on empty line and then `q` to quit

❖ to append text use `a` on empty line then hit enter, to exit the append mode type the dot `.` once on an empty line and hit enter. 







