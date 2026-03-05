# Basic Linux Navigation Commands

Linux is primarily operated through the command line.

These commands help navigate and explore the filesystem.

---

## `pwd`

Print Working Directory.

Shows the current directory.

Example:

```
pwd
```

Output:

```
/home/akash
```

---

## `ls`

Lists files and directories.

Example:

```
ls
```

List with details:

```
ls -l
```

List hidden files:

```
ls -a
```

Useful flags:

- `-l` detailed view
- `-a` show hidden files
- `-h` human readable size

Example:

```
ls -lah
```

---

## `cd`

Change directory.

Example:

```
cd /home
```

Move into a user directory:

```
cd /home/akash
```

Go back one directory:

```
cd ..
```

Go to home directory:

```
cd ~
```

---

## `clear`

Clears the terminal screen.

```
clear
```

Shortcut:

```
Ctrl + L
```

---

## `history`

Shows previously executed commands.

```
history
```

Useful for recalling commands used earlier.

---

## `man`

Shows manual page for a command.

Example:

```
man ls
```

Provides documentation and usage instructions.

Exit manual using:

```
q
```
