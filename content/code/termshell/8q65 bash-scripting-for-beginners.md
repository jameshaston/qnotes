---
title: bash scripting for beginners
tags: [bash, shell, zsh, scripting] 
id: 8q65
date: 2024-07-31
time: 00:07
---

# Bash Scripting For Beginners 

These notes are based on this [YouTube tutorial](https://youtu.be/q4R57RkGueY?si=IejEhVLrr4kjhfYd). It's a beginners-friendly guide
for learning bash scripting. 

> Related Zk Note: [zsh shell resources](34nc%20zsh-shell-resources.md).

## What is Bash Scripting

- Bash: bourne again shell.
- Both a command-line interface and a scripting language. 
- Write commands in a file and run them as a program. 

```bash
#!/bin/bash
echo 'hi from bash!'
```

## Goals for This Tutorial

- Build a simple script step by step.
- Learn key concepts along the way.
- Gain a solid foundation in bash scripting.

## A Simple Bash Script

The first line of a shell script always starts with a shebang `!#/bin/bash`. This 
tells the operating system what shell to use and where its location is on the 
computer.

Bash enables a user to set available settings using the `set` keyword.

```bash
#!/usr/bin/env bash
#   env: env knows where the binary tools are located. Its safer than using
#        the direct location of bash `/bin/bash`

# Set strict mode. Use in every script.
set -euo pipefail
#   -e: exit immediately if a command exists with a non-zero status.
#   -u: treat unset variables as an error when substituting.
#   -o pipefail: the return value of a pipefail is the status of the last
#      command to exit with a non-zero status, or zero if no command
#      exited with a non-zero status.
```

Exit codes are important. An exit code of `0` means there are no issues.
A non-zero exit code signifies an error of some kind. 

> Check the last error code with `echo $?`.

## Function Definitions and Variables

Functions allow you to group commands and reuse code. You can pass command
line arguments to a function using `${value}`. 

```bash
# User defined function definition
print_header() {
    echo "=== $1 ==="
}
```

When the above function is executed, it will output the header and the
first argument passed to it. The first argument is passed to `$1`.

Assign command line arguments to variables in a shell script with the
syntax `var_name="${1:-}"`. We double-quote variables to prevent word splitting
and glob expansion.

> `${1:-}` is a bash operator that means use `$1` if set, otherwise use an empty string for the argument.

## Basic Error Handling

Error handling is useful for validating input passed by the user.

```bash
# basic error handling example
if [[ $# -eq 0 ]]; then
    echo "Error: Name is required."
    echo "Usage: $0 <name>"
    exit 1
fi
```

`$#` is a special variable that holds the number of arguments passed from the 
command line. `[[ ]]` is a bash keyword for conditional expressions, which
are more powerful than `[ ]` single brackets. The double-square expression
evaluates what is between the brackets and returns a boolean `true` or `false`.

`eq` stands for equal.

Therefore, the expression `[[ $# -eq 0 ]]` is doing the following:

1. Get the number of command line arguments passed to the function with `$#`.
2. Check if the number of arguments passed is equal to zero with `-eq 0`.
3. If true, echo the messages to the user and echo with exit code 1.
4. If false, do nothing.

Recall that exit code 0 means success and any other non-zero exit code indicates an error. 

### Calling the Function

From the command line, call the function using:

```bash
print_header "Greetings Baelien"

# the first argument passed is stored in `name`.
echo "hi ${name}! Welcome to our bash script."
```

## Loops and Iteration

Bash has c-style loops and syntax. Here is an example of an infinite loop using `while`.

```bash
# input with validation
while true; do
    read -p "how many files do you want to create? (0-5): " num_files
    if [[ "$num_files" =~ ^[0-5]$ ]]; then
        break
    else
        echo "Please enter a number between 0 and 5."
    fi
done
```

The `read` statement tells bash that it will accept input from the user and then
process the input. This information is stored in the `num_files` variable. 

To run the shell script, save it, and then make the script executable with `chmod`.
Then use `./{filename}` to run the script and execute the code inside. 

> Bash executes a script from top to bottom.

```sh
chmod +x while.sh
./while.sh
```

## Conditional Operators and Case Statement

One way to handle conditional statements in bash is the `if` and `fi` statements.
Another way is to use the `case` and `esac` statements. Case statements can be
helpful for branching logic and completing more complex tasks. 

```bash
# case statement
case $num_files in
0)
    echo "no files to be createed."
    ;;
[1-3])
    echo "creating new files."
    ;;
[4-5])
    echo "creating many files."
    ;;
esac
```

## Loop Over Arrays with `for`

An array in bash is designated by `()`. For example, we can create a files variable
that is of type array: `files=()`. The `files` variable is an empty array.

Bash arrays can store multiple values and use c-style syntax, which is common in
many shell scripting languages like `bash` and `zsh`.

Example: Using an array and `for` loop for file creation.

```bash
files=()
for ((i=1; i <= num_files; i++)); do
    filename="file_$i.txt"
#   echo here puts "created file number: {number}" inside the file
    echo "created file number: $i" >"$filename"
    files+=("$filename")
done
```

You can combine logic and functions, such as using the previously created
`print_header` function in combination with the file creation logic.

```bash
# string manipulation
print_header "Created Files"
for file in "${files[@]}"; do
    echo "${file##*/}" # remove path, show only filename
done
```

`${files[@]}` exapnds to all array elements. `${file##*/}` is called parameter
expansion and removes everything up to the last '/'.

## Displaying the Exit Code of the Last Command

You can display the exit code of the last executed command using `$?`.

```bash
# demonstrating exit code of last command
ls non_existent_file 2>/dev/null
if [[ $? -ne 0 ]]; then
    echo "The previous command failed."
    
fi
```

In the above code:

- `$?` holds the exit status of the last command.
- `2>/dev/null` redirects error output to /dev/null (discarding it).
- `-ne` means "not equal to".

Its good practice to exit with an exit code.

```bash
print_header "Script Completed"
exit 0
```

## Debugging Bash Scripts

There is no built-in debugging in bash. However, you can use the option `-x` to
provide verbose output about your script to the command line. The verbose
output will print every line of your script and can help you narrow down
any errors that you are receiving. 

```bash
bash -x file_name.sh 
# or 
bash -x file_name.sh <option>
```

# Zk Reference Notes

- node: [termshell-node](z6c7-termshell-node.md)
- [zsh shell resources](34nc%20zsh-shell-resources.md)


