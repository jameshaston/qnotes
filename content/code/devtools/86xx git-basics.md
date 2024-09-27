---
title: git basics
tags: [git, github] 
id: 86xx
date: 2024-08-11
time: 16:09
---

# Git Basics 

Git is a source control management tool. These notes are baded on this [video](https://youtu.be/tRZGeaHPoaw?si=Bp-UJbQDkWQa3_Pz). See
the [git book](https://git-scm.com/book/en/v2) for details and documentation. 

# Config

- `git config -h` for help. 
- `git config --global user.name` for global username.
- `git config --global user.email` for global user email. 
- `man git` and `git help <command>` for help.

# Basic Git Commands

## Initialize a Local Repository

Use `git init` inside a directory to initialize a directory. Then use `git status`
to see the details of the repository you just created. 

## Track and Untrack Files

To add files to the git repository, use the command `git add .` for all files
or `git add file.name` to add a specific file to the repository. Use 
`git rm --cached file.name` to remove a file from staging/tracking.

# Zk Reference Notes

- node: [devtools-node](3zgk-devtools-node.md)

