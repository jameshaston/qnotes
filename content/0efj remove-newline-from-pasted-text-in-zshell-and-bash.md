---
id: 0efj
title: remove newline from pasted text in zshell and bash
date: 2024-08-26
time: 22:38
keywords: [tr, zsh, shell, cli, commands] 
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
