---
title: nvim lsp practical guide
tags: [nvim, lsp]
id: 2c8f
date: 2024-08-05
time: 14:46
---

# Nvim Lsp Practical Guide 

This [YouTube tutorial](https://youtu.be/0Jq-xkFqjSA?si=gIIE4BTO_iEsdqD_) covers setting up language server protocol servers in nvim.

Agenda:

- Configuring lsp
- Brief introduction to completion, snippets, and debugging
- Go through existing configuration and talk about recommendations
- Overview of plugins

> A great starter config is `kickstart nvim`. 

## How Does LSP Work

The language server protocol was developed by Microsoft to provide a standard protocol for
how servers and development tools interact and communicate. This way, a single lsp can 
be reused with numerous development tools. 

## LSP in Nvim

Nvim comes with a builtin client exposing API via `vim.lsp` and provides diagnostics with
`nvim.diagnostics`. Additionally, `lsp` commands are provided by `nvim-lspconfig`.

## Plugins 

- mason.nvim to manage external editor tooling (lsp, dap, linter, formatter).
- mason-lspconfig.nvim to handle nvim-lspconfig integration.
- nvim-lspconfig to configure lsp settings and language servers.

node: [nvim-node](u2cu-nvim-node.md)
