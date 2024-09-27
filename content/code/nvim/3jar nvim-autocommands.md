---
title: nvim autocommands
tags: [nvim, autocommands] 
id: 3jar
date: 2024-07-30
time: 17:52
---

# Nvim Autocommands 

These notes are based on this [YouTube tutorial](https://youtu.be/wX-KpX8tax8?si=o23l1ACGWSWpM9cX). 

Autocommands can help you automate repeitive tasks and improve efficiency and
productivity. They can integrate seamlessly with other tools, and trigger 
actions on specific events (file read/write, buffer enter/leave, etc.).

Autocommands can even integrate with external shell commands. See [nvim external shell commands](jic8%20nvim-external-shell-commands.md)
for an overview of shell commands.

> Autocommands in nvim execute specified commands automatically when a certain
> event occurs.

## Anatomy of an Autocommand

1. Create a group.
2. Create an event.
3. Create a pattern (filetype such as `*.rs` or `*.lua` etc.).
4. Create a command to execute.

```
autocmd [group] event pattern command
```

Nvim syntax:

```lua
vim.api.nvim_create_augroup("Group Name", {clear = true})
vim.api.nvim_create_autocmd({events}, {opts})
```

Alternative syntax using `vimscript`:

```vim
augroup mine | exe "au! BufRead *" | augroup END
augroup mine | exe "au BufRead * set tw=70" | augroup END
```

## Autocommand Flow

1. Trigger event {event}.
    - 'BufReadPre'.
    - 'BufWritePost'.
2. Trigger autocommands.
3. Execute {action} based on options.
    - group: 'MyGroup'.
    - pattern: '*.txt' or '*.md' etc.
    - callback: 'MyCallback'.
    - OR command: ':echo "hello"'.

## Helpful Autocommand Examples

Highlight yanked text:

```lua
vim.api.nvim_create_autocmd("TextYankPost", {
    pattern = "*",
    callback = function()
        vim.highlight.on_yank { higroup = "IncSearch", timeout = 250 }
    end,
})
```

The above example is triggered on the event `TextYankPost`. The pattern is `*`,
which means every file. Then, the autocommand procedes to trigger a lua 
function `callback`, which calls a built-in function to highlight text.

## Commands to Display Autocommands

| Command   | Description    |
|--------------- | --------------- |
| `:autocmd`   | Lists all currently defined autocmds.   |
| `:autocmd {event}`   | Shows autocmds for an event.   |
| `:verbose autocmd {event}`   | Detailed info about autocmds for specific events.   |
| Telescope autocommands | Lists all autocmds and fuzzy find. |

## Documentation

- [Lua Autocommands Reference for Nvim](https://neovim.io/doc/user/lua-guide.html#_autocommands).
- [TJ Lua Autocommands Intro](https://youtu.be/ekMIIAqTZ34?si=jNd8sXW5jdMv5Fwp). 
- [TJ Lua Augroups](https://youtu.be/F6GNPOXpfwU?si=Li83QgozVsQ4gbQR). 
- [Andrew Courter Autocommands Intro](https://youtu.be/qN6BuJpsFbQ?si=u6Is04NK9eOTQwFR).

# Zk Reference Notes

- node: [nvim-node](u2cu-nvim-node.md)
- [Custom Lua Functions in Nvim](flgu%20custom-lua-functions-in-nvim.md)
- [lua nvim docs](ttd3%20lua-nvim-docs.md)


