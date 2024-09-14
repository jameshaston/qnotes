---
id: vnp1
title: zsh shell expansion
date: 2024-08-15
time: 18:38
keywords: [shell:expansion, zsh, variable, brace, command:substitution] 
---

# Zsh Shell Expansion 

These notes are based on the book `Introduction to Shell Scripting Using Zsh`
located on my local machine at `~/Documents/books/zsh-shell-scripting.pdf`.

# Types of Shell Expansion

There are 8 expansion in total:

1. Brace.
2. Tilde.
3. Shell parameter and variable.
4. Command substitution.
5. Arithmetic.
6. Process substitution.
7. Word splitting.
8. File name.

This lesson will cover brace expansion, shell parameter and variable expansion,
and command substitution.

# Brace Expansion

Brace expansion is a mechanism by which arbitrary `strings` may be generated. 
Patterns to be brace-expanded take the form of an optional `preamble`, followed
by a series of comma-separated strings between a pair of braces, followed
by an optional `postscript`. 

The `preamble` is prefixed to each string contained within the braces, and the
`postscript` is then appended to each resulting string, expanding *left to right*.

Brace expansions may be nested. The results of each expanded string are not 
sorted; left to right order is preserved. 

```zsh
# example of brace expansion
mkdir -p ~/programming/{rust,python,c} #note the lack of spaces in the braces
```

# Shell Parameter and Variable Expansion

The `$` character is used for parameter expansion, command substitution, and
arithmetic expansion. The parameter name or symbol to be expanded may be 
enclosed in `{}`, which are optional but serve to protect the variable to be 
expanded from characters immediately following it which could be interpreted
as part of the name. 

The basic form of parameter expansion is `${parameter}`. 

> `{}` are required when `parameter` is a positional parameter.

If the first character of `parameter` is an exclamation point `!`, zsh uses the
value of the variable formed from the rest of `parameter` as the name of the
variable; this variable is then expanded and that value is used in the rest
of the substitution, rather than the value of `parameter` itself. This is 
known as indirect expansion. 

```zsh
# example of shell expansion
echo $SHELL

# output: /bin/zsh 
```

# Command Substitution

Command substitution allows the output of a command to replace the command
itself. This occurs when a command is enclosed in `()` or back ticks. Zsh 
performs the expansion by executing `command` and replacing the command substitution
with the standard output of the command, deleting trailing newlines. 

When using the `$(command)` form, all characters between the parentheses make up
the command and none are treated specially. 

```zsh
# an example of command substitution
echo $(date)

# output: /bin/zsh 
```

# Related `zk` Notes

- [zsh shell resources](34nc%20zsh-shell-resources.md).
- [zsh line editor](vyu9%20zsh-line-editor.md).

































