# Linux Filesystem Structure

Linux follows a hierarchical filesystem structure that starts from a single root directory `/`.

Unlike Windows, Linux does not use drive letters like C: or D:.  
Everything in the system exists under the root directory.

```
/
```

---

## Important Directories

### `/`
Root of the filesystem.  
All files and directories originate from this directory.

---

### `/bin`
Contains essential user command binaries.

Examples:
- ls
- cp
- mv
- cat
- mkdir

These commands are required for basic system operation.

---

### `/sbin`
Contains system administration binaries used for system management.

Examples:
- reboot
- shutdown
- fdisk
- mount

Typically used by root or system administrators.

---

### `/etc`
Contains system configuration files.

Examples:
- user configuration
- network configuration
- service configuration

Important files:
- `/etc/passwd`
- `/etc/shadow`
- `/etc/hosts`

---

### `/home`
Contains home directories for regular users.

Example:

```
/home/akash
```

User files, downloads, and personal configurations are stored here.

---

### `/root`
Home directory for the root user.

```
/root
```

Different from `/home`.

---

### `/var`
Contains variable data that changes frequently.

Examples:
- logs
- cache
- mail
- spool files

Important directory:

```
/var/log
```

Contains system log files.

---

### `/tmp`
Temporary files created by programs.

Files in this directory may be automatically deleted after reboot.

---

### `/usr`
Contains user utilities, applications, and libraries.

Examples:

```
/usr/bin
/usr/lib
/usr/share
```

Most installed programs exist here.

---

### `/proc`
Virtual filesystem that provides information about running processes and kernel.

Example:

```
/proc/cpuinfo
/proc/meminfo
```

These files are generated dynamically by the kernel.

---

### `/dev`
Contains device files representing hardware devices.

Examples:

```
/dev/sda
/dev/null
/dev/tty
```

Devices are treated as files in Linux.

---

### `/boot`
Contains files required to boot the operating system.

Includes:
- Linux kernel
- bootloader files
