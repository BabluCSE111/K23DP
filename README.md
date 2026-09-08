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
# Linux Day 4 – Paths in Linux

## What is a Path?

A **path** is the address of a file or directory in the Linux filesystem.

---

## Why Do We Need Paths?

Different files can have the same name but be stored in different directories.

Example:

```text id="r4vrfx"
/home/kali/Documents/notes.txt

/home/kali/Downloads/notes.txt
```

The path tells Linux exactly which file or directory you mean.

---

# Types of Paths

1. Absolute Path
2. Relative Path

---

# 1. Absolute Path

## What is it?

An **absolute path** is the complete address of a file or directory.

It always starts from the root directory:

```text id="zq3mt7"
/
```

## Example

```text id="w7k1nn"
/home/kali/Bablu/my.txt
```

### Characteristics

* Starts with `/`
* Works from any location.
* Includes every directory until the final file or directory.

---

# 2. Relative Path

## What is it?

A **relative path** starts from your current working directory.

It does **not** start with `/`.

## Example

Current directory:

```text id="0jlvlz"
/home/kali/Bablu
```

Directory structure:

```text id="h0z6py"
Bablu
├── Kumar
│   └── report.txt
├── my.txt
└── my2.txt
```

Relative paths:

```text id="eyzjlwm"
my.txt
Kumar/report.txt
```

---

# Difference Between Absolute and Relative Paths

| Absolute Path           | Relative Path                      |
| ----------------------- | ---------------------------------- |
| Starts from `/` (root). | Starts from the current directory. |
| Complete address.       | Short address.                     |
| Works from anywhere.    | Depends on your current location.  |

---

# Relation with `pwd`

```bash id="y6z2ws"
pwd
```

Displays your current working directory.

Example:

```text id="yitjlwm"
/home/kali/Bablu
```

Relative paths are written based on this current location.

---

# Important Concepts

* Every file and directory has a unique address.
* An absolute path always begins with `/`.
* A relative path never begins with `/`.
* The last part of the path must be the object you want to reach.
* Linux is **case-sensitive**.

Example:

```text id="pfehf7"
Linux
```

and

```text id="swlhlk"
linux
```

are different names.

---

# Examples

Absolute Path:

```text id="f4u3hx"
/home/kali/Documents/Linux/commands.txt
```

Relative Path (Current Directory = `/home/kali/Documents`):

```text id="mpgfpv"
Linux/commands.txt
```

---

# Revision Questions

1. What is a path?
2. Why are paths required in Linux?
3. What is an absolute path?
4. What is a relative path?
5. What is the main difference between absolute and relative paths?
6. Why is `/home/kali/file.txt` an absolute path?
7. Is `Documents/report.txt` an absolute or relative path?
8. Why are `Linux` and `linux` considered different in Linux?

---

# One-Line Summary

**A path is the address of a file or directory. Absolute paths start from `/` (root), while relative paths start from your current working directory.**
# Linux Day 5 – Special Directory References

## What are Special Directory References?

Linux provides special symbols that represent commonly used directories.

These are:

* `.` (Current Directory)
* `..` (Parent Directory)
* `~` (Home Directory)

They are **not commands**. They are **directory references (paths)**.

---

# 1. `.` (Current Directory)

## What is it?

Represents the directory you are currently working in.

### Example

Current directory:

```text
/home/kali/AR
```

Command:

```bash
ls .
```

Meaning:

List the contents of the current directory.

---

# 2. `..` (Parent Directory)

## What is it?

Represents the parent (one level above) of the current directory.

### Example

Current directory:

```text
/ home/kali/AR
```

Parent directory:

```text
/home/kali
```

Command:

```bash
cd ..
```

Meaning:

Move one level up to the parent directory.

---

# 3. `~` (Home Directory)

## What is it?

Represents the current user's home directory.

For the `kali` user:

```text
~
=
/home/kali
```

### Example

```bash
cd ~
```

or simply

```bash
cd
```

Both take you to:

```text
/home/kali
```

---

# Important Concept

## Command + Target

Almost every Linux command follows this pattern:

```text
Command + Target
```

Examples:

```bash
ls .
```

List the current directory.

```bash
ls ..
```

List the parent directory.

```bash
cd ..
```

Move to the parent directory.

```bash
cd ~
```

Move to the home directory.

```bash
file my.txt
```

Identify the type of `my.txt`.

```bash
cat my.txt
```

Display the contents of `my.txt`.

---

# `cd` Using Different Paths

## Absolute Path

```bash
cd /home/kali/Documents/Linux
```

Starts from the root (`/`).

Works from anywhere.

---

## Relative Path

Current directory:

```text
/home/kali
```

Command:

```bash
cd Documents/Linux
```

Starts from the current working directory.

---

# Important Observation

`ls` lists only the contents of the directory you specify.

Example:

Directory structure:

```text
AS
├── AB.txt
├── Linux
│   └── AC.txt
└── Notes
```

Running:

```bash
ls
```

or

```bash
ls .
```

shows:

```text
AB.txt
Linux
Notes
```

It does **not** automatically list files inside `Linux`.

To list files inside `Linux`:

```bash
ls Linux
```

Output:

```text
AC.txt
```

---

# Empty Directory

If a directory exists but contains no files:

```bash
ls Notes
```

The command executes successfully but prints nothing.

There is **no error**.

"No such file or directory" appears only when the specified file or directory does not exist.

---

# Key Points

* `.` = Current directory.
* `..` = Parent directory.
* `~` = Home directory.
* These are directory references, not commands.
* Think of Linux commands as **Command + Target**.
* `ls` lists only the directory you specify.
* `cd` changes your current working directory.
* An empty directory produces no output with `ls`.
* Linux is case-sensitive.

---

# Revision Questions

1. What does `.` represent?
2. What does `..` represent?
3. What does `~` represent?
4. Why are `.`, `..`, and `~` called directory references instead of commands?
5. Explain the "Command + Target" concept with two examples.
6. What is the difference between `ls`, `ls .`, and `ls Linux`?
7. Why doesn't `ls` automatically display files inside subdirectories?
8. What happens when you run `ls` on an empty directory?

---

# One-Line Summary

**Linux commands usually follow the pattern "Command + Target". The symbols `.`, `..`, and `~` are special directory references that help you work with the current directory, parent directory, and home directory efficiently.**
# Linux Day 6 – Wildcards (`*` and `?`)

## What are Wildcards?

Wildcards are special characters used to match filenames or directory names based on a pattern.

Instead of typing every filename, you describe a pattern and let Linux find the matches.

---

# Why were Wildcards Created?

Suppose you have:

```
report1.txt
report2.txt
report3.txt
report_final.txt
```

Instead of typing every filename, you can use a wildcard pattern.

Example:

```bash
ls report*
```

Linux lists all names that start with `report`.

---

# Wildcard `*` (Asterisk)

## Meaning

`*` matches **zero or more characters**.

### Examples

Files:

```
my
my.txt
myfile
my_notes.pdf
```

Command:

```bash
ls my*
```

Output:

```
my
my.txt
myfile
my_notes.pdf
```

### Another Example

Files:

```
cat.txt
car.txt
camera.txt
dog.txt
```

Command:

```bash
ls ca*
```

Output:

```
camera.txt
car.txt
cat.txt
```

`dog.txt` does not match because its name does not start with `ca`.

---

# Wildcard `?`

## Meaning

`?` matches **exactly one character**.

### Example

Files:

```
log1.txt
log2.txt
log3.txt
log10.txt
login.txt
```

Command:

```bash
ls log?.txt
```

Output:

```
log1.txt
log2.txt
log3.txt
```

`log10.txt` and `login.txt` do not match because they have more than one character after `log`.

---

# Difference Between `*` and `?`

| Wildcard | Meaning                 |
| -------- | ----------------------- |
| `*`      | Zero or more characters |
| `?`      | Exactly one character   |

Examples:

```bash
file*
```

Matches:

```
file
file1
file12
file_backup
```

```bash
file?
```

Matches:

```
file1
fileA
```

Does not match:

```
file
file12
```

---

# Wildcards Work with Many Commands

Wildcards are not limited to `ls`.

Examples:

```bash
cp *.txt Backup/
```

Copies all `.txt` files.

```bash
mv report* Archive/
```

Moves all files whose names start with `report`.

```bash
rm file?.txt
```

Removes files with exactly one character after `file`.

---

# Important Concept

The **shell** expands the wildcard first.

Example:

```bash
cp *.txt Backup/
```

If the directory contains:

```
a.txt
b.txt
c.txt
```

The shell internally expands it to:

```bash
cp a.txt b.txt c.txt Backup/
```

Then `cp` performs the copy.

---

# Hidden Files and Wildcards

A filename beginning with `.` is a **hidden file**.

Examples:

```
.bashrc
.secret
.config
```

Command:

```bash
ls
```

Shows only normal files.

Command:

```bash
ls -a
```

Shows both normal and hidden files.

Command:

```bash
ls -la
```

Shows hidden files with detailed information.

---

# `*` and Hidden Files

Files:

```
report.txt
notes.txt
.secret
.config
photo.jpg
```

Command:

```bash
ls *
```

Output:

```
notes.txt
photo.jpg
report.txt
```

Hidden files are **not** matched by `*` by default.

---

# Key Points

* Wildcards match filename patterns.
* `*` = Zero or more characters.
* `?` = Exactly one character.
* Wildcards work with many commands (`ls`, `cp`, `mv`, `rm`, etc.).
* The shell expands wildcard patterns before running the command.
* Hidden files begin with `.`.
* `ls` does not show hidden files.
* `ls -a` and `ls -la` show hidden files.
* `*` does not match hidden files by default.

---

# Revision Questions

1. What is a wildcard?
2. Why were wildcards created?
3. What does `*` represent?
4. What does `?` represent?
5. Explain the difference between `*` and `?`.
6. What will `ls report*` match?
7. What will `ls log?.txt` match?
8. Do wildcards work only with `ls`? Explain.
9. What is a hidden file?
10. Why does `ls *` not display hidden files?
11. What is the difference between `ls`, `ls -a`, and `ls -la`?

---

# One-Line Summary

**Wildcards allow Linux to match filenames using patterns: `*` matches zero or more characters, `?` matches exactly one character, and hidden files (starting with `.`) are not matched by `*` by default.**
# Linux Day 7 — `find` Command

## 1. What is `find`?

`find` is used to **search for files and directories**.

### Why do we need it?

`ls` tells us what is available in a directory, but when we don't know where an item is, `find` can search through a directory and its subdirectories.

### Basic structure

```bash
find <starting-location> <condition>
```

Example:

```bash
find /home/kali/SR -name "my1.txt"
```

Meaning:

```text
find              → search
/home/kali/SR     → starting location
-name             → search based on name
"my1.txt"         → name/pattern to search for
```

---

# 2. `find` Searches Subdirectories

`find` searches the **starting directory and its subdirectories**.

Example structure:

```text
SR
├── my1.txt
├── my2.txt
├── SR1
│   └── my1.txt
└── SR2
    └── my2.txt
```

Command:

```bash
find /home/kali/SR -name "my1.txt"
```

Result:

```text
/home/kali/SR/my1.txt
/home/kali/SR/SR1/my1.txt
```

So `find` doesn't stop at `SR`; it continues into `SR1` and `SR2`.

---

# 3. Important: Starting Directory Is Also Checked

If we run:

```bash
find /home/kali/SR -type d
```

`find` also checks `/home/kali/SR` itself.

It does **not** mean "only search inside SR."

Think:

```text
Starting point
     ↓
Check it
     ↓
Enter it
     ↓
Check contents
     ↓
Enter subdirectories
     ↓
Continue
```

---

# 4. `-name`

`-name` tells `find`:

> **Search based on the name.**

Example:

```bash
find /home/kali/SR -name "my1.txt"
```

This searches for an item whose name is `my1.txt`.

Important:

`-name` can match **files or directories**.

It does not mean "search only files."

---

# 5. `find` + Wildcards

We can use the wildcards we learned on Day 6.

### `*`

```bash
find /home/kali/SR -name "my*.txt"
```

`*` means:

> **Zero or more characters**

Example matches:

```text
my.txt
my1.txt
my2.txt
my10.txt
my_notes.txt
```

---

### `?`

```bash
find /home/kali/SR -name "my?.txt"
```

`?` means:

> **Exactly one character**

Examples:

```text
my1.txt    → match
my2.txt    → match
my10.txt   → no match
```

---

# 6. `-type`

`-type` tells `find`:

> **What type of item should I search for?**

## `-type d`

```bash
-type d
```

Means:

> Search for directories.

Example:

```bash
find /home/kali/SR -type d
```

---

## `-type f`

```bash
-type f
```

Means:

> Search for regular files.

Example:

```bash
find /home/kali/SR -type f
```

---

# 7. Connection With `ls -l`

Earlier we learned:

```text
d  → directory
-  → regular file
```

`find` uses the same idea:

```text
-type d → directory
-type f → regular file
```

So:

```text
ls -l                  find

d  → directory         -type d → directory
-  → regular file      -type f → regular file
```

---

# 8. Combining Conditions

We can combine `-type` and `-name`.

Example:

```bash
find /home/kali/SR -type f -name "my*.txt"
```

Meaning:

> Search `/home/kali/SR` and its subdirectories for **regular files** whose names match `my*.txt`.

Another example:

```bash
find /home/kali/SR -type d -name "my*.txt"
```

Meaning:

> Search for **directories** whose names match `my*.txt`.

---

# 9. Mental Model of `find`

Think of `find` as applying filters:

```text
Starting location
       ↓
/home/kali/SR
       ↓
Search through it
       ↓
-type f
       ↓
Only regular files
       ↓
-name "my*.txt"
       ↓
Name must match pattern
       ↓
Results
```

Each condition makes the search more specific.

---

# 10. Important Examples

### Find a specific name

```bash
find /home/kali/SR -name "my1.txt"
```

### Find all `.txt` names beginning with `my`

```bash
find /home/kali/SR -name "my*.txt"
```

### Find only regular files

```bash
find /home/kali/SR -type f
```

### Find only directories

```bash
find /home/kali/SR -type d
```

### Find regular files matching a pattern

```bash
find /home/kali/SR -type f -name "my*.txt"
```

---

# Key Points to Remember

1. `find` → search.
2. The path after `find` is the **starting location**.
3. `find` searches the starting directory **and its subdirectories**.
4. The starting directory itself is also checked.
5. `-name` → search based on name.
6. `-type d` → directories.
7. `-type f` → regular files.
8. `*` → zero or more characters.
9. `?` → exactly one character.
10. `-type` and `-name` can be combined to make a more specific search.

---

## One-Line Summary

**`find` searches from a starting location through its subdirectories, and conditions such as `-name` and `-type` let us control exactly what we want to find.**
# 🐧 Linux Day 9 — Pipes, `wc`, and `tail`

## 1. Pipe `|`

### What is it?

`|` sends the **output of one command** to another command.

### Mental model

```text
Command 1
   ↓
 output
   ↓
   |
   ↓
Command 2
```

### Example

```bash
ls -la | grep "txt"
```

Meaning:

> `ls -la` produces output → `grep` receives that output → keeps lines containing `txt`.

### Important

The pipe passes **output/text**, not the actual files or directories.

---

## 2. Multiple Pipes

We can connect more than two commands:

```bash
ls -la | grep "txt" | grep "my"
```

Flow:

```text
ls -la
  ↓
grep "txt"
  ↓
grep "my"
```

Each command processes the output from the previous command.

### Example

```bash
ls -la | grep "txt" | grep "2"
```

If the output contains:

```text
my1.txt
my2.txt
my3.txt
```

the final result is:

```text
my2.txt
```

### Important misconception

```bash
grep "2"
```

does **not** mean "second line."

It means:

> Search for the text/character `2`.

---

# 3. `grep -i` with Pipes

```bash
ls -la | grep -i "sr"
```

`-i` makes the search **case-insensitive**.

It can match:

```text
sr
SR
Sr
sR
```

### Remember

```text
grep -i → ignore uppercase/lowercase differences
```

---

# 4. `wc`

`wc` can count information from files or command output.

Important options:

```text
-l → lines
-w → words
-c → bytes
```

---

## 5. `wc -l`

```bash
wc -l grep_lab.txt
```

→ counts the number of **lines** in the file.

### With a pipe:

```bash
ls -la | grep "txt" | wc -l
```

Flow:

```text
ls -la
   ↓
grep "txt"
   ↓
matching lines
   ↓
wc -l
   ↓
number of matching lines
```

If there are 3 `.txt` entries:

```text
3
```

---

# 6. `wc -w`

```bash
wc -w grep_lab.txt
```

→ counts the **words** in the file.

### Important distinction

```text
grep -w → match a whole word
wc -w   → count words
```

The meaning of an option depends on the command.

---

# 7. Combining `grep` + `wc`

```bash
grep "Linux" grep_lab.txt | wc -l
```

Meaning:

> Find lines containing `Linux` → count those matching lines.

If 3 lines contain `Linux`:

```text
3
```

---

# 8. `tail`

`tail` displays the **end of a file**.

```bash
tail grep_lab.txt
```

By default:

> `tail` displays the **last 10 lines**.

### Important

If the file has fewer than 10 lines:

```text
5 lines available
↓
tail asks for last 10
↓
only 5 exist
↓
all 5 are displayed
```

If the file has 100 lines:

```text
tail
↓
last 10 lines
```

---

# 9. Why `tail` is useful in SOC

Log files can contain thousands of lines.

Instead of reading the entire log:

```bash
cat auth.log
```

you can quickly inspect the newest entries:

```bash
tail auth.log
```

This is useful when investigating recent activity.

---

# 🧠 Main Mental Model

```text
ls
 ↓
produces output
 ↓
|
 ↓
grep
 ↓
filters output
 ↓
|
 ↓
wc
 ↓
counts the result
```

Example:

```bash
ls -la | grep "txt" | wc -l
```

means:

> List → filter for `txt` → count the matching lines.

---

# 📌 Commands Learned Today

```bash
ls -la | grep "txt"
```

```bash
ls -la | grep -i "sr"
```

```bash
ls -la | grep "txt" | grep "my"
```

```bash
ls -la | grep "txt" | wc -l
```

```bash
wc -l grep_lab.txt
```

```bash
wc -w grep_lab.txt
```

```bash
grep "Linux" grep_lab.txt | wc -l
```

```bash
tail grep_lab.txt
```

---

# ✅ Day 9 Revision Checklist

* [ ] Understand what `|` does
* [ ] Understand that the pipe passes command output
* [ ] Understand multiple pipes
* [ ] Know `grep -i`
* [ ] Know `wc -l`
* [ ] Know `wc -w`
* [ ] Understand `grep | wc -l`
* [ ] Know `tail`
* [ ] Remember `tail` shows the last 10 lines by default
* [ ] Understand why pipes are useful for log investigation

### Key takeaway

> **Pipes let us connect simple Linux commands together to filter, process, and count information.**
# 🐧 Linux Day 10 — `tail`, `head` & Log Analysis

## 1. `tail -n`

`tail` shows the **end of a file**.

```bash
tail file
```

→ last **10 lines** by default.

To choose the number of lines:

```bash
tail -n 5 file
```

→ last 5 lines.

Examples:

```bash
tail -n 3 auth.log
```

→ last 3 lines.

```bash
tail -n 20 auth.log
```

→ last 20 lines.

### Mental model

```text
tail → end
-n   → how many lines
```

---

# 2. `head`

`head` shows the **beginning of a file**.

```bash
head auth.log
```

→ first 10 lines by default.

To choose the number:

```bash
head -n 4 auth.log
```

→ first 4 lines.

### Mental model

```text
head → beginning
tail → end
```

---

# 3. Important: Order of Pipes

The order of commands changes the meaning.

### Example 1

```bash
tail -n 5 auth.log | grep "Failed"
```

Meaning:

> Take the last 5 lines → search for `Failed` among those 5.

### Example 2

```bash
grep "Failed" auth.log | tail -n 5
```

Meaning:

> Find all `Failed` lines → show the last 5 matching lines.

These are **not the same**.

---

# 4. `grep` + `head`

```bash
grep "Failed password" auth.log | head -n 4
```

Meaning:

> Find failed-password entries → show the **first 4 matching entries**.

Important:

```bash
head -n 4 auth.log
```

→ first 4 lines of the **file**

while:

```bash
grep "Failed password" auth.log | head -n 4
```

→ first 4 lines **matching the search**

---

# 5. `grep -n`

```bash
grep -n "Failed password" auth.log
```

`-n` displays the **line number** along with the matching line.

Example:

```text
2:Aug 11 10:03 Failed password for admin
4:Aug 11 10:07 Failed password for root
```

The number before `:` is the line number.

---

# 6. Practical SOC Investigation

We created:

```text
~/LG/auth.log
```

We investigated failed login attempts.

### Count failed logins

```bash
grep "Failed password" auth.log | wc -l
```

Result:

```text
5
```

→ **5 failed login attempts**

### Find failed entries

```bash
grep "Failed password" auth.log
```

We found:

```text
admin
root
admin
root
admin
```

Therefore:

```text
admin → 3 failures
root  → 2 failures
```

### Find line numbers

```bash
grep -n "Failed password" auth.log
```

Failed entries occurred on:

```text
2
4
6
9
11
```

---

# 7. `wc` Review

```bash
wc -l
```

→ count lines

```bash
wc -w
```

→ count words

Example:

```bash
grep "Failed password" auth.log | wc -l
```

→ count failed-login entries.

---

# 8. `grep -i` Review

```bash
grep -i "failed" auth.log
```

`-i` makes the search **case-insensitive**.

It can match:

```text
failed
Failed
FAILED
FaIlEd
```

---

# 9. Filename Mistake We Encountered

You accidentally created:

```text
auth.log~
```

instead of:

```text
auth.log
```

These are different filenames.

```text
auth.log
auth.log~
```

Linux treats them as separate files.

### Important reminder

Linux is:

> **case-sensitive and character-sensitive.**

---

# 🧠 Main Mental Model

For log analysis, think:

```text
grep
 ↓
FIND

|
 ↓
PASS OUTPUT

head / tail
 ↓
TAKE FIRST / LAST RESULTS

wc
 ↓
COUNT
```

Example:

```bash
grep "Failed password" auth.log | tail -n 5
```

means:

> Find failed-password entries → take the last 5 matching entries.

---

# 📌 Commands Learned Today

```bash
tail auth.log
```

```bash
tail -n 5 auth.log
```

```bash
head auth.log
```

```bash
head -n 4 auth.log
```

```bash
grep -n "Failed password" auth.log
```

```bash
grep "Failed password" auth.log | head -n 4
```

```bash
grep "Failed password" auth.log | tail -n 5
```

```bash
grep "Failed password" auth.log | wc -l
```

---

# ✅ Day 10 Revision Checklist

* [ ] Understand `tail`
* [ ] Understand `tail -n`
* [ ] Understand `head`
* [ ] Understand `head -n`
* [ ] Know the difference between `head`/`tail`
* [ ] Understand pipe order
* [ ] Understand `grep | head`
* [ ] Understand `grep | tail`
* [ ] Know `grep -n`
* [ ] Use `grep + wc` to count log entries
* [ ] Understand the SOC log-investigation workflow

### 🔥 Key takeaway

> **The order of commands in a pipeline matters. First decide what data you want, then decide how you want to filter, limit, or count it.**
