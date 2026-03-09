# System Services and Cron in Linux

Linux systems run many background programs called **services**.  
These services handle tasks such as networking, logging, and web servers.

Linux also allows users to schedule tasks automatically using **cron jobs**.

---

# System Services

A service is a program that runs in the background and performs system functions.

Examples of services:

- SSH server
- Web server (Apache, Nginx)
- Database server
- System logging service

Most modern Linux distributions manage services using **systemd**.

---

# systemctl

The `systemctl` command is used to manage system services.

Check service status:

```bash
systemctl status ssh
```

Start a service:

```bash
sudo systemctl start ssh
```

Stop a service:

```bash
sudo systemctl stop ssh
```

Restart a service:

```bash
sudo systemctl restart ssh
```

---

# Enable or Disable Services

Enable a service at system startup:

```bash
sudo systemctl enable ssh
```

Disable service from starting automatically:

```bash
sudo systemctl disable ssh
```

---

# Listing Services

List running services:

```bash
systemctl list-units --type=service
```

List all services:

```bash
systemctl list-unit-files --type=service
```

---

# Cron Jobs

Cron is a task scheduler used to run commands automatically at scheduled times.

Cron jobs are managed using `crontab`.

---

# Viewing Cron Jobs

View current user's cron jobs:

```bash
crontab -l
```

---

# Editing Cron Jobs

Edit cron jobs:

```bash
crontab -e
```

This opens the cron configuration file.

---

# Cron Syntax

Cron uses a time-based format:

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week
│ │ │ └──── Month
│ │ └────── Day of month
│ └──────── Hour
└────────── Minute
```

---

# Cron Examples

Run script every day at 2:00 AM:

```
0 2 * * * /home/user/backup.sh
```

Run command every 10 minutes:

```
*/10 * * * * command
```

Run task every Monday at 5 AM:

```
0 5 * * 1 command
```

---

# Cron Job Locations

System cron directories:

```
/etc/crontab
/etc/cron.d/
/etc/cron.daily/
/etc/cron.hourly/
```

These directories contain scheduled system tasks.

---

# Why Services and Cron Are Important

System services allow programs to run continuously in the background.

Cron jobs allow automation of tasks such as:

- system backups
- log rotation
- updates
- scheduled scripts
