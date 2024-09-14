---
id: xj9h
title: nvim practical guide
date: 2024-07-29
time: 18:04
keywords: [neovim, nvim]
---

# Nvim Practical Guide 

A practical, beginners-friendly overview of neovim (nvim) based on this [YouTube tutorial](https://youtu.be/23PjWcKnUZs?si=CdasFIeRgisE9UwL). 

## Modes

Nvim has different modes for completing different tasks in the editor. 

- Normal (default): for navigating and executing commands.
- Insert (`i`): for typing text. 
- Visual (`v`): for selecting text.
- Command (Ex or `:`): for executing commands.
- Replace (`r`): overwrites existing text.

Use the `esc` key to exit the existing mode and enter `normal` mode.

## Getting Help and Built-in Documentation

Vim comes with extensive built-in documentation. 

- `:help` opens general help.
- `:help {topic}` to get help on a specific topic.
- `ctrl-]` to follow the help tag.
- `ctrl-t` to go back in help tags.

Use `:help index` for a command list for each mode.

## Undo and Redo 

- `u` to undo last change.
- `ctrl-r` to redo the last undo change.
- `.` to repeat the last change.
- `U` to undo all changes on the last modified line.

## Movement

Navigate efficiently with the following `motions`.

- `w` next word; `b` beginning of word; `e` end of word.
- `W`, `B`, `E`, same as above but for space-separated words.
- `0` start of line; `$` end of line.
- `^` first non-blank character of the line.
- `gg` beginning of file; `G` end of file.
- `{number}G` specific line number.


## Text Objects

Vim understands text structures (objects) for efficient text editing.

- `w` word.
- `s` sentence. Make sure the sentence ends with a period `.`.
- `p` paragraph.
- `t` tag (html/xml).
- `"`, `'`, `` ` ``, `(`, `[`, `{`. 
- `i` inner and `a` around.

Examples:

- `diw` delete inner word.
- `ci"` change inside double quotes.
- `ya)` yank around parentheses.
- `vis` to select all words in a sentence.
- `V` to select the entire line.
- `Y` to yank the entire line.

## Operators

- `d` for delete (also cut).
    - use in combination with text objects like `w` etc.
- `c` change (delete and enter insert mode).
- `y` yank (copy).
- `>` indent to the right.
- `<` indent to the left (unident).
- `=` auto-indent.
- `gq` format text.

Use with count for more power! `d2w` to delete two words.

> Tip: Operators + Text Objects = Vim superpowers!

## Inserting Text

- `i` insert before cursor; `I` insert start of line.
- `a` insert after cursor; `A` insert end of line.
- `o` open line below; `O` open line above.

## Deleting and Changing Text

- `x` delete character under cursor; `X` delete character before cursor.
- `dw` delete word; `dd` delete line.
- `D` delete from cursor to end of line.
- `cc` change entire line; `C` change from cursor to end of line. 

## Copy and Paste

- `yy` or `Y` yank entire line.
- `yw` yank word.
- `y$` yank to end of line.
- `p` put after cursor.
- `P` put before cursor.

## Registers

Vim uses registers to store text. This is where copied or pasted text goes.

- `{register}y` yank into the specified register.
- `{register}p` paste into the specified register.
- `:reg` to view the contents of all registers.
- `"+y` yank to the system clipboard.
- `"+p` paste from the system clipboard.

Use `ctrl-r` in `insert` mode to view all registers. Also, use the Telescope 
plugin to view current registers and their contents. In my current configuration,
I use `<leader>tt` to open the Telescope main menu, and from there I can select
"registers" to view all of the registers and their contents. 

> Tip: Use named registers (a-z) for longer-term storage.

- `v` to enter character-wise visual mode.
- `V` to enter line-wise visual mode.
- `ctrl-v` to enter block-wise visual mode.
- `gv` to reselect the last visual selection.

After selecting, use operators like `d`, `y`, or `c`.

> Tip: Use `ctrl-v` to select a block, then `I` to insert at the beginning.

## Search and Replace

Find and modify text with ease.

- `/pattern` search forward.
- `?pattern` search backward. 
- `n` next match; `N` previous match. 
- `*` search for word under cursor. 
- `:s/old/new/` replace on current line. 
- `:%s/old/new/g` replace entire file. 
- `:%s/old/new/gc` replace with confirmation. 
- `:.,.+5s/old/new/g` replace in range (current line to 5 lines below) 

> Tip: Use `:%s//new/g` to replace last search with "new"

## Working with Multiple Files

Manage multiple files efficiently.

- `:e filename` to edit a file.
    - Use `ctrl-o` and `ctrl-i` to navigate between the files.
- `:bn` and `:bp` to navigate to next and previous buffers.
- `:ls` list all buffers.

Manage windows and tabs.

- `vne` to open a new vertical split, and then use `:e` to open a new file in that split.
- `ctrl-w s` or `:sp` to split a window horizontally.
- `ctrl-w v` or `:vsp` to split a window vertically.
- `:tabnew` to open a new tab.
- `gt` or `gT` to navigate between tabs. 

> Tip: Use `:e` to open a new file, then `ctrl-w v` to split vertically.

## Macros

Automate repetitive tasks with macros.

1. `q{register}` to start recording to a register (a-z).
2. Perform actions.
3. `q` to stop recording.
4. `@{register}` play the macro.
5. `@@` to repeat the last played macro.

Example: Record a macro to increment numbers and add a period.

1. `qa` start recording to register `a`.
2. `ctrl-a` to increment number.
3. `A.` to append a period.
4. `q` to stop recording.
5. `@a` to play, `10@a` to repeat 10 times. 

## Advanced Motions

Use advanced motions to move with precision.

- `%` jump to matching parenthesis or bracket.
- `f{char}` find character forward in line.
- `t{char}` until character forward in line.
- `F{char}` and `T{char}` backwards versions.
- `;` repeat last f, t, F, or T motion.
- `,` repeat last f, t, F, or T motion backwards.

> Tip: Use `f(` to jump to a parenthesis, then `%` to jump to its match.

## Marks and Jumps

Navigate within and between files.

- `m{a-zA-Z}` set a mark.
- `` ` {a-z}`` jump to mark in current buffer.
- `` ` {A-Z}`` jump to mark in any buffer.
- `ctrl-o` jump to older position.
- `ctrl-i` jump to newer position. 

> Tip: Use `` ` `` to jump back to the last jump position.




