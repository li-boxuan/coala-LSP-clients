# vim language client for coala

[Language Server Protocol](https://github.com/Microsoft/language-server-protocol) (LSP) support for [vim](http://www.vim.org/) and [neovim](https://neovim.io/).

[![asciicast](https://asciinema.org/a/Jz0EzvqDK43ZQThB0Xa4xHnUo.png)](https://asciinema.org/a/Jz0EzvqDK43ZQThB0Xa4xHnUo)

## Dependency
* Python >= 3.4
* coala (see [install guide](http://docs.coala.io/en/latest/Users/Install.html))
* [coala Language Server](https://github.com/coala/coala-vs-code/)
* [LanguageClient-neovim](https://github.com/autozimu/LanguageClient-neovim)

## Features
* Linting for multiple languages.

## Quick Start
> This assumes you have coala installed and .coafile configured, but not LSP server & client

### Install coala Language Server

Clone or download [coala Language Server repository](https://github.com/coala/coala-vs-code/).

Set your environment variable. For example, run the following command in your terminal if you are using bash:

```shell
echo 'export PATH=/change_to_your_dir/coala-vs-code:$PATH'  >> ~/.bash_profile
```
Make sure ```coala-langserver.sh``` can be run in your terminal

### Install vim Language Client
Using [`vim-plug`](https://github.com/junegunn/vim-plug):

```vim
Plug 'autozimu/LanguageClient-neovim', {
    \ 'branch': 'next',
    \ 'do': 'bash install.sh',
    \ }

" (Optional) Multi-entry selection UI.
Plug 'junegunn/fzf'
```

Example configuration

```vim
let g:LanguageClient_serverCommands = {
    \ 'python': ['coala-langserver.sh'],
    \ 'javascript': ['coala-langserver.sh'],
    \ }
```
Please see [INSTALL](https://github.com/autozimu/LanguageClient-neovim/blob/next/INSTALL.md) for complete instructions for language client.

After installation of both language client and language server, restart neovim/vim and
language services will be available right away.

Note current coala Language Server only supports ```didSave``` action, i.e. you MUST save your file to trigger code analysis.
