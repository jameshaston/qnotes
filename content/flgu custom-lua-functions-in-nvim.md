---
id: flgu
title: Custom Lua Functions in Nvim
date: 2024-07-30
time: 18:44
keywords: [nvim, lua, functions, modules] 
---

# Custom Lua Functions in Nvim 

These notes are based on this [YouTube tutorial](https://youtu.be/R1ecY30YBVk?si=B_M_3ie03dNb00Rz).

## Introduction

Why would you want to create your own lua functions and modules for nvim?

- Enhance nvim with `lua` functions.
- Customize your text editing experience.
- Integrate with nvim features and plugins.
- Write your own modules, utilities, functions, etc.
- Create your own nvim plugin to share with the community.

## When to Use Functions

If you are simplifying a repetitive task, such as basic text manipulation,
that is a good candidate for `macros`. For more complex behavior, `lua` functions 
are a great option. 

- Simple tasks -> macros.
- Complex operations or features -> lua functions.
- Advanced, custom behavior -> plugins.

## Lua API in Nvim

See [lua nvim docs](ttd3%20lua-nvim-docs.md) for the doc reference for using the lua api in nvim.

```lua
vim.cmd() -- vim api: external commands, vimscript functions
vim.fn -- access vim functions
vim.api -- nvim api for remote plugins and GUI
vim.* -- lua specific functions
```

Also see `:h lua` or `:h lua-{function}` for help inside nvim. More help topics
are available with `:helpgrep lua{*}` for more help.

## Using Lua in Nvim

Use `:lua` to run `lua` code in nvim. Here are some examples:

- `:lua print('hello')` to call the lua `print` function and output 'hello'.
- `:lua =_G` to print global scope.
- `"dofile('myluafile.lua')` to load lua file to `_G` scope.
- `luafile myluafile.lua` to run the lua file.

## Loading Lua Modules in Nvim

A module name is the file name without the `.lua` extension.

```lua
require("mymodule")
require('folder_name.module')
mymod = require('module')

package.loaded['mymodule'] = nil -- clears cache of module, then load
require('mymodule')
```

## Creating and Loading `user_functions`

You can create your lua own functions and modules and store them in a directory that
nvim can access. 

First, create a directory for `user_functions`:

```sh
mkdir -p ~/.config/nvim/lua/user_functions
```

Then add the following code to the `init.lua` file:

```lua
for _, file in ipairs(vim.fn.readdir(vim.fn.stdpath "config" .. "/lua/user_functions", [[v:val =~ '\.lua$']])) do
    require("user_functions." .. file:gsub("%.lua$", ""))
end
```

The code snippet above enables automatic loading of all files in the `/user_functions` directory.

> See [Piotr1215 Nvim Config](https://github.com/Piotr1215/dotfiles/tree/master/.config/nvim) for implementation details and examples.

## Lua Modules and File Structure

- Organize `lua` code using modules.
- Use `require` to load `lua` files.
- Everything is a table!

```lua
-- example module
local M = {} -- {} is a lua table that can hold func, properties, etc.

-- use `M.{func}` to call function
function M.my_function()
    print('hi from my_module')
end

-- return module
return M
```

> Keep your `lua` code modular and maintainable.

## Writing a Basic Lua Function

Example of a simple function to greet a user in nvim.

```lua
-- greet.lua

-- create a greeting function
local function greet(name)
    print('Sup ' .. name) -- .. in lua is concatenation
end

-- usage: call function
greet('James')
```

Now the function is available in `greet.lua`. One way to call the function
is to run `:luafile {filename}` or `:luafile %` for the current file. 

Another way to use the `greet.lua` function is to add `require('user_functions.greet')`
to your `init.lua`, which will automatically call the `greet` function when loading
nvim.

## Development Tools for Lua

- `folke/neodev.nvim` for autocompletion of your lua code and lsp.
- `:h nvim-lua-guide` for comprehensive documentation.

## Developing a Window Zoom Module "Zoomer"

> Goal: Create a simple module to toggle window zooming.

The implementation of this module will be in `zoomer.lua`. To get started, 
open the `Telescope` main menu and search for `help`. Then fuzzy find the 
documentation related to `window` and related keywords.

### Start Small with Test Functions

```lua
-- zoomer.lua starter module
vim.cmd.wincmd "_" -- maximize current window height (ctrl-w-_)
vim.cmd.wincmd "|" -- maximize current widnwo width (ctrl-w-|)
```

### Build Out Functions

```lua
-- zoomer.lua

local zoomed = false

function zoom_toggle()
    if zoomed then
        vim.cmd.wincmd "=" --equalize window size
        zoomed = false
    else 
        vim.cmd.wincmd "_"
        vim.cmd.wincmd "|"
        zoomed = true
    end
end

return zoom_toggle
```

### Refactor Code into Lua Module

```lua
-- zoomer.lua
local M = {}
local zoomed = false

function M.zoom_toggle()
    if zoomed then
        vim.cmd.wincmd "=" --equalize window size
        zoomed = false
    else 
        vim.cmd.wincmd "_"
        vim.cmd.wincmd "|"
        zoomed = true
    end
end

return M -- a lua table containing the `zoom_toggle` function
```

### Add Custom Key Maps

```lua
-- zoomer.lua
local M = {}
local zoomed = false

function M.zoom_toggle()
    if zoomed then
        vim.cmd.wincmd "=" --equalize window size
        zoomed = false
    else 
        vim.cmd.wincmd "_"
        vim.cmd.wincmd "|"
        zoomed = true
    end
end

vim.keymap.set("n", "<leader>zom", M.zoom_toggle, {remap = true, silent = false})

return M -- a lua table containing the `zoom_toggle` function
```

## Related Zk Note References

- [nvim external shell commands](jic8%20nvim-external-shell-commands.md).
- [nvim external shell commands](jic8%20nvim-external-shell-commands.md).



