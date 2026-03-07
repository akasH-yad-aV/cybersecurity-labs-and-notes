# Package Management in Linux

Package management is the process of installing, updating, removing, and managing software on a Linux system.

Linux distributions use package managers to handle software packages and their dependencies.

---

# Package Managers

Different Linux distributions use different package managers.

| Distribution | Package Manager |
|------|------|
| Debian / Ubuntu | apt |
| RedHat / CentOS | yum / dnf |
| Arch Linux | pacman |

In this file we focus mainly on **APT**, which is commonly used in Debian-based systems like Ubuntu and Kali Linux.

---

# Updating Package Lists

Before installing new software, update the package list.

```bash
sudo apt update
```

This command retrieves the latest list of available packages from repositories.

---

# Upgrading Installed Packages

Upgrade all installed packages:

```bash
sudo apt upgrade
```

This updates installed software to the latest available versions.

---

# Installing Packages

Install a new package:

```bash
sudo apt install package_name
```

Example:

```bash
sudo apt install nmap
```

This downloads and installs the package along with required dependencies.

---

# Removing Packages

Remove an installed package:

```bash
sudo apt remove package_name
```

Example:

```bash
sudo apt remove nmap
```

---

# Removing Packages with Configuration Files

Remove package and configuration files:

```bash
sudo apt purge package_name
```

Example:

```bash
sudo apt purge nmap
```

---

# Searching for Packages

Search for packages in repositories:

```bash
apt search package_name
```

Example:

```bash
apt search wireshark
```

---

# Viewing Package Information

Display detailed information about a package:

```bash
apt show package_name
```

Example:

```bash
apt show nmap
```

---

# Listing Installed Packages

List all installed packages:

```bash
dpkg -l
```

Search within installed packages:

```bash
dpkg -l | grep nmap
```

---

# Package Files

Downloaded packages are stored in:

```
/var/cache/apt/archives
```

Installed package information is stored in:

```
/var/lib/dpkg
```

---

# Why Package Management Is Important

Package managers simplify software management by:

- Handling dependencies
- Providing secure software repositories
- Automating updates
- Managing system software efficiently
