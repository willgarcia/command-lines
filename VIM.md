vim - history
-------------

```shell
q:
```

vim - execute bash command while still in vim
---------------------------------------------

```shell
:! <command>
```

vim - autocomplete
------------------

```shell
CTRL+n
```

vim - .vimrc
------------

```shell
call plug#begin('~/.vim/plugged')

Plug 'rstacruz/vim-closer'

Plug 'junegunn/seoul256.vim'

Plug 'scrooloose/syntastic'
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'Xuyuanp/nerdtree-git-plugin'

Plug 'bling/vim-airline'

call plug#end()

let g:seoul256_background = 236
colo seoul256

map <C-n> :NERDTreeToggle<CR>

set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

set incsearch

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

set laststatus=2
```
