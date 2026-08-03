# Linux Day 1 – Introduction & Basic Navigation

## What is Linux?

Linux is an operating system that manages computer hardware and software. It allows users to create, store, organize, and manage files and directories.

---

# Important Terms

### File

A file stores data such as text, images, videos, or programs.

### Directory (Folder)

A directory is a container used to organize files and other directories.

---

# Commands Learned

## 1. `pwd` (Print Working Directory)

### What is it?

Displays your current location in the Linux filesystem.

### Syntax

```bash
pwd
```

### Example Output

```text
/home/kali
```

---

## 2. `ls` (List)

### What is it?

Displays the files and directories in the current location.

### Syntax

```bash
ls
```

---

## 3. `ls -la`

### What is it?

Displays all files and directories, including hidden files, with detailed information.

### Syntax

```bash
ls -la
```

---

# Important Concepts

### Hidden Files

Files beginning with `.` are hidden.

Example:

```text
.bashrc
.profile
```

---

### First Character in `ls -la`

* `d` → Directory
* `-` → Regular file

Example:

```text
drwxr-xr-x  Documents
-rw-r--r--  notes.txt
```

---

# Key Points

* `pwd` tells you **where you are**.
* `ls` tells you **what is here**.
* `ls -la` provides detailed information.
* `.` at the beginning of a filename means it is hidden.

---

# Revision Questions

1. What does `pwd` display?
2. What is the difference between `ls` and `ls -la`?
3. What is a hidden file?
4. What does `d` indicate?
5. What does `-` indicate?

---

# One-Line Summary

**Use `pwd` to know your location, `ls` to see files and directories, and `ls -la` to view detailed information, including hidden files.**
# Linux Day 2 – Navigating and Managing Files

## Commands Learned

### 1. `cd` (Change Directory)

### What is it?

Changes your current working directory.

### Syntax

```bash
cd directory_name
```

### Example

```bash
cd Documents
```

---

### 2. `cp` (Copy)

### What is it?

Creates a copy of a file or directory while keeping the original unchanged.

### Syntax

```bash
cp source destination
```

### Example

```bash
cp notes.txt backup.txt
```

Result:

* `notes.txt` remains.
* `backup.txt` is created.

---

### 3. `mv` (Move / Rename)

### What is it?

* Moves a file or directory to another location.
* Renames a file or directory.

### Syntax

```bash
mv source destination
```

### Examples

Rename:

```bash
mv notes.txt report.txt
```

Move:

```bash
mv report.txt Documents/
```

---

# Important Concepts

## Difference Between `cp` and `mv`

| `cp`             | `mv`                         |
| ---------------- | ---------------------------- |
| Creates a copy   | Moves or renames             |
| Original remains | Original is moved or renamed |

---

## Linux Identifies Objects

Linux identifies objects by their actual type, not just by their filename.

Example:

```bash
mv report.txt report.pdf
```

This changes only the filename.

It does **not** create a real PDF document.

---

## Verify Your Work

After using `cp` or `mv`, verify the result:

```bash
ls
```

or

```bash
ls -la
```

---

# Key Points

* `cd` changes your location.
* `cp` creates a duplicate.
* `mv` moves or renames.
* Renaming does not change the file's contents or type.
* Always verify after running commands.

---

# Revision Questions

1. What does `cd` do?
2. What is the difference between `cp` and `mv`?
3. How does `mv` rename a file?
4. Does changing `.txt` to `.pdf` create a PDF?
5. Why should you verify your commands with `ls`?

---

# One-Line Summary

**Use `cd` to navigate, `cp` to copy, `mv` to move or rename, and remember that changing a filename never changes the actual file type.**
# Linux Day 3 – Creating Files and Directories

## Commands Learned

### 1. `mkdir` (Make Directory)

**What is it?**

* Creates a new directory (folder).

**Syntax:**

```bash
mkdir directory_name
```

**Example:**

```bash
mkdir Projects
```

---

### 2. `touch`

**What is it?**

* Creates a new empty file.
* If the file already exists, it updates the file's timestamp.

**Syntax:**

```bash
touch file_name
```

**Example:**

```bash
touch notes.txt
```

---

### 3. `file`

**What is it?**

* Identifies the actual type or state of a file.

**Syntax:**

```bash
file file_name
```

**Example:**

```bash
file notes.txt
```

Possible output:

```text
notes.txt: empty
```

---

# Important Concepts

### Directory vs File

* `mkdir` creates a **directory**.
* `touch` creates a **regular file**.

### Identifying Objects with `ls -la`

* `d` → Directory
* `-` → Regular file

Example:

```text
drwxr-xr-x  Projects
-rw-r--r--  notes.txt
```

---

### Filename vs File Content

Changing a filename **does not** change what the file actually is.

Example:

```bash
mv notes.txt report.pdf
```

This only changes the **name**. It does **not** create a real PDF document.

---

### Difference Between `file` and `cat`

| `file`                              | `cat`                                          |
| ----------------------------------- | ---------------------------------------------- |
| Identifies what kind of file it is. | Displays the contents of a file.               |
| Example output: `notes.txt: empty`  | Displays the text stored in the file (if any). |
| Does not print the file's contents. | Does not identify the file type.               |

---

# Commands Practiced

```bash
mkdir Bablu
cd Bablu
mkdir Kumar
touch my.txt
touch my2.txt
ls -la
file my.txt
```

---

# Key Points to Remember

* `mkdir` creates directories.
* `touch` creates empty files.
* `file` tells you the file's actual type or state.
* `touch` does not write data into a file.
* Renaming a file does not change its contents or type.
* Always verify your work using `ls -la` and `file`.

---

# Revision Questions

1. What is the purpose of the `mkdir` command?
2. What does the `touch` command do?
3. Why does `file my.txt` show `empty` after creating the file with `touch`?
4. What is the difference between `file` and `cat`?
5. Why doesn't `mv report.txt report.pdf` create a real PDF file?

---

# One-Line Summary

**`mkdir` creates directories, `touch` creates empty files, `file` identifies the real type or state of a file, and a filename alone never changes what a file actually is.**
