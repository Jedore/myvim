# vimrc for windows

### Get Start
- Install vim to `D:\Git\Vim`
- Set ENV `VIM` to `D:\Git\vim`
- Install [vundle](https://github.com/VundleVim/Vundle.vim)  
  Create `vimfiles\bundle` directory in `$VIM`.  
  Execute `git clone https://github.com/VundleVim/Vundle.vim.git` in `vimfiles\bundle`.  
  Put this at the top of your `.vimrc` to use Vundle. Remove plugins you don't need, they are for illustration purposes.

  ```shell
  set nocompatible              " be iMproved, required
  filetype off                  " required
  
  " set the runtime path to include Vundle and initialize
  set rtp+=$VIM/vimfiles/bundle/Vundle.vim
  call vundle#begin('$VIM/vimfiles/bundle/')
  " alternatively, pass a path where Vundle should install plugins
  "call vundle#begin('~/some/path/here')
  
  " let Vundle manage Vundle, required
  Plugin 'VundleVim/Vundle.vim'
  
  " Keep Plugin commands between vundle#begin/end.
  
  " All of your Plugins must be added before the following line
  call vundle#end()            " required
  filetype plugin indent on    " required
  " To ignore plugin indent changes, instead use:
  "filetype plugin on
  
  " Brief help
  " :PluginList       - lists configured plugins
  " :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
  " :PluginSearch foo - searches for foo; append `!` to refresh local cache
  " :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
  
  " see :h vundle for more details or wiki for FAQ
  " Put your non-Plugin stuff after this line
  ```

- some configuration
  ```shell
  set spell
  set nobackup
  set noswapfile
  set noundofile
  set nonu
  set tabstop=4
  set encoding=utf8
  syntax enable

  colorscheme solarized
  set bg=dark

  set guifont=Source_Code_Pro:h13:cANSI
  
  "solve messy code after set encoding=utf8
  source $VIMRUNTIME/delmenu.vim
  source $VIMRUNTIME/menu.vim
  
  " for gvim on MS windows
  source $VIMRUNTIME/mswin.vim
  
  " reset mapleader
  let mapleader=" "
  let maplocalleader=" "
  
  " for moving across multi windows
  :nnoremap <leader>j <C-w>j
  :nnoremap <leader>k <C-w>k
  :nnoremap <leader>h <C-w>h
  :nnoremap <leader>l <C-w>l
  
  :nnoremap <leader>w :w<CR>
  :nnoremap <leader>q :q<CR>
  :nnoremap <leader>x :x<CR>

  " for buffer 
  :nnoremap <leader>bn :bn<CR>
  :nnoremap <leader>bp :bp<CR>
  :nnoremap <leader>bw :bw<CR>
  :nnoremap <leader>bd :bd<CR>
  
  " take effect not restarting gvim
  :nnoremap <leader>so :so $VIM\_vimrc<CR>

  " for markdown file format 
  autocmd FileType markdown setlocal tabstop=4
  let g:vim_markdown_folding_disabled = 1
  set conceallevel=2
    
  " for python file format 
  au BufNewFile,BufRead *.py 
  \ set tabstop=4 |
  set expandtab |
  set softtabstop=4 |
  set shiftwidth=4 |
  set textwidth=79 |
  set autoindent |
  set fileformat=unix

  " highlight unnecessary white space at line tail 
  highlight BadWhitespace ctermbg=red guibg=darkred
  au BufRead,BufNewFile *.py,*.pyw,*.c,*.h match BadWhitespace /\s\+$/

  " pydiction 
  let g:pydiction_location='$VIM/vimfiles/bundle/pydiction/complete-dict'
  ```

### Source Code Pro Font

- [Install](https://github.com/adobe-fonts/source-code-pro)

- configure
  ```
  set guifont=Source_Code_Pro:h13:cANSI
  ```

### Solarized theme
```shell
Plugin 'altercation/vim-colors-solarized.git'
```
```shell
colorscheme solarized
set bg=dark
```

### Markdown
```shell
Plugin 'plasticboy/vim-markdown'`
```
```shell
" for markdown file format
autocmd FileType markdown setlocal tabstop=4
let g:vim_markdown_folding_disabled = 1
set conceallevel=2
```

### Vim-airline
```shell
Plugin 'vim-airline/vim-airline'
```
```shell
" for status line
let g:airline#extensions#tabline#enabled = 1
```

### Auto-pairs
```shell
Plugin 'jiangmiao/auto-pairs'
```

### Pycdition
```shell
Plugin 'rkulla/pydiction'
```

### Sinify
```
Plugin 'mhinz/vim-signify'
```

### Correcting spelling mistakes on the fly
[reference](https://castel.dev/post/lecture-notes-1/)
```shell
" for spelling
setlocal spell
set spelllang=en_gb
inoremap <C-l> <c-g>u<Esc>[s1z=`]a<c-g>u
```
