syntax enable
filetype off
set number
set exrc
set ruler
set nocompatible
set belloff=all
set signcolumn=yes
set relativenumber
set updatetime=50
set shortmess+=c
set clipboard=unnamed
set encoding=utf-8
set showcmd
set showmatch
set sw=2
set laststatus=2
set scrolloff=15
set noshowmode
set bg=dark
set tabstop=2
set cursorline
set incsearch
set breakindent
set wrap
set tw=90
set wildmenu
set wildmode=longest:list,full
set nobackup
set noswapfile
set nowritebackup
set hidden
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
Plug 'honza/vim-snippets' " atajos de teclado

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
let NERDTreeShowHidden=1

let g:javascript_plugin_flow = 1

nmap <leader>c :NERDTreeFind<ENTER>

nmap ¡ :tabn <CR>
nmap ' :tabp <CR>
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

" coc
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)


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


" mostrar documentacion de los metodos y funciones

nnoremap <silent> K :call <SID>show_documentation()<CR>
function! s:show_documentation()
if (index(['vim','help'], &filetype) >= 0)
execute 'h '.expand('<cword>')
else
call CocAction('doHover')
endif
endfunction


" Remove  flechas in Command Mode
cnoremap <Down> <Nop>
cnoremap <Left> <Nop>
cnoremap <Right> <Nop>
cnoremap <Up> <Nop>

" Remove flechas in Insert Mode
inoremap <Down> <Nop>
inoremap <Left> <Nop>
inoremap <Right> <Nop>
inoremap <Up> <Nop>

" Remove flechas in Normal Mode
nnoremap <Down> <Nop>
nnoremap <Left> <Nop>
nnoremap <Right> <Nop>
nnoremap <Up> <Nop>

" Remove flechas in Visual Mode
vnoremap <Down> <Nop>
vnoremap <Left> <Nop>
vnoremap <Right> <Nop>
vnoremap <Up> <Nop>


" extensiones coc
coc-snippets coc-prettier coc-html coc-git coc-emmet coc-tsserver coc-json coc-css

" coc-settings.json 'CocConfig
{
  "coc.preferences.formatOnSaveFiletypes": [
    "css",
    "markdown",
    "json",
    "javascript",
    "javascriptreact",
    "html"
  ],
  "prettier.printWidth": 90,
  "prettier.singleQuote": true,
  "prettier.disableSuccessMessage": true,
  "prettier.jsxSingleQuote": true,
  "prettier.arrowParens": "avoid",
  "prettier.proseWrap": "always",
  "diagnostic.level": "information"
}
