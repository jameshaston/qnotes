---
id: t67j
title: zsh basic input and output redirection
date: 2024-08-15
time: 19:39
keywords: [zsh, redirection, stdin, stdout, stderr, heredoc] 
---

# Basic Input And Output Redirection Zsh

These notes are based on the book `Introduction to Shell Scripting Using Zsh`
located on my local machine at `~/Documents/books/zsh-shell-scripting.pdf`. See
Section 4: Input/Output Redirection. 

## What is Redirection

Redirection means capturing output from a file, command, program, script, or
even code block within a script and sending it as input to another file, command,
program, or script. 

There are always three default files that are open:

1. stdin (keyboard).
2. stdout (the screen). 
3. stderr (error messages output to the screen). 

## File Descriptors

The default files contain numbers known as file descriptors. You can call them by
their file descriptor numbers when redirecting them. For example, `2>&1` can be
used in a script to redirect stderr and stdout to a log file or any other file. 

1. stdin (keyboard) - file descriptor `0`.
2. stdout (the screen) file descriptor `1`. 
3. stderr (error messages output to the screen) file descriptor `2`. 

# Redirecting Output

The default files and any other open file can be redirected using `>`. 

```sh
# example of redirecting output to a new file
ls -lah ~/rust > ~/rust/lsout.txt
cat ~/rust/lsout.txt 
```

*Results:*
```
total 8.0K
drwxr-xr-x   7 jameshaston staff  224 Aug 15 19:51 .
drwxr-x---+ 82 jameshaston staff 2.6K Aug 15 19:52 ..
-rw-r--r--   1 jameshaston staff 6.1K Aug 14 21:08 .DS_Store
drwxr-xr-x   3 jameshaston staff   96 Aug 12 01:36 cli-apps
drwxr-xr-x   6 jameshaston staff  192 Aug 14 21:08 interpreter
drwxr-xr-x   4 jameshaston staff  128 Aug 12 01:38 learning
-rw-r--r--   1 jameshaston staff    0 Aug 15 19:55 lsout.txt
```

Use `>>` to append output to the file. 

```sh
echo "this is appended text..." >> ~/rust/lsout.txt
cat ~/rust/lsout.txt
```

*Results:*
```
total 8.0K
drwxr-xr-x   7 jameshaston staff  224 Aug 15 19:51 .
drwxr-x---+ 82 jameshaston staff 2.6K Aug 15 19:52 ..
-rw-r--r--   1 jameshaston staff 6.1K Aug 14 21:08 .DS_Store
drwxr-xr-x   3 jameshaston staff   96 Aug 12 01:36 cli-apps
drwxr-xr-x   6 jameshaston staff  192 Aug 14 21:08 interpreter
drwxr-xr-x   4 jameshaston staff  128 Aug 12 01:38 learning
-rw-r--r--   1 jameshaston staff    0 Aug 15 19:55 lsout.txt
this is appended text...
```

## `stdout` and `stderr`

There are a few ways to handle `stdout` and `stderr`. The following examples
will produce different results. 

```sh
ls -lah /tnt > ~/rust/mylogfile.txt 2>&1 
cat ~/rust/mylogfile.txt
```

*Results:* `ls: cannot access '/tnt': No such file or directory`

The command above will send the `stdout` and `stderr` output to a file called
`mylogfile.txt`.

The following command will send `stdout` and `stderr` to both the screen and to
a file using a pipe `|` redirection and the `tee` command.

Note that `tee` is a command to read from standard input and write to standard 
output and files.

```sh
ls -lah /tnt 2>&1 | tee ~/rust/screen-and-log.txt
cat ~/rust/screen-and-log.txt
```

*Results:*
```
ls: cannot access '/tnt': No such file or directory
```

To redirect standard input, use the `more` command to read the `lsout.txt` file
as input and then pipe it to the `grep` command and search for all lines that
contain the word "appended" in the file. 

`more` is a command to interactively display a file, allowing scrolling and
searching.

```sh
more ~/rust/lsout.txt | grep -i appended
```

*Results:* `this is appended text...`

# Here Documents

`<<-EOF` is a syntax used in a `here-document`. It uses I/O redirection to feed
a list of commands to an interactive program until reaching the specified 
delimiter, which is `EOF` (end-of-file) in this case. 

## Heredoc Example

Create a shell script to create a basic `html` page, and then call the command 
and redirect its output to a new `index.html`. 

```bash
#!/usr/bin/env zsh

# a script to make an html page.

cat <<-EOF
<HTML>
<HEAD>

<TITLE>
my first heredoc
</TITLE>
</HEAD>

<Body>
<H1>my first heredoc</H1>
</Body>
</HTML>

EOF
```

Then call the script and redirect it to `index.html`. 

```sh
chmod +x heredoc.sh
./heredoc.sh > index.html
```














