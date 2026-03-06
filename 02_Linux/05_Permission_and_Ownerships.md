# Permissions and Ownership in Linux

Linux uses a permission system to control who can read, write, or execute files and directories.

Each file and directory has an associated **owner**, **group**, and **permission set**.

Permissions help protect system files and prevent unauthorized access.

---

# Viewing Permissions

To view permissions, use:

```bash
ls -l
```

Example output:

```
-rw-r--r-- 1 akash akash 245 Jun 10 09:12 notes.txt
drwxr-xr-x 2 akash akash 4096 Jun 10 10:20 Documents
```

---

# Permission Structure

Example:

```
-rw-r--r--
```

Breakdown:

```
-  rw-  r--  r--
│   │    │    │
│   │    │    └── Others permissions
│   │    └────── Group permissions
│   └────────── Owner permissions
└────────────── File type
```

---

# File Types

First character indicates file type.

| Symbol | Type |
|------|------|
| - | Regular file |
| d | Directory |
| l | Symbolic link |
| c | Character device |
| b | Block device |

Example:

```
d rwx r-x r-x
```

This indicates a directory.

---

# Permission Types

Each permission has a specific meaning.

| Permission | Symbol | Meaning |
|------|------|------|
| Read | r | View file contents |
| Write | w | Modify file |
| Execute | x | Run file as program |

---

# Permission Groups

Linux divides permissions into three groups:

### Owner (User)

The user who created the file.

### Group

Users that belong to the file's group.

### Others

All other users on the system.

---

# Changing Permissions

Permissions can be modified using `chmod`.

Example:

```bash
chmod u+x script.sh
```

Adds execute permission for the owner.

Example removing permission:

```bash
chmod g-w file.txt
```

Removes write permission from group.

---

# Numeric Permission Mode

Permissions can also be represented numerically.

| Permission | Value |
|------|------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Example:

```
rwx = 7
rw- = 6
r-- = 4
```

Example command:

```bash
chmod 755 script.sh
```

Meaning:

```
Owner: rwx
Group: r-x
Others: r-x
```

---

# Changing Ownership

Ownership can be changed using `chown`.

Example:

```bash
sudo chown user file.txt
```

Change both owner and group:

```bash
sudo chown user:group file.txt
```

---

# Changing Group

Group ownership can be modified using `chgrp`.

Example:

```bash
chgrp developers file.txt
```

---

# Why Permissions Are Important

Permissions protect system files and sensitive data.

For example:

- Prevent unauthorized file modification
- Restrict execution of malicious scripts
- Control access to critical system directories

Improper permissions can lead to security vulnerabilities.
