---
title: conditional statements in zsh
tags: [zsh, conditionals, statements] 
id: 9izu
date: 2024-08-15
time: 21:50
---

# Conditional Statements In Zsh 

These notes are based on the book `Introduction to Shell Scripting Using Zsh`
located on my local machine at `~/Documents/books/zsh-shell-scripting.pdf`.

See Section 8: Conditional Statements for the book reference.

See "conditional expressions" section of `man zshmisc`.

Also see [Zsh Docs for conditional expressions](https://zsh.sourceforge.io/Doc/Release/Conditional-Expressions.html) to see all of the options
you can use inside of `if` statements. 

# Types of Statements

***If Statements*** are used when there is a need to check only conditions. If the 
condition found evaluates to `true`, then the statement inside the block will
be executed. 

***If-Else Statements*** are used when an `if` statement block is executed and
evaluates to `false`. 

***If-Elif-Else Statements*** are used when more than two conditions exist which 
cannot be solved only by using an `if-else` statement. Multiple `elif` statements
can be used inside of one `if-else` loop.

***Case Statements*** simplifies complex conditions with multiple different choices.
This statement is easier to maintain and more readable than nested `if` statements.
The `case` statement tests the input value until it finds the corresponding
pattern and executes the command linked to that input value. 

# Conditional Logic

[In this chapter](https://effective-shell.com/part-4-shell-scripting/mastering-conditional-logic), we introduce conditional logic and look at `if`,
`case`, and `select` statements. We will also look at how to chain commands 
together.

## The `if` Statement

We can use the `if` statement (expression) to perform operations in shell scripts
only when certain conditions are met. The `if` statement has the following
structure:

```
if <test-commands>
then 
    <conditional-command 1>
    <conditional-command 2>
    <conditional-command n>
fi
```

The `if` statement will run the test commands. If the result of the commands are
all `0` (exit code 0), then each conditional statement will be run. We close the
statement with the `fi` keyword.

Let's create an example that tries to create a folder using `mkdir`. The `mkdir`
command will return `0` if the folder is created successfully. 

```bash
#!/usr/bin/env zsh

if mkdir ~/backups
then
    echo "successfully created the 'backups' directory."
fi
```

*Results:* `mkdir: cannot create directory ‘/Users/jameshaston/backups’: File exists`

## The `test` Command

The `test` (evaluate expression) command is used to check whether a certain
condition is true or false. If the condition is `true`, then the command returns
`0` to indicate success. 

We could improve our earlier `if` statement by only creating the `backups/` dir
if it does not already exist using the `test` command:

```bash
#!/usr/bin/env zsh

if ! test -d ~/backups
then 
    echo "creating backups folder"
    mkdir ~/backups
fi
```

The `test` command evaluates an expression, in this case `-d ~/backups`. This expression uses
the `-d` operator to check if the provided path is a directory. We want to create the
directory only if it does not exist, so we use the not `!` operator to invert
the result of `test`. 

You can surround an expression with square brackets and the shell will evaluate
the expression with the `test` command. This can make your scripts more compact.

```bash
#!/usr/bin/env zsh

if ! [ -d ~/backups ]
then 
    echo "creating backups folder"
    mkdir ~/backups
fi
```

This square `[]` bracket syntax is common and is shorthand for the `test` command.
See `man test` for more information.

## Using Multiple Statements in a Single Line

You will often see `if` and `then` statements on the same line.

```bash
#!/usr/bin/env zsh

if ! [ -d ~/backups ]; then 
    echo "creating backups folder"
    mkdir ~/backups
fi
```

The shell assumes that each individual line is a statement. To use multiple
statements on a single line, use `;` as a command separator. 

## The `else` Statement

You can use the `else` statement to define a series of statements that should
be executed if the condition is *not* true. 

Here's how we can write a script that informs the user of whether they have
installed the `common` command or not:

```bash
#!/usr/bin/env zsh

if [ -e /usr/local/bin/common ] # -e : true if file exists
then 
    echo "the 'common' command is installed."
else 
    echo "the 'common' command is NOT installed."
fi
```

*Results:* `the 'common' command is NOT installed.`


## The `elif` Statement

The `elif` statement can be used to create additional checks and define statements
that should run if other conditions are true. Let's see an example by updating
our script to check whether the `common` command is executable, using the `-x`
operator. 

```bash
#!/usr/bin/env zsh

if [ -x /usr/local/bin/common ]; then
    echo "the 'common' command is executable."
elif [ -e /usr/local/bin/common ]; then
    echo "the 'common' command is installed but not executable."
else 
    echo "the 'common' command is not installed."
fi
```

*Results:* `the 'common' command is not installed.`

# Common Test Operators for Files

There are lots of operators for the `test` command to work with the filesystem.
See `man test` for all operators. Here are some useful operators:

- `-d` true if the file exists and is a folder.
- `-e` true if the file exists, regardless of file type. 
- `-f` true if the file exists and is a regular file. 
- `-L` true if the file exists and is a symbolic link. See [dotfiles](pdel%20dotfiles.md) re: symbolic links.
- `-r` true if the file exists and is human readable.
- `-s` true if the file exists and has size greater than 0.
- `-w` true if the file exists and is writable.
- `-x` true if the file exists and is executable; if dir then checks if it can be searched.
- `file1 -nt file2` true if file1 is newer than file2.
- `file1 -ot file2` true if file1 is older than file2.
- `file1 -ef file2` true if the files are the same file. 

# Combining Tests

Often you will want to check multiple conditions. You can use the `&&` and 
operator and the `||` or operator to check for multiple conditions.

```bash
#!/usr/bin/env zsh

if [[ $year -ge 1980 ]] && [[ $year -lt 1990 ]]; then
    echo "$year is in the 1980's"
else
    echo "$year is not in the 1980's"
fi
```

*Results:* ` is not in the 1980's`

# Case Statements (Bash Only)

Case statements are useful for simplifying complex `if` statements. A `case` 
statement is a bit like an `if` statement. Here is the structure:

```
case <expression> in
    pattern1)
        <pattern1 commands>
        ;;
    pattern2)
        <pattern2 commands>
        ;;
    *)
        <default commands>
        ;;
esac
```

Typically, you will provide the `case` statement a variable and use it to check
against a number of values. Here's an example checking to see whether the response
is 'yes' or 'no'.

> Do not run the following code in nvim! Run in the terminal. 

```bash
#!/usr/bin/env bash

read -p "Yes or no: " response
case "${response}" in 
    y | Y | yes | ok)
        echo "You have confirmed!"
        ;;
    n | N | no) 
        echo "You have denied!"
        ;;
    *)
        echo "'${response}' is not a valid response."
        ;;
esac
```

# Zk Reference Notes

- node: [termshell-node](z6c7-termshell-node.md)
- [zsh shell expansion](vnp1%20zsh-shell-expansion.md).
- [zsh basic input and output redirection](t67j%20zsh-basic-input-and-output-redirection.md).
- [loops in zsh](cegv%20loops-in-zsh.md).
- [conditional statements in zsh](9izu%20conditional-statements-in-zsh.md). 


