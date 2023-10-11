# NeoVIM

## User Interface

`:setlocal nonumber norelativenumber` - Disables line numbers

## Neovim for Beginners

https://alpha2phi.medium.com/learn-neovim-the-practical-way-8818fcf4830f#545a

### Neovim for Beginners - init.lua

https://alpha2phi.medium.com/neovim-for-beginners-init-lua-45ff91f741cb

https://github.com/alpha2phi/neovim-for-beginner/tree/01-init.lua

https://alpha2phi.medium.com/neovim-startup-screen-edd933ec8261

https://github.com/mhinz/vim-startify

https://alpha2phi.medium.com/12-neovim-themes-with-tree-sitter-support-8be320b683a4

https://github.com/folke/tokyonight.nvim

### Neovim for Beginners - Status Line

https://alpha2phi.medium.com/neovim-for-beginners-status-line-dd0c97fba978

https://github.com/nvim-lualine/lualine.nvim

https://github.com/nvim-tree/nvim-web-devicons

https://github.com/nvimdev/galaxyline.nvim

### Neovim for Beginners - File Explorer

#### Netrw commands

`:h netrw`

With `netrw` it is possible to browse local and remote files, e.g.:

`nvim .`

`nvim scp://somewhere/path/to/file`

`:[N]Explore[!] [dir]` - Explore the directory of the current file.

`:[N]Hexplore[!] [dir]` — Horizontal Split & Explore.

`:[N]Lexplore[!] [dir]` — Left Explorer Toggle.

`:[N]Sexplore[!] [dir]` — Split & Explore the current file’s directory.

`:[N]Vexplore[!] [dir]` — Vertical Split & Explore.

`:Texplore [dir]` — Tab & Explore.

`:Rexplore` — Return to/from the Explorer.

#### File Explroer

https://github.com/nvim-tree/nvim-tree.lua

https://github.com/nvim-tree/nvim-tree.lua/issues/767

https://alpha2phi.medium.com/neovim-for-beginners-file-explorer-a0b2e5cf6c57

https://stackoverflow.com/questions/69345321/nvim-tree-lua-installed-through-vundle-but-its-commands-dont-exist

## Modern Neovim

https://alpha2phi.medium.com/learn-neovim-the-practical-way-8818fcf4830f#8c31

### Modern Neovim - init.lua

https://alpha2phi.medium.com/modern-neovim-init-lua-ab1220e3ecc1

## Packer

```
nvim +PackerCompile

nvim +PackerUpdate

nvim +PackerInstall
```

https://github.com/wbthomason/packer.nvim

An autocommand can automatically run `:PackerCompile` whenever `plugins.lua` is updated:

```
augroup packer_user_config
  autocmd!
  autocmd BufWritePost plugins.lua source <afile> | PackerCompile
augroup end
```

This autocommand can be placed in you `init.vim`.
