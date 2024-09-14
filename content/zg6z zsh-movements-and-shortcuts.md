---
id: zg6z
title: zsh movements and shortcuts
date: 2024-08-11
time: 01:31
keywords: [zsh, movements, editing, vi, vi:mode, shortcuts] 
---

# Zsh Movements And Shortcuts 

See [zsh shell resources](34nc%20zsh-shell-resources.md) for documentation on zsh and builtin bindkeys.

## Navigation

- `alt f/b` previous/next word.
- `ctrl a/e` beggining/end of command.
- `ctrl xx` toggle between the start of line and the current cursor position.

## Editing

- `ctrl x,e` open command in editor.
- `ctrl k` cut from current position to end of line.
- `ctrl u` delete whole line.
- `alt w` delete from cursor to beginning of line.
- `alt l/u` lower/upper word.
- `alt c` capitalize the first char of current word. 
- `ctrl w` cut prev word.
- `alt .` or `!$` previous command's last argument.
- `!*` all args of the previous command.
- `alt t` swap current word with previous word.
- `ctrl y` paste.
- `ctrl _` undo most recent change.
- `alt r` cancel the changes, revert.

## Process

- `ctrl z` background/foreground job. Suspends the current fg job and moves to bg.
    - use `fg` to bring background job to foreground.

## History

- `ctrl r` history search through previous commands.
- `ctrl s` retrieve most recent command from history.

## Modes 

- `ctrl x,v` enter `vi` mode to use vi-like bindings.
- `set -o vi` enables vi mode for the current session.







