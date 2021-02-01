set number
set nocompatible
set exrc
set belloff=all
set signcolumn=yes
set relativenumber
set nohlsearch
set updatetime=300
set shortmess+=c
set numberwidth=1
set clipboard=unnamed
syntax enable
set showcmd
set encoding=utf-8
set showmatch
set sw=2
set laststatus=2
set scrolloff=15
set noshowmode
set bg=dark
set tabstop=2
set breakindent
set smartindent
set cul
set incsearch
set wrap
set wildmenu
set wildmode=longest:list,full
set nobackup
set noswapfile
set nowritebackup
set hidden
set magic
set timeoutlen=150
set cmdheight=1
set path+=**


call plug#begin('~/.vim/plugged')

Plug 'morhetz/gruvbox' "tema
Plug 'scrooloose/nerdtree' " ver directorios al lado
Plug 'jiangmiao/auto-pairs' " cerrar comillas automaticamente
Plug 'alvan/vim-closetag' " cerrar tags automaticamente
Plug 'mg979/vim-visual-multi', {'branch': 'master'} " muchos cursores
Plug 'neoclide/coc.nvim', {'branch': 'release'} " autocompletado

call plug#end()

colorscheme gruvbox
let g:gruvbox_contrast_dark = "hard"

let mapleader=" "

let NERDTreeQuitOnOpen=1
let NERDTreeAutoDeleteBuffer=1
let NERDTreeMinimalUI=1
let NERDTreeDirArrows=1
let NERDTreeShowLineNumbers=1
let NERDTreeMapOpenInTab='<tab>'


let g:javascript_plugin_flow = 1


nmap <leader>c :NERDTreeFind<ENTER>

nmap ' :tabn <CR>
nmap ¡ :tabp <CR>
nmap - :tabm + <CR>
nmap , :tabm - <CR>

nmap <leader>w :w<ENTER>
imap <Space>i <Esc>
cnoremap <Space>i <Esc>
onoremap <Space>i <Esc>
xnoremap <Space>i <Esc>
nmap <leader>q :q<ENTER>
nmap <leader>f /
nmap <leader>s :tabf
nmap <leader>l :wincmd l<ENTER>
nmap <leader>h :wincmd h<ENTER>
nmap <leader>k :wincmd k<ENTER>
nmap <leader>j :wincmd j<ENTER>
nmap <leader>b <C-v>

" cambiar el modo del puntero segun el modo
let &t_SI = "\e[6 q"
let &t_EI = "\e[2 q"
let &t_SR = "\e[4 q"

" usar tab para elegir opcion
inoremap <expr> <TAB> pumvisible() ? "\<C-n>" : "\<TAB>"
inoremap <expr> <S-TAB> pumvisible() ? "\<C-p>" : "\<TAB>"
" usar enter para seleccionar opcion de menu
inoremap <expr> <CR> pumvisible() ? "\<C-y>" : "\<C-g>u\<CR>"

" quitar los espacios extras al guardar

fun! TrimWhitespace()
    let l:save = winsaveview()
    keeppatterns %s/\s\+$//e
    call winrestview(l:save)
endfun

augroup THE_PRIMEAGEN
    autocmd!
    autocmd BufWritePre * :call TrimWhitespace()
    " autocmd VimEnter * :VimApm
    autocmd BufEnter,BufWinEnter,TabEnter *.rs :lua require'lsp_extensions'.inlay_hints{}
augroup END
