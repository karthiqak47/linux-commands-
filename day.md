# Advanced Bash Scripting

## Introduction

In advanced Bash scripting, you can create more powerful and dynamic scripts by using:

- Conditional statements (`if`, `else`)
- Logical operators
- Arithmetic calculations
- Arrays
- Loops (`for`)

These features enable automation, decision-making, and repetitive task execution.

---

# Learning Objectives

After completing this reading, you will be able to:

- Use conditional statements to execute commands only when a condition is true
- Apply logical operators for true/false comparisons
- Perform arithmetic calculations in Bash
- Create and manipulate arrays
- Implement `for` loops for repetitive operations

---

# Conditional Statements

Conditional statements allow a script to make decisions.

## Basic Syntax

```bash
if [ condition ]
then
    statement_block_1
else
    statement_block_2
fi
```

### How It Works

- If the condition is **true**, commands inside the `then` block execute.
- If the condition is **false**, commands inside the `else` block execute.
- The `fi` keyword marks the end of the conditional block.

---

## Important Notes

✅ Always leave spaces inside brackets.

```bash
if [ $a == 1 ]
```

❌ Incorrect:

```bash
if [$a==1]
```

✅ Every `if` must end with `fi`.

✅ The `else` block is optional.

---

# Example: Check Number of Arguments

```bash
if [[ $# == 2 ]]
then
    echo "Number of arguments is equal to 2"
else
    echo "Number of arguments is not equal to 2"
fi
```

### Explanation

| Variable | Meaning |
|-----------|----------|
| `$#` | Number of command-line arguments |

---

# String Comparison

Suppose:

```bash
string_var="Yes"
```

You can compare strings using:

```bash
if [ "$string_var" == "Yes" ]
then
    echo "Condition is true"
fi
```

---

# Multiple Conditions

## AND Operator (`&&`)

Both conditions must be true.

```bash
if [ condition1 ] && [ condition2 ]
then
    echo "Both conditions are true"
else
    echo "One or both conditions are false"
fi
```

---

## OR Operator (`||`)

At least one condition must be true.

```bash
if [ condition1 ] || [ condition2 ]
then
    echo "At least one condition is true"
else
    echo "Both conditions are false"
fi
```

---

# Logical Operators

Logical operators compare values and return either true or false.

## Comparison Operators

| Operator | Meaning |
|-----------|----------|
| `==` | Equal to |
| `!=` | Not equal to |
| `<` | Less than |
| `>` | Greater than |
| `<=` or `-le` | Less than or equal to |
| `>=` or `-ge` | Greater than or equal to |

---

## Equality Example

```bash
a=2

if [ $a == 2 ]
then
    echo "a is equal to 2"
fi
```

---

## Not Equal Example

```bash
a=3

if [ $a != 2 ]
then
    echo "a is not equal to 2"
fi
```

---

## Less Than or Equal Example

```bash
a=1
b=2

if [ $a -le $b ]
then
    echo "a is less than or equal to b"
else
    echo "a is greater than b"
fi
```

Output:

```text
a is less than or equal to b
```

---

# Arithmetic Calculations

Bash supports integer arithmetic using:

```bash
$(( ))
```

---

## Simple Addition

```bash
echo $((3 + 2))
```

Output:

```text
5
```

---

## Using Variables

```bash
a=3
b=2

c=$(($a + $b))

echo $c
```

Output:

```text
5
```

---

# Arithmetic Operators

| Symbol | Operation |
|----------|------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |

---

## Example

```bash
echo $((10 - 3))
echo $((10 * 3))
echo $((10 / 2))
```

Output:

```text
7
30
5
```

---

# Integer Division

Bash only performs integer arithmetic.

Example:

```bash
echo $((3 / 2))
```

Output:

```text
1
```

The decimal portion (`0.5`) is discarded.

---

# Arrays

Arrays store multiple values in a single variable.

---

## Creating an Array

```bash
my_array=(1 2 "three" "four" 5)
```

Array contents:

```text
Index 0 → 1
Index 1 → 2
Index 2 → three
Index 3 → four
Index 4 → 5
```

---

## Empty Array

```bash
declare -a empty_array
```

---

## Appending Elements

```bash
my_array+=("six")
my_array+=(7)
```

Result:

```text
1 2 three four 5 six 7
```

---

# Accessing Array Elements

## First Element

```bash
echo ${my_array[0]}
```

Output:

```text
1
```

---

## Third Element

```bash
echo ${my_array[2]}
```

Output:

```text
three
```

---

## Print Entire Array

```bash
echo ${my_array[@]}
```

Output:

```text
1 2 three four 5 six 7
```

---

## Array Indexing

**Important:** Bash arrays start at index 0.

```text
First element  → index 0
Second element → index 1
Third element  → index 2
```

---

# For Loops

A `for` loop repeatedly executes commands.

---

## Loop Through Array Elements

```bash
for item in ${my_array[@]}
do
    echo $item
done
```

Output:

```text
1
2
three
four
5
```

---

## Loop Using Array Indices

```bash
for i in ${!my_array[@]}
do
    echo ${my_array[$i]}
done
```

This method gives access to array indices.

---

# Numeric For Loop

Useful when you know the number of iterations.

```bash
N=6

for (( i=0; i<=$N; i++ ))
do
    echo $i
done
```

Output:

```text
0
1
2
3
4
5
6
```

---

# Example: Count and Sum Array Elements

```bash
#!/usr/bin/env bash

my_array=(1 2 3)

count=0
sum=0

for i in ${!my_array[@]}
do
    echo ${my_array[$i]}

    count=$((count + 1))
    sum=$((sum + my_array[$i]))
done

echo "Count = $count"
echo "Sum = $sum"
```

Output:

```text
1
2
3
Count = 3
Sum = 6
```

---

# Real-World Example

Check if a user passed an argument:

```bash
#!/bin/bash

if [ $# -eq 0 ]
then
    echo "No arguments provided"
else
    echo "Arguments received"
fi
```

Run:

```bash
./script.sh hello
```

Output:

```text
Arguments received
```

---

# Quick Reference

## Conditional Statement

```bash
if [ condition ]
then
    commands
else
    commands
fi
```

---

## Arithmetic

```bash
$((a+b))
$((a-b))
$((a*b))
$((a/b))
```

---

## Arrays

```bash
arr=(1 2 3)

echo ${arr[0]}
echo ${arr[@]}
```

---

## For Loop

```bash
for item in ${arr[@]}
do
    echo $item
done
```

---

# Summary

## Conditionals

Used to execute commands only when a condition is true.

```bash
if [ condition ]
```

---

## Logical Operators

Compare values:

```bash
==
!=
-le
-ge
&&
||
```

---

## Arithmetic

Perform integer calculations:

```bash
$(( ))
```

---

## Arrays

Store multiple values:

```bash
arr=(1 2 3)
```

Access values:

```bash
${arr[0]}
${arr[@]}
```

---

## For Loops

Repeat commands:

```bash
for item in ${arr[@]}
do
    ...
done
```

Advanced Bash scripting combines these concepts to create powerful automation scripts capable of decision-making, data processing, and repetitive task execution.
