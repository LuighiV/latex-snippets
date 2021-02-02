# Vim + LaTeX snippets setup

*[How I'm able to take notes in mathematics lectures using LaTeX and Vim](https://castel.dev/post/lecture-notes-1/)*

## Vim configuration

Copy `tex.snippets` to `~/.vim/UltiSnips/` and assuming you're using [Vim Plug](https://github.com/junegunn/vim-plug), add the following to your `.vimrc`:

```vim
Plug 'sirver/ultisnips'
    let g:UltiSnipsExpandTrigger = '<tab>'
    let g:UltiSnipsJumpForwardTrigger = '<tab>'
    let g:UltiSnipsJumpBackwardTrigger = '<s-tab>'

Plug 'lervag/vimtex'
    let g:tex_flavor='latex'
    let g:vimtex_view_method='zathura'
    let g:vimtex_quickfix_mode=0

Plug 'KeitaNakamura/tex-conceal.vim'
    set conceallevel=1
    let g:tex_conceal='abdmg'
    hi Conceal ctermbg=none

setlocal spell
set spelllang=en_us
inoremap <C-l> <c-g>u<Esc>[s1z=`]a<c-g>u
```

For the colorscheme, install [pywal](https://github.com/dylanaraps/pywal), add the following to your `.vimrc`

```vim
Plug 'dylanaraps/wal'
colorscheme wal
set background=dark
```

Finally, execute `wal --theme base16-nord`.

Something not working as expected? Feel free to open an issue!

## Integrating with vim-snippets

There is an interesting plugin called vim-snippets which adds some snippets for
popular languages [Vim-Snippets](https://github.com/honza/vim-snippets). However it is not as completed as the shown by the
development made by Gilles Castel. So for people who are interested on using
this and also the vim-snippets plugin there is a specific setup which only
enables using latex-snippets for Tex files.

You should add the following line in a tex.vim file located in the ftplugin
folder usually at `~/.vim/after/ftplugin`
```bash
let g:UltiSnipsSnippetDirectories=["custom-snippets"]
```

This only enables snippets from custom-snippets folder in runtimepath.

Then create the folder `custom-snippets` in the `~/.vim/after` location, and
add the `tex.snippets` file provided here.

If you haven't added the vim-snippets plugin only add the file in the `UltiSnips` folder as normal.

If you are interested in how I set this repository in conjunction with other
plugins for software development please check my repository at [Nvim-config](https://github.com/LuighiV/nvim-config).

