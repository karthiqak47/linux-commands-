# Linux Pipes (`|`)

## Learning Objectives

After completing this reading, you will be able to:

- Describe pipes
- Use pipes to combine commands when working with strings and text file contents
- Use pipes to extract information from URLs and JSON data

---

# What Are Pipes?

A **pipe (`|`)** in Linux allows you to use the output of one command as the input of another command.

### Syntax

```bash
command1 | command2 | command3 | ... | commandN
```

There is no limit to the number of commands you can chain together.

---

# Why Use Pipes?

Instead of storing intermediate results in files, pipes allow commands to work together directly.

Example:

```bash
cat file.txt | sort | uniq
```

This:

1. Reads the file
2. Sorts the contents
3. Removes duplicates

---

# Example 1: Combining Commands

## The `sort` Command

Sorts lines alphabetically.

```bash
sort filename
```

## The `uniq` Command

Removes **consecutive duplicate lines**.

```bash
uniq filename
```

---

## Sample File: `pets.txt`

```text
goldfish
dog
cat
parrot
dog
goldfish
goldfish
```

---

## Using `sort`

```bash
sort pets.txt
```

Output:

```text
cat
dog
dog
goldfish
goldfish
goldfish
parrot
```

Notice duplicates still exist.

---

## Using `uniq`

```bash
uniq pets.txt
```

Output:

```text
goldfish
dog
cat
parrot
dog
goldfish
```

Only consecutive duplicates are removed.

---

## Combining `sort` and `uniq`

```bash
sort pets.txt | uniq
```

Output:

```text
cat
dog
goldfish
parrot
```

### Why It Works

1. `sort` places identical lines together.
2. `uniq` removes consecutive duplicates.

---

# Example 2: Using `tr` with Pipes

## The `tr` Command

`tr` (translate) replaces characters in text.

### Syntax

```bash
tr [OPTIONS] [target] [replacement]
```

Since `tr` reads from standard input, it is commonly used with pipes.

---

## Replace Vowels with `_`

```bash
echo "Linux and shell scripting are awesome!" | tr "aeiou" "_"
```

Output:

```text
L_n_x _nd sh_ll scr_pt_ng _r_ _w_s_m_!
```

---

## Replace Everything Except Vowels

Use the `-c` option:

```bash
echo "Linux and shell scripting are awesome!" | tr -c "aeiou" "_"
```

Output:

```text
_i_u__a_____e______i__i___a_e_a_e_o_e_
```

### Explanation

- `-c` means **complement**
- Match all characters **except** the specified ones

---

# Processing File Contents with `tr`

Convert all text to uppercase:

```bash
cat pets.txt | tr "[a-z]" "[A-Z]"
```

Output:

```text
GOLDFISH
DOG
CAT
PARROT
DOG
GOLDFISH
GOLDFISH
```

---

## Combining Multiple Commands

```bash
sort pets.txt | uniq | tr "[a-z]" "[A-Z]"
```

Output:

```text
CAT
DOG
GOLDFISH
PARROT
```

This pipeline:

1. Sorts the file
2. Removes duplicates
3. Converts text to uppercase

---

# Extracting Information from JSON Files

Suppose you have the following JSON data saved in a file named `Bitcoinprice.txt`:

```json
{
  "coin": {
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "rank": 1,
    "price": 57907.78008618953,
    "priceBtc": 1,
    "volume": 48430621052.9856
  }
}
```

---

## Goal

Extract the value of the `"price"` field.

Example desired output:

```text
"price": 57907.78008618953
```

---

## Using `grep`

```bash
grep -oE "\"price\"\s*:\s*[0-9]*\.?[0-9]*"
```

### Explanation

| Option | Meaning |
|----------|----------|
| `-o` | Print only the matching text |
| `-E` | Enable extended regular expressions |

### Regex Breakdown

```regex
\"price\"\s*:\s*[0-9]*\.?[0-9]*
```

| Pattern | Meaning |
|-----------|-----------|
| `\"price\"` | Match `"price"` |
| `\s*` | Match zero or more spaces |
| `:` | Match colon |
| `[0-9]*` | Match digits |
| `\.?` | Optional decimal point |
| `[0-9]*` | More digits |

---

## Extract Price from JSON File

```bash
cat Bitcoinprice.txt | grep -oE "\"price\"\s*:\s*[0-9]*\.?[0-9]*"
```

Output:

```text
"price": 57907.78008618953
```

---

# Common Pipe Examples

## Count Number of Files

```bash
ls | wc -l
```

---

## Search for a Word

```bash
cat file.txt | grep "error"
```

---

## Count Matching Lines

```bash
cat file.txt | grep "error" | wc -l
```

---

## Display First 10 Results

```bash
ls -l | head
```

---

## Display Last 10 Results

```bash
ls -l | tail
```

---

# Summary

## Pipes

A pipe (`|`) passes the output of one command as the input of another.

```bash
command1 | command2
```

---

## Useful Combinations

### Remove Duplicates

```bash
sort file.txt | uniq
```

### Convert to Uppercase

```bash
cat file.txt | tr "[a-z]" "[A-Z]"
```

### Extract Data Using Regex

```bash
cat data.json | grep -oE "pattern"
```

### Count Results

```bash
grep "text" file.txt | wc -l
```

---

## Key Takeaways

- Pipes connect commands together.
- They eliminate the need for temporary files.
- Commands like `sort`, `uniq`, `grep`, `tr`, `head`, `tail`, and `wc` become much more powerful when combined.
- Linux pipelines are one of the most important tools for text processing and automation.
