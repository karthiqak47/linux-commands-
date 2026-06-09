# 🐧 Linux Commands Reference Guide

A quick reference guide for commonly used Linux commands.

---

# 1. Information Commands

Commands used to obtain system and user information.

| Command | Description |
|----------|-------------|
| `pwd` | Print current working directory |
| `whoami` | Show current user |
| `id` | Display user and group IDs |
| `uname -a` | Show system information |
| `hostname` | Display system hostname |
| `date` | Show current date and time |
| `cal` | Display calendar |
| `uptime` | Show system uptime |
| `history` | Show command history |

### Examples

```bash
pwd
whoami
uname -a
date
history
```

---

# 2. Getting Help

Linux provides several built-in documentation tools.

| Command | Description |
|----------|-------------|
| `man <command>` | Open manual page |
| `<command> --help` | Quick help |
| `info <command>` | Detailed GNU documentation |
| `whatis <command>` | One-line description |
| `apropos <keyword>` | Search commands by keyword |

### Examples

```bash
man ls
ls --help
whatis grep
apropos file
```

---

# 3. File & Directory Navigation

Commands for moving around the filesystem.

| Command | Description |
|----------|-------------|
| `ls` | List files and directories |
| `ls -l` | Long listing format |
| `ls -a` | Show hidden files |
| `ls -la` | Long listing including hidden files |
| `cd <dir>` | Change directory |
| `cd ..` | Move to parent directory |
| `cd ~` | Go to home directory |
| `pwd` | Print current directory |
| `tree` | Show directory structure |
| `find <path> -name <file>` | Search for files |

### Examples

```bash
cd Documents
cd ..
cd ~

find . -name test.txt
tree
```

---

# 4. File & Directory Management

Commands for creating, deleting, copying, and moving files.

| Command | Description |
|----------|-------------|
| `mkdir <dir>` | Create directory |
| `mkdir -p a/b/c` | Create nested directories |
| `rmdir <dir>` | Remove empty directory |
| `rm <file>` | Delete file |
| `rm -r <dir>` | Delete directory recursively |
| `cp <src> <dest>` | Copy file |
| `cp -r <src> <dest>` | Copy directory |
| `mv <src> <dest>` | Move/Rename file |
| `touch <file>` | Create empty file |
| `cat <file>` | Display file contents |
| `less <file>` | View file page-by-page |
| `head <file>` | First 10 lines |
| `tail <file>` | Last 10 lines |

### Examples

```bash
mkdir test
touch file.txt

cp file.txt backup.txt
mv file.txt newfile.txt

rm file.txt
rm -r test
```

---

# 5. Permissions & Ownership

Linux controls file access through permissions.

## Viewing Permissions

```bash
ls -l
```

### Permission Commands

| Command | Description |
|----------|-------------|
| `chmod 755 file` | Set permissions |
| `chmod u+x file` | Add execute permission |
| `chmod 644 file` | Read/write owner, read others |
| `chown user file` | Change owner |
| `chgrp group file` | Change group |
| `umask` | View default permissions |
| `sudo command` | Run as administrator |

### Examples

```bash
chmod 755 script.sh
chmod u+x script.sh

sudo chown karthik file.txt
```

---

## Permission Values

| Permission | Value |
|------------|--------|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

### Common Permission Sets

| Numeric | Symbolic |
|----------|----------|
| `777` | `rwxrwxrwx` |
| `755` | `rwxr-xr-x` |
| `644` | `rw-r--r--` |

---

# 6. Access Control Lists (ACL)

ACLs provide more granular permissions than standard Linux permissions.

## View ACLs

```bash
getfacl file.txt
```

## Add ACL Entry

```bash
setfacl -m u:john:rwx file.txt
```

## Remove ACL Entry

```bash
setfacl -x u:john file.txt
```

### Useful Commands

| Command | Description |
|----------|-------------|
| `getfacl <file>` | View ACL permissions |
| `setfacl -m u:user:rwx <file>` | Add ACL entry |
| `setfacl -x u:user <file>` | Remove ACL entry |
| `groups` | Show user groups |
| `getent group` | List system groups |

### Examples

```bash
getfacl file.txt

setfacl -m u:john:rwx file.txt

setfacl -x u:john file.txt
```

---

# 7. Useful Keyboard Shortcuts

| Shortcut | Action |
|-----------|---------|
| `Ctrl + C` | Stop running command |
| `Ctrl + D` | Logout / End input |
| `Ctrl + L` | Clear terminal |
| `Tab` | Auto-complete |
| `↑` | Previous command |
| `↓` | Next command |
| `Ctrl + R` | Search command history |

---

# 8. Common Lab Commands

Frequently used commands in Linux labs and scripting exercises.

## Writing to Files

Overwrite file:

```bash
echo "Hello" > file.txt
```

Append to file:

```bash
echo "More text" >> file.txt
```

---

## Text Searching

```bash
grep "word" file.txt
```

Searches for lines containing `"word"`.

---

## Count Lines

```bash
wc -l file.txt
```

Example Output:

```text
25 file.txt
```

---

## Sort File Contents

```bash
sort file.txt
```

---

## Compare Files

```bash
diff file1 file2
```

---

## Archive Files

Create archive:

```bash
tar -cvf archive.tar dir/
```

Extract archive:

```bash
tar -xvf archive.tar
```

---

# 9. System Monitoring

Commands for monitoring system resources and processes.

| Command | Description |
|----------|-------------|
| `ps` | Show running processes |
| `ps aux` | Detailed process list |
| `top` | Real-time process monitor |
| `free -h` | Memory usage |
| `df -h` | Disk usage |
| `du -sh directory` | Directory size |
| `kill PID` | Terminate process |

---

## Process Monitoring

```bash
ps
ps aux
top
```

---

## Memory Usage

```bash
free -h
```

Example Output:

```text
Total   Used   Free
16G      8G     7G
```

---

## Disk Usage

Filesystem usage:

```bash
df -h
```

Directory size:

```bash
du -sh Downloads
```

---

## Kill a Process

```bash
kill 1234
```

Where `1234` is the Process ID (PID).

---

# Quick Cheat Sheet

## Navigation

```bash
pwd
ls
ls -la
cd ..
cd ~
```

## File Operations

```bash
touch file.txt
cp file1 file2
mv old new
rm file.txt
mkdir test
```

## Permissions

```bash
chmod 755 script.sh
chmod u+x script.sh
chown user file
```

## Search

```bash
find . -name file.txt
grep "word" file.txt
```

## System Info

```bash
uname -a
hostname
date
uptime
```

## Monitoring

```bash
ps aux
top
free -h
df -h
```

---

# Summary

This guide covers:

✅ System Information Commands  
✅ Help & Documentation Commands  
✅ Navigation Commands  
✅ File Management Commands  
✅ Permissions & Ownership  
✅ ACL Management  
✅ Terminal Shortcuts  
✅ Common Lab Commands  
✅ System Monitoring Tools

These commands form the foundation of everyday Linux administration, shell scripting, and development workflows.
