```
██╗   ██╗██╗███╗   ███╗ ██████╗  ██████╗ 
██║   ██║██║████╗ ████║██╔════╝ ██╔═══██╗
██║   ██║██║██╔████╔██║██║  ███╗██║   ██║
╚██╗ ██╔╝██║██║╚██╔╝██║██║   ██║██║   ██║
 ╚████╔╝ ██║██║ ╚═╝ ██║╚██████╔╝╚██████╔╝
  ╚═══╝  ╚═╝╚═╝     ╚═╝ ╚═════╝  ╚═════╝ 
```
# Vimgo
Vimgo is a vim configuration that I used in daily coding. It is still in progress, but will become better and better.

## Prerequisite
Vimgo uses [vim-airline](https://github.com/vim-airline/vim-airline). For the nice looking powerline symbols to appear, you will need to install [powerline fonts](https://github.com/powerline/fonts). Installation instructions can be found in this [documentation](https://github.com/powerline/fonts#installation).

## Install
To install vimgo, simply do following in your terminal: 
```
git clone https://github.com/aizpy/vimgo.git ~/.vimgo
cd ~/.vimgo && ./install.sh
```

## Screenshots
<img width="1280" alt="Fullscreen_2019_5_24__11_15_AM" src="https://user-images.githubusercontent.com/15732419/58300837-ce7a1b80-7e16-11e9-8065-912fc8fd8e70.png">

<img width="1280" alt="Fullscreen_2019_5_24__11_18_AM" src="https://user-images.githubusercontent.com/15732419/58300849-d8038380-7e16-11e9-8edc-85b936460e17.png">

<img width="1280" alt="Fullscreen_2019_5_24__11_19_AM" src="https://user-images.githubusercontent.com/15732419/58300852-dc2fa100-7e16-11e9-8cdb-f97c5eb589ba.png">

<img width="1280" alt="Fullscreen_2019_5_24__11_20_AM" src="https://user-images.githubusercontent.com/15732419/58300864-e487dc00-7e16-11e9-9ff1-933b5381a336.png">

<img width="1280" alt="Fullscreen_2019_5_24__11_22_AM" src="https://user-images.githubusercontent.com/15732419/58300871-e782cc80-7e16-11e9-822c-1c46d65b76a1.png">

## Included Plugins

### Start Screen
* [Startify](https://github.com/mhinz/vim-startify): Provides a start screen for Vim and Neovim.

### File/Buffer Explorer

* [vinegar](https://github.com/tpope/vim-vinegar): Combine with netrw to create a nice file system explorer. vinegar is my first choice to explore file system. You can toggle it on with `-`.
* [NERDTree](https://github.com/scrooloose/nerdtree): In case you don't like vinegar, NERDTree is your second choice.
* [BufExplorer](https://github.com/vim-scripts/bufexplorer.zip): Easily switch between buffers. Can be opened with `<leader+o>`.
* [MRU](https://github.com/vim-scripts/mru.vim): Most recently used buffer. Can be opened with `<leader+f>`.

### Fuzzy Finding
* [CtrlP](https://github.com/ctrlpvim/ctrlp.vim): Fuzzy file, buffer, mru and tag finder. Can be opened with `<Ctrl+F>`.
* [fzf](https://github.com/junegunn/fzf.vim): Fzf wrapper for vim. Use `<Ctrl-B>` to open `BTags`, which is somewhat like **Goto Symbol...** feature using in Sumblime Text editor. If you had installed [rg](https://github.com/BurntSushi/ripgrep), with fzf you can search `rg` results with `:Rg [PATTERN]`.

### Lint
* [ale](https://github.com/w0rp/ale): Syntax and lint checking for vim (async).

### Git
* [vim-fugitive](https://github.com/tpope/vim-fugitive): A Git wrapper so awesome.

### Auto Completion
* [coc.nvim](https://github.com/neoclide/coc.nvim): Intellisense engine for vim8 & neovim, full language server protocol support as VSCode.
* [snippets](https://github.com/honza/vim-snippets): Snippets files for various programming languages.

### Languages
* [polyglot](https://github.com/sheerun/vim-polyglot): A collection of language packs for Vim.

### Status Line
* [vim-airline](https://github.com/vim-airline/vim-airline): Lean & mean status/tabline for vim that's light as air.

### Yank
* [vim-yankstack](https://github.com/maxbrunsfeld/vim-yankstack): Maintains a history of previous yanks, changes and deletes

### Misc
* [commentary](https://github.com/tpope/vim-commentary): Comment stuff out.  Use `gcc` to comment out a line (takes a count), `gc` to comment out the target of a motion. `gcu` uncomments a set of adjacent commented lines.
* [Multiple Cursors](https://github.com/terryma/vim-multiple-cursors): Sublime Text style multiple selections.
* [IndentLine](https://github.com/Yggdroot/indentLine): Display the indention levels with thin vertical lines.
* [Auto Pairs](https://github.com/jiangmiao/auto-pairs): Insert or delete brackets, parens, quotes in pair.

## Key Mappings

### Basic
```vim
" With a map leader it's possible to do extra key combinations
" like <leader>w saves the current file
let mapleader = ","

" Smart way to move between windows
map <C-j> <C-W>j
map <C-k> <C-W>k
map <C-h> <C-W>h
map <C-l> <C-W>l

" Switch CWD to the directory of the open buffer
map <leader>cd :cd %:p:h<cr>:pwd<cr>

" Disable highlight when <leader><cr> is pressed
map <silent> <leader><cr> :noh<cr>

" Useful mappings for managing tabs
map <leader>tn :tabnew<cr>
map <leader>to :tabonly<cr>
map <leader>tc :tabclose<cr>
map <leader>tm :tabmove

" remove trailing space
map <leader>ts :%s/\s\+$//e<cr>:noh<cr>:w<cr>
```

### Plugins
```vim
"
" ==============> coc <==============
"

" Use <cr> to confirm completion, `<C-g>u` means break undo chain at current position.
" Coc only does snippet and additional edit on confirm.
inoremap <expr> <cr> pumvisible() ? "\<C-y>" : "\<C-g>u\<CR>"
inoremap <expr> <tab> pumvisible() ? "\<C-y>" : "\<tab>"

" Use `[c` and `]c` to navigate diagnostics
nmap <silent> [c <Plug>(coc-diagnostic-prev)
nmap <silent> ]c <Plug>(coc-diagnostic-next)

" Remap keys for gotos
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

" Use K to show documentation in preview window
nnoremap <silent> K :call <SID>show_documentation()<CR>

function! s:show_documentation()
  if (index(['vim','help'], &filetype) >= 0)
    execute 'h '.expand('<cword>')
  else
    call CocAction('doHover')
  endif
endfunction

" Remap for do codeAction of selected region, ex: `<leader>aap` for current paragraph
xmap <leader>a  <Plug>(coc-codeaction-selected)
nmap <leader>a  <Plug>(coc-codeaction-selected)

" Remap for do codeAction of current line
nmap <leader>ac  <Plug>(coc-codeaction)
" Fix autofix problem of current line
nmap <leader>qf  <Plug>(coc-fix-current)

" Use <C-l> for trigger snippet expand.
imap <C-l> <Plug>(coc-snippets-expand)

" Use <C-j> for select text for visual placeholder of snippet.
vmap <C-j> <Plug>(coc-snippets-select)

" Use <C-j> for jump to next placeholder, it's default of coc.nvim
let g:coc_snippet_next = '<tab>'

" Use <C-k> for jump to previous placeholder, it's default of coc.nvim
let g:coc_snippet_prev = '<s-tab>'

" Use <C-j> for both expand and jump (make expand higher priority.)
imap <C-j> <Plug>(coc-snippets-expand-jump)


"
" ==============> bufExplorer <==============
"
map <leader>o :BufExplorer<cr>


"
" ==============> NERDTree <==============
"
map <leader>nn :NERDTreeToggle<cr>
map <leader>nb :NERDTreeFromBookmark<Space>
map <leader>nf :NERDTreeFind<cr>

"
" ==============> ale <==============
"
nmap <silent> <leader>a <Plug>(ale_next_wrap)

"
" ==============> fzf <==============
"
map <c-b> :BTags<cr>

"
" ==============> CtrlP <==============
"
let g:ctrlp_map = '<c-f>'

"
" ==============> Fugitive <==============
"
map ;s :Gstatus<cr>
map ;c :Gcommit<cr>
map ;d :Gdiff<cr>
map ;f :Gpush<cr>
map ;b :Gpull<cr>

"
" ==============> MRU <==============
"
map <leader>f :MRU<CR>
```
## License
[MIT License](https://github.com/pyericz/vimgo/blob/master/LICENSE)
