i - insert mode

esc - command mode



:set number -> show line numbers

:set linebreak -> wrap words

:set now rap



:syntax on



fo will find the next o

3fo will find the 3rd occurrence of o

% - matching parenthesis

0 - beginning of the line

$ - end of the line

*- Next word under cursor

!#- previous word under cursor

gg - beginning of the file

G - end

5G - line 5

/<string> - search ... n and N for next and previous respectively

o or O - insert a line and go into insert mode

x - delete the current character

X - backspace

r<char> - change the current char without going to the insert mode

. - repeat the previous command

u - undo

Ctrl +R - redo

:w - save

:q - quit

:q! - quit without saving







NerdTree - https://github.com/preservim/nerdtree

:NERDTree

:NERDTreeClose

You can also map it to F2 by putting map <F2> :NERDTreeToggle<CR> in your .vimrc file.

t: Open the selected file in a new tab
i: Open the selected file in a horizontal split window
s: Open the selected file in a vertical split window
I: Toggle hidden files
m: Show the NERD Tree menu
R: Refresh the tree, useful if files change outside of Vim
?: Toggle NERD Tree's quick help







```
vim ~/.vimrc
autocmd vimenter * NERDTree
```



```
:tabnext
:tabn
```



in VIM-RC

```
map  <C-l> :tabn<CR>
map  <C-h> :tabp<CR>
map  <C-n> :tabnew<CR>
```

- Control+l moves to the next tab
- Control+h moves to the previous tab
- Control+n creates a new tab









The visual mode has three subtypes.

Press v to enter the visual mode.
Press V to enter visual line mode, where the text is selected by line.
Press Ctrl+v to enter visual block mode. In this mode, the text is selected by rectangle blocks.

Move the cursor to the end of the text you want to copy or cut. You can use a movement command or up, down, right, and left arrow keys.

Press y to copy, or d to cut the selection.

Move the cursor to the location where you want to paste the contents.

Press P to paste the contents before the cursor, or p to paste it after the cursor.







yy - Yank (copy) the current line, including the newline character.
3yy - Yank (copy) three lines, starting from the line where the cursor is positioned.
y$ - Yank (copy) everything from the cursor to the end of the line.
y^ - Yank (copy) everything from the cursor to the start of the line.
yw - Yank (copy) to the start of the next word.
yiw – Yank (copy) the current word.
y% - Yank (copy) to the matching character. By default supported pairs are (), {}, and []. Useful to copy text between matching brackets.