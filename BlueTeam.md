# Linux Processes — Blue Team Notes

## 1. Process Basics

A **process** is a program that is currently running.

```text
Program  → instructions stored on disk
Process  → running instance of that program
```

Every running process has a **PID (Process ID)**.

* **PID** → identifies the process
* **PPID** → identifies the parent process that started it
* **USER** → user running/owning the process
* **CMD** → command/executable being run

---

## 2. Useful Commands

```bash
# Show processes from current terminal
ps

# Show detailed processes
ps aux

# Investigate a specific process
ps -p PID -o user,pid,ppid,stat,cmd

# Show process tree
pstree -p

# Show tree for a specific process
pstree -p PID

# Find highest CPU processes
ps aux --sort=-%cpu | head

# Find highest memory processes
ps aux --sort=-%mem | head
```

---

## 3. Important `ps aux` Fields

```text
USER  PID  %CPU  %MEM  VSZ  RSS  TTY  STAT  START  TIME  COMMAND
```

* **USER** → process owner
* **PID** → Process ID
* **%CPU** → CPU usage
* **%MEM** → memory usage
* **VSZ** → virtual memory size
* **RSS** → physical RAM currently used
* **STAT** → process state
* **COMMAND** → command/executable

> High CPU, high memory, or root ownership alone does **not** mean malware.

---

## 4. Process States

Common `STAT` states:

| State | Meaning               |
| ----- | --------------------- |
| `R`   | Running/runnable      |
| `S`   | Sleeping/waiting      |
| `D`   | Uninterruptible sleep |
| `T`   | Stopped               |
| `Z`   | Zombie                |

Common modifiers:

```text
s → session leader
l → multithreaded
N → lower scheduling priority (nice)
+ → foreground process group
```

Example:

```text
Ssl+
```

means:

```text
S → sleeping
s → session leader
l → multithreaded
+ → foreground process group
```

---

## 5. Parent → Child Processes

Processes form relationships.

Example:

```text
systemd/init (1)
    └── lightdm (949)
          └── Xorg (961)
```

If:

```text
PID 961
PPID 949
```

then **LightDM (949) is the parent of Xorg (961)**.

Use:

```bash
ps -p 961 -o user,pid,ppid,stat,cmd
```

and:

```bash
pstree -p
```

---

## 6. Threads

In `pstree`, entries inside `{}` are associated threads.

Example:

```text
vmtoolsd(559)
├── {vmtoolsd}(686)
├── {vmtoolsd}(689)
└── {vmtoolsd}(690)
```

`vmtoolsd(559)` is the main process; the `{vmtoolsd}` entries are its threads.

---

## 7. Investigating an Executable

Linux provides process information under:

```text
/proc/PID/
```

Find the executable:

```bash
sudo readlink -f /proc/559/exe
```

Example:

```text
/usr/bin/vmtoolsd
```

Find which Debian package owns it:

```bash
dpkg -S /usr/bin/vmtoolsd
```

Check package status/version:

```bash
dpkg -s open-vm-tools | grep -E '^(Package|Status|Version):'
```

---

## 8. Blue Team Process Investigation

When you find an interesting process, investigate it step-by-step:

```text
Process
   ↓
PID
   ↓
USER
   ↓
PPID
   ↓
Parent Process
   ↓
Process Tree
   ↓
Command / Path
   ↓
Executable
   ↓
Package
   ↓
Expected Behavior
```

### Example Investigation

```text
PID:       559
USER:      root
PPID:      1
EXE:       /usr/bin/vmtoolsd
PACKAGE:   open-vm-tools
STATUS:    install ok installed
```

Process relationship:

```text
systemd/init (1)
    └── vmtoolsd (559)
```

This gives evidence that the process has a legitimate explanation.

> **Blue Team rule: Don't judge a process from one attribute. Investigate its context.**

## Quick Commands

```bash
ps
ps aux
ps -p PID -o user,pid,ppid,stat,cmd
pstree -p
pstree -p PID
ps aux --sort=-%cpu | head
ps aux --sort=-%mem | head
sudo readlink -f /proc/PID/exe
dpkg -S /path/to/executable
dpkg -s package-name
```
# Linux Services & systemd — Quick Notes

## 1. systemd

`systemd` manages services and background processes on Linux.

Use `systemctl` to inspect and manage services.

## 2. Essential Commands

```bash
systemctl status <service>
```

Detailed current status: running, stopped, failed, PID, logs, etc.

```bash
systemctl is-active <service>
```

Checks whether the service is currently running.

```bash
systemctl is-enabled <service>
```

Checks whether the service is configured to start automatically at boot.

```bash
systemctl cat <service>
```

Shows the service's systemd configuration.

## 3. Important Status Values

| Value              | Meaning                              |
| ------------------ | ------------------------------------ |
| `active (running)` | Service is running now               |
| `inactive`         | Service is not running now           |
| `failed`           | Service encountered a failure        |
| `enabled`          | Configured to start automatically    |
| `disabled`         | Not configured for automatic startup |

> **Important:** `enabled` does not mean `running`.

## 4. systemd Service File

Example:

```ini
[Unit]
Description=Regular background program processing daemon
Documentation=man:cron(8)
After=remote-fs.target nss-user-lookup.target

[Service]
EnvironmentFile=-/etc/default/cron
ExecStart=/usr/sbin/cron -f $EXTRA_OPTS
Restart=on-failure
KillMode=process
SyslogFacility=cron

[Install]
WantedBy=multi-user.target
```

### `[Unit]`

Basic service information and startup relationships.

* `Description=` → human-readable purpose of the service.
* `Documentation=` → points to documentation.
* `After=` → controls startup order.

### `[Service]`

Defines how systemd runs and manages the service.

* `EnvironmentFile=` → loads environment settings.
* `ExecStart=` → command used to start the service.
* `Restart=on-failure` → restart if the service fails.
* `KillMode=` → controls how service processes are stopped.
* `SyslogFacility=` → categorizes service log messages.

### `[Install]`

Defines how the service is connected to startup when enabled.

* `WantedBy=` → specifies the systemd target associated with the service.

## 5. Blue Team Investigation

A useful investigation chain:

```text
Service
   ↓
Main PID
   ↓
User
   ↓
PPID / Parent
   ↓
Executable
   ↓
Configuration
   ↓
Boot Configuration
```

### Example: cron

```bash
systemctl status cron
```

```text
Main PID: 756 (cron)
```

Find the user, PID, parent and command:

```bash
ps -p 756 -o user,pid,ppid,cmd
```

Find the actual executable:

```bash
sudo readlink -f /proc/756/exe
```

Result:

```text
/usr/sbin/cron
```

Investigation:

```text
cron service
    ↓
PID 756
    ↓
root
    ↓
PPID 1 → systemd
    ↓
/usr/sbin/cron
    ↓
enabled at boot
```

## 6. Key Commands to Remember

```bash
systemctl status <service>
systemctl is-active <service>
systemctl is-enabled <service>
systemctl cat <service>

ps -p <PID> -o user,pid,ppid,cmd
sudo readlink -f /proc/<PID>/exe
```

### Key Distinction

```text
status      → What is happening now?
is-active   → Is it running now?
is-enabled  → Will it start automatically?
cat         → How is it configured?
```
