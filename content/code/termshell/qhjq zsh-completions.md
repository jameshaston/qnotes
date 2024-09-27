---
title: zsh completions
tags: [cli, zsh, completions, shell, bash] 
id: qhjq
date: 2024-08-02
time: 22:56
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

# Zk Reference Notes

- node: [termshell-node](z6c7-termshell-node.md)
- [zsh line editor](vyu9%20zsh-line-editor.md)
- [zsh completions](qhjq%20zsh-completions.md)
- [zsh shell expansion](vnp1%20zsh-shell-expansion.md)
- [zsh basic input and output redirection](t67j%20zsh-basic-input-and-output-redirection.md)
- [conditional statements in zsh](9izu%20conditional-statements-in-zsh.md)
- [loops in zsh](cegv%20loops-in-zsh.md)



