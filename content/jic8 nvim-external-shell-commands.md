---
id: jic8
title: nvim external shell commands
date: 2024-07-29
time: 20:36
keywords: [nvim, neovim, shell, commands] 
---

# Nvim External Shell Commands 

Vim has the feature to run external shell commands from within neovim.

References for these notes:

- These notes are based on this [YouTube tutorial](https://youtu.be/H7frd02OUps?si=J2zcKL43LUUQJJNM). 
- See [nvim practical guide](xj9h%20nvim-practical-guide.md) for a basic overview of editing in nvim.
- See [lua nvim docs](ttd3%20lua-nvim-docs.md) for using lua in nvim.

## Vim External Commands: Quick Reference

- `:!{cmd}` execute shell command, display output.
- `:r !{cmd}` execute shell command, insert output below cursor.
- `:w !{cmd}` send current buffer as stdin to command.
- `:.!{cmd}` replace current line with command output.
    - `.` is a placeholder for the current line.
- `:%!{cmd}` replace entire buffer with command output.
- `'<,'>!{cmd}` replace selection with command output.

## Practical Examples

The following are some practical examples of using external shell commands in
nvim.

### 1. Quick File Backup with `:!{cmd}`

Create a backup of the current file.

1. Open a file inside of nvim.
2. Enter the shell command below and press enter.

```sh
:!cp % new_%
```

The command above calls the `cp` shell command, passes `%` to represent the current
file, and then creates a new file with the name `new_{filename}`, where `%` is
the name of the file you first opened. 

### 2. Insert External Date with `:r !{cmd}`

Using `:r !date`, we can insert the shell output of the `date` command into the
current buffer on the line of the cursor.

```sh
:r !date # -> Mon Jul 29 22:33:24 PDT 2024
```

The command above starts with `:r` to represent `read`. This command executes
a shell command, in this case `date`, takes the shell output of the command,
and inserts it into the current buffer at the current cursor position. 

## 3. Use Buffer as Command Input with `:w !{cmd}`

Example: Create files from buffer content. One line in the buffer is passed as an argument
to the shell command at a time.

```markdown
The current buffer contains the following lines:

file1_test
file2_test
file3_test
```

The lines in the buffer can be passed to an external shell command to create
files named after each line in the buffer.

```vim
:w !xargs touch
```

The above command creates the files `file1_test`, `file2_test`, and `file3_test`.

## 4. Line and Selection Manipulation

Example: pretty print JSON on the current line.

```json
{"name": "James","age": 35,}
```
If the above json was not formatted, you could call `jq` to format it and
insert the pretty-printed json data on the current line.

```vim
:.!jq .
```

Where `.` represents the current line in the current buffer. 

You can also use visual selection to select text to be manipulated via a 
shell command using `:'<,'>!{cmd}`


## 5. Custom Key Bindings for Shell Integration

You can create custom key bindings for your favorite external shell commands.
Here are some helpful examples.

```lua
-- execute current line and output to command line
vim.keymap.set("n", "<leader>ex", ":.w !bash -e<cr>", opts)

-- execute all lines and output to command line
vim.keymap.set("n", "<leader>eX", ":%w !bash -e<cr>", opts)

-- execute current line and replace with result
vim.keymap.set("n", "<leader>el", ":.!bash -e<cr>", {noremap = true, silent = false })

-- execute all lines and replace with result
vim.keymap.set("n", "<leader>eL", ":% !bash %<cr>", opts)

-- make file executable
vim.keymap.set("n", "<leader>cx", ":!chmod +x %<cr>", opts)

-- execute file and show output
vim.keymap.set("n", "<leader>ef", "<cmd>lua *G.execute*file_and_show_output()<cr>", {noremap = true, silent = false })
```

You can create your own shell scripts or functions and call those using external
shell commands in nvim.




