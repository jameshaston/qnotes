---
id: gyt5
title: wget introduction 
topic: wget command line interface
subtopic: shell cli tools 
date: 2024-07-21
time: 23:33
keywords: [wget, cli:tools, url, ftp, shell]
---

# Dowload Directory or File Using `wget` 

Using [wget](https://www.gnu.org/software/wget/manual/wget.html) , you can download files and directories from a specified url. For more information
and options, see `man wget`. To download multiple files from a directory, use the code snippet below.

This [wget cheetsheet](bqan%20wget-cheatsheet) provides a few examples using `wget` command line interface.

## Basic Usage

```sh
# download a file from a url.
wget url

# recursive download that does not download parent dir.
wget -r --no-parent url
```

## YouTube Tutorials for `wget`

- [wget CLI Tutorial](https://www.youtube.com/watch?v=xjavP081t1A)  
- [wget Examples and Options](https://www.youtube.com/watch?v=11AksshwGEU)  
- [wget Cheatsheet](https://github.com/mcandre/cheatsheets/blob/master/wget.md)  

## Alternatives

- `curl` 
- `lftp` specializes in FTP transfers 
- `scp` specializes in SSH file transfers 

## Related Topics

- Terminal
- Shell
- CLI Tools
