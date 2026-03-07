# Process Management in Linux

A process is an instance of a running program.

Linux allows users to monitor, control, and manage processes using various commands.

Each process in Linux is assigned a **Process ID (PID)** which uniquely identifies it.

---

# Viewing Running Processes

## ps

Displays information about active processes.

Example:

```bash
ps
```

Common usage:

```bash
ps aux
```

Explanation:

| Option | Meaning |
|------|------|
| a | Show processes of all users |
| u | Display detailed user information |
| x | Show processes without a terminal |

Example output:

```
USER   PID  %CPU %MEM COMMAND
akash  1250  0.0  0.1 bash
root    832  0.1  0.3 sshd
```

---

# top

Displays real-time information about system processes.

```bash
top
```

Shows:

- CPU usage
- Memory usage
- Running processes
- System load

Press `q` to exit.

---

# htop

Improved version of `top` with a more interactive interface.

```bash
htop
```

Note: It may need installation.

Example:

```bash
sudo apt install htop
```

---

# Process ID (PID)

Each running process has a unique **PID**.

Example:

```
PID 1250
```

The PID is used to manage or terminate processes.

---

# Killing Processes

## kill

Used to terminate a process using its PID.

Example:

```bash
kill 1250
```

---

## kill -9

Forcefully terminates a process.

```bash
kill -9 1250
```

Signal `9` sends a **SIGKILL**, which immediately stops the process.

---

# Background Processes

A process can run in the background.

Example:

```bash
firefox &
```

The `&` symbol runs the process in the background.

---

# Foreground and Background Jobs

View background jobs:

```bash
jobs
```

Bring job to foreground:

```bash
fg
```

Send process to background:

```bash
bg
```

---

# Finding Processes

## pgrep

Search for processes by name.

Example:

```bash
pgrep firefox
```

---

# Process Hierarchy

Linux processes follow a parent-child relationship.

The first process started by the kernel is:

```
init
```

or

```
systemd
```

This process manages other system services.

---

# Why Process Management Is Important

Process management helps administrators:

- Monitor system activity
- Identify resource-heavy programs
- Terminate malfunctioning processes
- Maintain system stability
