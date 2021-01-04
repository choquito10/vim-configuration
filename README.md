#vim
set number
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
set noshowmode
set bg=dark
set ignorecase                
set tabstop=2 
set breakindent 
set smartindent
set cul
set hlsearch
set incsearch
set wildmenu 
set wildmode=longest:list,full
set nobackup 
set noswapfile 
set nowritebackup
set magic
set confirm
set timeoutlen=150
set cmdheight=1


call plug#begin('~/.vim/plugged')

Plug 'morhetz/gruvbox' "tema
Plug 'scrooloose/nerdtree' " ver directorios al lado 
Plug 'jiangmiao/auto-pairs' " cerrar comillas automaticamente 
Plug 'alvan/vim-closetag' " cerrar tags automaticamente
Plug 'valloric/youcompleteme' "autocompletado
Plug 'mg979/vim-visual-multi', {'branch': 'master'} " muchos cursores
Plug 'prettier/vim-prettier', { 'do': 'npm install' } " formateador

call plug#end()


colorscheme gruvbox
let g:gruvbox_contrast_dark = "hard"

let mapleader=" "

let NERDTreeQuitOnOpen=1
let NERDTreeAutoDeleteBuffer=1
let NERDTreeMinimalUI=1
let NERDTreeDirArrows=1
let NERDTreeShowLineNumbers=1
let NERDTreeMapOpenInTab='<ENTER>'

nmap <leader>c :NERDTreeFind<ENTER>

nmap 0 :tabn <CR>
nmap 9 :tabp <CR>
nmap . :tabm + <CR>
nmap , :tabm - <CR>

nmap <leader>w :w<ENTER> 
imap <Space>i <Esc>
cnoremap <Space>i <Esc>
onoremap <Space>i <Esc>
xnoremap <Space>i <Esc>
nmap <leader>q :q<ENTER>
nmap <leader>f /
nmap <leader>l :wincmd l<ENTER> 
nmap <leader>h :wincmd h<ENTER> 
nmap <leader>k :wincmd k<ENTER> 
nmap <leader>j :wincmd j<ENTER> 
nmap <leader>b <C-v>


" cambiar el modo del puntero segun el modo
let &t_SI = "\e[6 q"
let &t_EI = "\e[2 q"
let &t_SR = "\e[4 q"

autocmd BufWritePre *.js,*.jsx,*.mjs,*.ts,*.tsx,*.css,*.less,*.scss,*.json,*.graphql PrettierAsync
let g:prettier#autoformat = 0
let g:prettier#exec_cmd_path = "~/path/to/cli/prettier"
let g:prettier#config#single_quote = 'true'
let g:prettier#quickfix_enabled=0
let g:prettier#config#trailing_comma = 'all'
let g:prettier#config#print_width = 80
