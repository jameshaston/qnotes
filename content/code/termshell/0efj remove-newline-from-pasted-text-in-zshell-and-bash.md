---
title: remove newline from pasted text in zshell and bash
tags: [tr, zsh, shell, cli, commands] 
id: 0efj
date: 2024-08-26
time: 22:38
---

# Use `tr` to Remove Newline from Pasted Text

The `tr` command can remove characters from text. 

```bash
echo "ayyyy 

supppp"
```

*Results:*
```
ayyyy 

supppp
```

```bash
echo "ayyyy supppp" | tr -d '\n'
```

*Results:* `ayyyy supppp`

# Zk Reference Notes

- node: [termshell-node](z6c7-termshell-node.md)
- [zsh shell resources](34nc%20zsh-shell-resources.md)
- [bash scripting for beginners](8q65%20bash-scripting-for-beginners.md)
- [zsh cheatsheet](19lq%20zsh-cheatsheet.md)

