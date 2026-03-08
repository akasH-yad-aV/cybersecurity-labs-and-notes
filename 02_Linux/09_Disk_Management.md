# Disk Management in Linux

Disk management involves monitoring, partitioning, mounting, and analyzing storage devices.

Linux treats storage devices as files located in the `/dev` directory.

Example disk devices:

```
/dev/sda
/dev/sdb
/dev/nvme0n1
```

---

# Viewing Disk Usage

## df

Shows disk space usage of mounted filesystems.

Example:

```bash
df
```

Human-readable format:

```bash
df -h
```

Example output:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  42% /
```

Explanation:

| Column | Meaning |
|------|------|
| Filesystem | Storage device |
| Size | Total disk size |
| Used | Used space |
| Avail | Available space |
| Use% | Percentage used |
| Mounted on | Mount point |

---

# Checking Directory Size

## du

Displays disk usage of files and directories.

Example:

```bash
du
```

Human-readable format:

```bash
du -h
```

Check size of a directory:

```bash
du -sh /home
```

Explanation:

- `-s` summary
- `-h` human readable

---

# Listing Storage Devices

## lsblk

Shows block devices such as disks and partitions.

Example:

```bash
lsblk
```

Example output:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   50G  0 disk
├─sda1   8:1    0   49G  0 part /
└─sda2   8:2    0    1G  0 part [SWAP]
```

Explanation:

- `disk` → physical device
- `part` → partition

---

# Partition Information

## fdisk

Used to view or manage disk partitions.

View disk partitions:

```bash
sudo fdisk -l
```

Shows:

- disks
- partition layout
- partition sizes

---

# Mounting Filesystems

Mounting attaches a filesystem to the Linux directory structure.

Example:

```bash
sudo mount /dev/sdb1 /mnt
```

This makes the device accessible under `/mnt`.

---

# Unmounting Filesystems

Before removing a disk or USB device it must be unmounted.

Example:

```bash
sudo umount /mnt
```

---

# Mount Points

A mount point is a directory where a storage device is attached.

Examples:

```
/
 /home
 /mnt
 /media
```

---

# Automatically Mounting Disks

Linux stores mount configuration in:

```
/etc/fstab
```

This file defines which filesystems are mounted automatically during system boot.

---

# Why Disk Management Is Important

Disk management helps administrators:

- monitor storage usage
- manage disk partitions
- mount storage devices
- prevent disk space issues
