---
id: 50kx
title: create a dotfiles folder
date: 2024-07-27
time: 20:34
keywords: [dotfiles, config, gnu:stow] 
---

# Create A Dotfiles Folder 

Basic steps to create a dotfiles directory:

1. Create the directory in the correct location.
2. Move configuration files into the new directory.
3. Symlink the files to the original location. 
4. Verify that the setup works as expected.

## Dotfiles Directory

It's recommended to create the dotfiles directory in the home directory. For
example, create a `dotfiles` directory in `/Users/jameshaston/`.

```sh
$ pwd
/Users/jameshaston/

$ mkdir dotfiles
```

## Move Configuration Files to `~/dotfiles`

Now that the `~/dotfiles/` directory is created, move the config files that
you want to manage into the directory. For example, move your `.zshrc` file 
to the new dotfiles directory. 

```sh
mv ~/.config/zsh/.zshrc ~/dotfiles/ # OR

# create a `.config` directory in the `dotfiles/` directory
mkdir -p ~/dotfiles/.config/zsh/
mv ~/.config/zsh/.zshrc ~/dotfiles/.config/zsh/.zshrc 
```

This is an important step. You want to mirror the structure of your existing
`.config` directory.

## Symlink Files

Now create symbolic links to the original configuration file locations using `ln`.
We will use symlinks to create links back into the home directory for all of 
the configuration files and folder we moved. 

```sh
# Create a new symlink called ~/.zshrc which comes from
# `~/dotfiles/.config/zsh/.zshrc`
# link target-file-or-dir to existing-file-or-dir
ln -sf ~/dotfiles/.config/zsh/.zshrc ~/.config/zsh/.zshrc
```

### Create a symbolic link to a file or directory:

`ln -s /path/to/file_or_directory path/to/symlink`

### Overwrite an existing symbolic link to point to a different file:

`ln -sf /path/to/new_file path/to/symlink`

See `man ln` for details about the `ln` command and the [dotfiles](pdel%20dotfiles.md) note for usage
examples and documentation. 


