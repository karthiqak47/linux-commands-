
LINUX COMMANDS REFERENCE
=============================
1. INFORMATIONAL COMMANDS
-------------------------
pwd                 Print current working directory
whoami              Show current user
id                  Display user and group IDs
uname -a            Show system information
hostname            Display system hostname
date                Show current date and time
cal                 Display calendar
uptime              Show system uptime
history             Show command history

2. GETTING HELP
---------------
man <command>       Open manual page
<command> --help    Quick help for a command
info <command>      Detailed GNU documentation
whatis <command>    One-line command description
apropos <keyword>   Search commands by keyword

Examples:
man ls
ls --help
whatis grep
apropos file

3. FILE & DIRECTORY NAVIGATION
------------------------------
ls                  List files and directories
ls -l               Long listing format
ls -a               Show hidden files
ls -la              Long listing including hidden files
cd <dir>            Change directory
cd ..               Move to parent directory
cd ~                Go to home directory
pwd                 Show current path
tree                Display directory structure
find <path> -name <file>
                    Search for files

Examples:
cd Documents
cd ..
find . -name test.txt

4. FILE & DIRECTORY MANAGEMENT
------------------------------
mkdir <dir>         Create directory
mkdir -p a/b/c      Create nested directories
rmdir <dir>         Remove empty directory
rm <file>           Delete file
rm -r <dir>         Delete directory recursively
cp <src> <dest>     Copy file
cp -r <src> <dest>  Copy directory
mv <src> <dest>     Move/Rename file
touch <file>        Create empty file
cat <file>          Display file contents
less <file>         View file page-by-page
head <file>         Show first 10 lines
tail <file>         Show last 10 lines

Examples:
mkdir test
touch file.txt
cp file.txt backup.txt
mv file.txt newfile.txt
rm file.txt

5. PERMISSIONS & OWNERSHIP
--------------------------
ls -l               View permissions
chmod 755 file      Change permissions
chmod u+x file      Add execute permission
chmod 644 file      Read/write owner, read others
chown user file     Change owner
chgrp group file    Change group ownership
umask               View default permissions
sudo <command>      Run as administrator

Examples:
chmod 755 script.sh
chmod u+x script.sh
sudo chown karthik file.txt

Permission Values:
r = 4 (read)
w = 2 (write)
x = 1 (execute)

Examples:
777 = rwxrwxrwx
755 = rwxr-xr-x
644 = rw-r--r--

6. ACCESS CONTROL COMMANDS (ACL)
--------------------------------
getfacl <file>
    View ACL permissions

setfacl -m u:user:rwx <file>
    Add ACL permissions

setfacl -x u:user <file>
    Remove ACL entry

groups
    Show user groups

getent group
    Display system groups

Examples:
getfacl file.txt
setfacl -m u:john:rwx file.txt
setfacl -x u:john file.txt

7. USEFUL SHORTCUTS
-------------------
Ctrl + C      Stop running command
Ctrl + D      Logout / End input
Ctrl + L      Clear terminal screen
Tab           Auto-complete
Up Arrow      Previous command
Down Arrow    Next command
Ctrl + R      Search command history

8. COMMON LAB COMMANDS
----------------------
echo "Hello" > file.txt
    Write text to file

echo "More text" >> file.txt
    Append text

grep "word" file.txt
    Search text

wc -l file.txt
    Count lines

sort file.txt
    Sort contents

diff file1 file2
    Compare files

tar -cvf archive.tar dir/
    Create archive

tar -xvf archive.tar
    Extract archive

9. SYSTEM MONITORING
--------------------
ps
    Show running processes

ps aux
    Detailed process list

top
    Real-time process monitor

free -h
    Memory usage

df -h
    Disk usage

du -sh directory
    Directory size

kill PID
    Terminate process

