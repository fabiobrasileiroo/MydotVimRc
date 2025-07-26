# MydotVimRc
My config vim

``` bash
" Ativa syntax highlight e indentação automática
syntax on
filetype plugin indent on

" Aparência
set number              " Números absolutos
set relativenumber      " Números relativos para navegação
set cursorline          " Destaca a linha atual
set background=dark     " Tema escuro
colorscheme gruvbox     " Tema: gruvbox (bonito e confortável)

" Tabs e indentação
set tabstop=2
set softtabstop=2
set shiftwidth=2
set expandtab
set smartindent
set autoindent

" Usabilidade
set clipboard=unnamedplus
set hidden
set nowrap
set backspace=indent,eol,start
set updatetime=1000

" Tecla líder (prefixo de atalhos)
let mapleader = ","

" Autosave ao sair do modo inserção, mover o cursor ou perder foco
autocmd InsertLeave,TextChanged,FocusLost,CursorHold * silent! write

" Instalação de plugins via vim-plug
call plug#begin('~/.vim/plugged')

" Tema gruvbox
Plug 'morhetz/gruvbox'

" JavaScript/TypeScript/JSX/TSX
Plug 'pangloss/vim-javascript'
Plug 'leafgarland/typescript-vim'
Plug 'peitalin/vim-jsx-typescript'

" HTML5/CSS3
Plug 'othree/html5.vim'
Plug 'hail2u/vim-css3-syntax'

" Auto complete (YCM requer build com suporte TS)
Plug 'ycm-core/YouCompleteMe'

" Linter e formatador (ALE)
Plug 'dense-analysis/ale'

" Prettier (formatador JS/TS/HTML etc.)
Plug 'prettier/vim-prettier', { 'do': 'npm install' }

call plug#end()

" ALE configurações (usa prettier ao salvar)
let g:ale_fix_on_save = 1
let g:ale_fixers = {
\   'javascript': ['prettier'],
\   'typescript': ['prettier'],
\   'typescriptreact': ['prettier'],
\   'javascriptreact': ['prettier'],
\   'json': ['prettier'],
\   'html': ['prettier'],
\ }

" Atalhos úteis
nmap <leader>f :Prettier<CR>
nmap <leader>e :ALEToggle<CR>

" Define a cor do cursor
highlight Cursor guifg=NONE guibg=gray
```

### Instale o **gerenciador de plugins**:

``` bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### Abra o vim e rode:

``` bash
:PlugInstall
```

### YouCompleteMe
``` bash
cd ~/.vim/plugged/YouCompleteMe
python3 install.py --ts-completer
```
