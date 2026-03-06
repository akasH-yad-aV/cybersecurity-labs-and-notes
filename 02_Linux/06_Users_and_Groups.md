# Users and Groups in Linux

Linux is a multi-user operating system.  
Multiple users can access the system, and each user can have different permissions and access levels.

Users and groups help manage permissions and control access to files and system resources.

---

# User Accounts

Each user account has:

- Username
- User ID (UID)
- Group ID (GID)
- Home directory
- Default shell

User information is stored in:

```
/etc/passwd
```

Example entry:

```
akash:x:1001:1001:Akash:/home/akash:/bin/bash
```

Breakdown:

| Field | Description |
|------|-------------|
| akash | Username |
| x | Password placeholder |
| 1001 | User ID (UID) |
| 1001 | Group ID (GID) |
| Akash | User description |
| /home/akash | Home directory |
| /bin/bash | Default shell |

---

# Password Storage

Encrypted passwords are stored in:

```
/etc/shadow
```

This file is only accessible by the root user.

Example entry:

```
akash:$6$randomhash:19400:0:99999:7:::
```

---

# Creating Users

New users can be created using:

```bash
sudo useradd username
```

Example:

```bash
sudo useradd testuser
```

Create user with home directory:

```bash
sudo useradd -m testuser
```

---

# Setting Password

Set password for a user:

```bash
sudo passwd username
```

Example:

```bash
sudo passwd testuser
```

---

# Deleting Users

Remove a user account:

```bash
sudo userdel username
```

Remove user and home directory:

```bash
sudo userdel -r username
```

---

# Groups in Linux

Groups allow multiple users to share permissions.

Group information is stored in:

```
/etc/group
```

Example entry:

```
developers:x:1002:user1,user2
```

---

# Creating Groups

Create a group:

```bash
sudo groupadd developers
```

---

# Adding User to Group

Add a user to a group:

```bash
sudo usermod -aG groupname username
```

Example:

```bash
sudo usermod -aG developers akash
```

`-aG` means append user to the group without removing existing groups.

---

# Checking User Groups

View groups a user belongs to:

```bash
groups username
```

Example:

```bash
groups akash
```

---

# Current Logged-in User

Check current user:

```bash
whoami
```

Show logged-in users:

```bash
who
```

---

# Why Users and Groups Are Important

Users and groups help enforce security by controlling access to files and system resources.

Administrators use them to:

- Manage user access
- Assign permissions
- Restrict system operations
