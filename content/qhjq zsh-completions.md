---
id: qhjq
title: zsh completions
date: 2024-08-02
time: 22:56
keywords: [cli, zsh, completions, shell, bash] 
---

# Zsh Completions 

Learn how to setup completions for any command line interface tool, keep them
up to date, and how completions work in zsh in general. 

These notes are based on this [YouTube tutorial by DevInsideYou](https://youtu.be/BHxaUP0kz9w?si=XBmr1BPIoCNRhaM3). 

Completions are a feature of a shell that allows the shell to complete a command
for you, typically with a keymap such as `tab`. 

# `fpath`

Completions use files in `fpath` directories. Inside of the directories are files
that contain the completion functions, referred to as widgets in zsh. 

```bash
# view completions using the following commands
echo $fpath # space concatenated 

echo $FPATH # `:` concatenated
```

# Completions Directory 

Choose or make a directory to store all of your completion files, such as 
`~/.config/zsh/completions`.  You can choose any direcotry and then add that 
directory to your `.zshrc` file. 

```bash
# ~/.config/zsh/completions
fpath=($HOME/.config/zsh/completions $fpath)
# Enable the completion system
autoload compinit
# init all completions on fpath and ignore all insecure files and directories
compinit -i
```
































