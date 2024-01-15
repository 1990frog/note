[toc]

# Exiting
## `:q` Close file
## `:qa` Close all files
## `:w` Save
## `:wq` / `:x` Save and close file
## `ZZ` Save and quit
## `ZQ` Quit without checking changes

# Existing insert mode
## `Esc` \ `<C - [>` Exit insert mode
## `<C - C>` Exit insert mode, and abort current command

# Clipboard
## `x` Delete character
## `dd` Delete line(Cut)
## `yy` Yank line(Copy)
## `P` Paste
粘贴剪贴板内容到光标下方
## `p` Paste before
粘贴剪贴板内容到光标上方
## `"*p` / `"+p` Paste from system clipboard
" 表示使用寄存器
"* 表示使用当前选择区 
替代方式：`ctrl+insert`复制，`shift+insert`粘贴
## `"*y` / `"+y` Paste to system clipboard

# Find & Replace
## `:%s/foo/bar/g` Replace foo with bar in whole document

# Navigating
## `h j k l` Arrow keys
## `<C-U>` / `<C-D>` Half-page up/down
## `<C-B>` / `<C-F>` Page up/down
## Words
### `b` / `w` Previous/next word
### `ge` / `e` Previous/next end of word 
## Line
### `0` Start of line
### `^` Start of line(after whitespace)
### `$` End of line
## Character
### `fc` Go forward to character c
### `Fc` Go backward to character c
## Document
### `gg` First line
### `G` Last line
### `:{number}` Go to line {number}
### `{number}G` Go to line {number}
### `{number}j` Go down {number} lines
### `{number}k` Go up {number} lines
## window
### `zz` Center this line
### `zt` Top this line
### `zb` Bottom this line
### `H` move to top of screen
### `M` move to middle of screen
### `L` move to bottom of screen
