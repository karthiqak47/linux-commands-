# Linux Metacharacters, Quoting, Redirection, and Command Substitution

## Learning Objectives

After completing this reading, you will be able to:

- List examples of metacharacters
- Use quoting to specify literal or special character meanings
- Implement input and output redirection
- Apply command substitution
- Describe applications for command-line arguments

---

# Metacharacters

Metacharacters are special characters that the shell interprets as instructions rather than literal text.

## Common Metacharacters

| Metacharacter | Meaning |
|--------------|----------|
| `#` | Comment |
| `;` | Command separator |
| `*` | Wildcard matching any sequence of characters |
| `?` | Wildcard matching a single character |

---

# Pound Symbol (`#`)

The `#` symbol is used to write comments in shell scripts and configuration files.

Anything after `#` on a line is ignored by the shell.

### Example

```bash
#!/bin/bash

# This is a comment

echo "Hello, world!"  # This is another comment
```

### Why Use Comments?

- Explain code behavior
- Improve readability
- Document scripts for future maintenance

---

# Semicolon (`;`)

The semicolon allows multiple commands to be executed on a single line.

### Example

```bash
echo "Hello,"; echo "world!"
```

Output:

```text
Hello,
world!
```

### How It Works

Commands are executed sequentially from left to right.

---

# Asterisk (`*`)

The `*` wildcard matches any sequence of characters, including none.

### Example

```bash
ls *.txt
```

Matches:

```text
notes.txt
data.txt
report.txt
```

### Use Cases

- Selecting groups of files
- Bulk operations
- Pattern matching

---

# Question Mark (`?`)

The `?` wildcard matches exactly one character.

### Example

```bash
ls file?.txt
```

Matches:

```text
file1.txt
fileA.txt
filex.txt
```

Does **not** match:

```text
file12.txt
file.txt
```

---

# Quoting

Quoting controls how the shell interprets special characters.

## Quoting Symbols

| Symbol | Meaning |
|----------|----------|
| `\` | Escape a single character |
| `" "` | Allow variable expansion |
| `' '` | Treat everything literally |

---

# Backslash (`\`)

The backslash escapes special characters.

### Example

Create a file containing spaces:

```bash
touch file\ with\ spaces.txt
```

Without escaping:

```bash
touch file with spaces.txt
```

Linux interprets this as three separate filenames.

---

# Double Quotes (`" "`)

Inside double quotes:

- Most characters are treated literally
- Variables are expanded

### Example

```bash
echo "Hello $USER"
```

Output:

```text
Hello karthik
```

The shell replaces `$USER` with the current username.

---

# Single Quotes (`' '`)

Inside single quotes:

- Everything is treated literally
- Variables are NOT expanded

### Example

```bash
echo 'Hello $USER'
```

Output:

```text
Hello $USER
```

Notice the variable name is printed instead of its value.

---

# Input and Output Redirection

By default:

- Input comes from the keyboard (stdin)
- Output goes to the terminal (stdout)
- Errors go to the terminal (stderr)

Redirection changes this behavior.

---

## Redirection Operators

| Symbol | Meaning |
|----------|----------|
| `>` | Redirect output (overwrite) |
| `>>` | Redirect output (append) |
| `2>` | Redirect errors (overwrite) |
| `2>>` | Redirect errors (append) |
| `<` | Redirect input |

---

# Redirect Output (`>`)

Send command output to a file.

### Example

```bash
ls > files.txt
```

Output is stored in:

```text
files.txt
```

### Warning

If the file already exists:

```text
Contents are overwritten.
```

---

# Append Output (`>>`)

Append output to an existing file.

### Example

```bash
ls >> files.txt
```

Result:

```text
Existing contents remain.
New output is added at the end.
```

---

# Redirect Standard Error (`2>`)

Send error messages to a file.

### Example

```bash
ls non_existent_directory 2> error.txt
```

Terminal:

```text
(no error shown)
```

File:

```text
error.txt
```

contains the error message.

---

# Append Standard Error (`2>>`)

Append error messages instead of overwriting.

### Example

```bash
ls non_existent_directory 2>> error.txt
```

Useful for maintaining error logs.

---

# Redirect Input (`<`)

Use a file as input.

### Example

```bash
sort < data.txt
```

Instead of typing input manually, `sort` reads from `data.txt`.

---

# Command Substitution

Command substitution allows the output of one command to become part of another command.

## Syntax

### Modern Form

```bash
$(command)
```

### Legacy Form

```bash
`command`
```

The modern `$(...)` syntax is preferred.

---

# Example: Save Current Directory

Store the current directory path:

```bash
here=$(pwd)
```

Move elsewhere:

```bash
cd /tmp
```

Return to original location:

```bash
cd "$here"
```

### Explanation

1. `pwd` prints current directory
2. Output is stored in variable `here`
3. Variable can later be reused

---

# More Examples

## Display Current Date

```bash
echo "Today is $(date)"
```

Output:

```text
Today is Mon Aug 10 14:30:00 IST 2025
```

---

## Count Files

```bash
echo "Number of files: $(ls | wc -l)"
```

Output:

```text
Number of files: 25
```

---

# Command-Line Arguments

Command-line arguments are values passed to a program when it is executed.

## Example

```bash
./MyScript.sh arg1 arg2
```

Here:

- `arg1` is the first argument
- `arg2` is the second argument

---

# Accessing Arguments in Bash

| Variable | Meaning |
|-----------|----------|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |
| `$#` | Number of arguments |
| `$@` | All arguments |

---

## Example Script

```bash
#!/bin/bash

echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
```

Run:

```bash
./MyScript.sh Linux Bash
```

Output:

```text
Script Name: ./MyScript.sh
First Argument: Linux
Second Argument: Bash
```

---

# Quick Reference

## Metacharacters

```bash
# Comment
; Command separator
* Any number of characters
? One character
```

---

## Quoting

```bash
\      Escape character
"..."  Variables expanded
'...'  Everything literal
```

---

## Redirection

```bash
>     Output overwrite
>>    Output append
2>    Error overwrite
2>>   Error append
<     Input redirection
```

---

## Command Substitution

```bash
$(command)
```

Example:

```bash
echo $(date)
```

---

# Summary

### Metacharacters

Special symbols interpreted by the shell:

```bash
# ; * ?
```

### Quoting

Controls interpretation of special characters:

```bash
\
" "
' '
```

### Redirection

Redirect input, output, and errors:

```bash
> >> 2> 2>> <
```

### Command Substitution

Use command output inside another command:

```bash
$(command)
```

### Command-Line Arguments

Pass values to scripts:

```bash
./script.sh arg1 arg2
```

These concepts form the foundation of Linux shell scripting and command-line automation.
