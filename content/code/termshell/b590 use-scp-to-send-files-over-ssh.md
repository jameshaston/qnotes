---
title: use scp to send files over ssh
tags: [scp, ssh, file, transfer] 
id: b590
date: 2024-08-25
time: 14:59
---

# Use Scp To Send Files Over Ssh 

The `scp` (secure copy) command is useful for sending files to a remote machine
over `ssh`. 

See `man scp` and `man ssh` for details. [This video](https://youtu.be/Aa7tKMmeFZI?si=1MzcZz-BQiywaHwz) provides a good overview
of the `scp` command. 

# Send a File to a Remote Machine

```bash
# scp filename dest-ip-or-server:/path/on/remote/machine
scp test.txt james@dev:/home/james 
```

# Transfer from a Remote Machine to a Local Machine

```bash
scp james@dev:/home/james/test.txt /home/james
```

You can use a `command` combined with `ssh` to perform an action on the remote
machine. 

```bash
# ssh <remote machine> ls
ssh dev ls
```

# Zk Reference Notes

- node: [termshell-node](z6c7-termshell-node.md)
- [zsh shell resources](34nc%20zsh-shell-resources.md)
- [bash scripting for beginners](8q65%20bash-scripting-for-beginners.md)
- [zsh shell expansion](vnp1%20zsh-shell-expansion.md)
- [zsh basic input and output redirection](t67j%20zsh-basic-input-and-output-redirection.md)

