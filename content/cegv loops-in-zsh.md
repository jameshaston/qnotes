---
id: cegv
title: loops in zsh
date: 2024-08-15
time: 20:52
keywords: [zsh, loops] 
---

# Loops In Zsh 

These notes are based on the book `Introduction to Shell Scripting Using Zsh`
located on my local machine at `~/Documents/books/zsh-shell-scripting.pdf`.

In this lesson we will cover `for`, `until`, and `while` loops using zsh. 

# Loop Types Explained

The `for` loop is a little different from other programming languages. Basically,
it let's you iterate over a series of words within a string. 

The `while` loop executes a piece of code if the control expression is `true`,
and only stops when the expression evaluates to `false` or an explicit break is
found in the code block. 

The `until` loop is almost equal to the `while` loop, except that the code is 
executed while the control expression evaluates to `false`. 

# `for` Loop 

Let's create a `for` loop to list the files and directories in the current working
directory as a basic example. 

```sh
#!/usr/bin/env zsh
for i in $( ls -p ~/rust ); do
echo item: $i
done
```

*Results:*
```
item: cli-apps/
item: interpreter/
item: learning/
item: lsout.txt
item: mylogfile.txt
item: screen-and-log.txt
```

# Until Loop Example 

```bash
#!/usr/bin/env zsh

counter=1
until [ $counter -gt 10 ]; do
echo $counter
((counter++))
done
echo "Until loop completed."
```

*Results:*
```
1
2
3
4
5
6
7
8
9
10
Until loop completed.
```

# While Loop Example

```bash
#!/usr/bin/env zsh
counter=1
while [ $counter -le 10 ]; do
echo $counter
((counter++))
done
echo "While loop completed."
```

*Results:*
```
1
2
3
4
5
6
7
8
9
10
While loop completed.
```












