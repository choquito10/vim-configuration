# vim-configuration

set number 
" activar el clipboard 
set clipboard=unnamed
" espacios que hace al precionar tab
set tabstop=2
syntax enable 
set encoding=utf-8
set mouse=a
" tamaño de los espacios 
set sw=2 
set relativenumber 
set bg=dark 
" identar con buena manera
set breakindent
set smartindent 
" fondo blanco donde esta el cursor
set cul 
" colorear la palabra que se encontro en la busqueda
set hlsearch 
" buscar como buscan los browsers
set incsearch 
" no mostrar la posicion del cursor
set noru
" mostrar en el titulo de la terminal en que archivo estamos
set title
" abrir archivo a la derecha
set splitright
" muestra el autocompletado de la barra de comandos 
set wildmenu
set wildmode=longest:list,full
" Muestra siempre la barra de estado de vim
set laststatus=2
" los tres de abajo evitan guardar copias del archivo que se esta editando
set nobackup 
set noswapfile
set nowritebackup
" usar regex
set magic
" avisar de cambios sin guardar
set confirm
" evitar el tiempo de espera al oprimir el espacio
set timeoutlen=150
" no dejar los buffers abiertos
set hidden

call plug#begin('~/.vim/plugged')

Plug 'atahabaki/archman-vim' " tema 
Plug 'scrooloose/nerdtree' " ver directorios al lado 
Plug 'neoclide/coc.nvim', {'branch': 'release'} " autocompletado
Plug 'tpope/vim-commentary' " comentarios 
Plug 'prettier/vim-prettier', { 'do': 'npm install' } " prettier
Plug 'jiangmiao/auto-pairs' " cerrar comillas automaticamente
Plug 'alvan/vim-closetag' " cerrar tags automaticamente 

call plug#end()

" color de schema de tema
colorscheme archman

" tecla de atajos 
let mapleader=" "

" cerrar carpetas de al lado al elegir un archivo
let NERDTreeQuitOnOpen=1 

" quitar aviso de errores prettier
let g:prettier#quickfix_enabled=0

" formatear al guardar
autocmd TextChanged,InsertLeave *.js,*.jsx,*.mjs,*.ts,*.tsx,*.css,*.less,*.scss,*.json,*.graphql,*.md,*.vue,*.yaml,*.html PrettierAsync

" formatear con comillas simples
let g:prettier#config#config_precedence = 'file-override'
let g:prettier#config#single_quote = 'true'

" cuando formatea deje 2 espacios
let g:prettier#config#tab_width = 2 

" usar espacios en vez de tabs 
let g:prettier#config#use_tabs = 'false'

" cerrar tags automatico para esas extensiones
let g:closetag_filenames = '*.html,*.js,*.jsx,*.ts,*.tsx'

" tab para bajar en las  opciones
inoremap <expr> <Tab> pumvisible() ? "\<C-n>" : "\<Tab>"

" moverse entre las pestañas
nmap 0 :tabn<CR>
nmap 9 :tabp<CR>

" mover las pestañas para izquierda o derecha
nmap . :tabm +<CR>
nmap , :tabm -<CR>

" buscar archivo y abrirlo en nueva tab
nmap <leader>s :tabfind

nmap <leader>c :NERDTreeFind<CR>
nmap <leader>w :w<CR>
nmap <leader>q  :q<CR>
imap <leader>i <ESC>
xmap <leader>i <ESC>
cmap <leader>i <ESC>
nmap <leader>f /
nmap <leader>l :wincmd l<CR>
nmap <leader>h :wincmd h<CR>
nmap <leader>k :wincmd k<CR>
nmap <leader>j :wincmd j<CR>
