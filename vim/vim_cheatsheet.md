<!-- TOC -->

- [Exiting](#exiting)
    - [:q Close file](#q-close-file)
    - [:qa Close all files](#qa-close-all-files)
    - [:w Save](#w-save)
    - [:wq / :x Save and close file](#wq--x-save-and-close-file)
    - [ZZ Save and quit](#zz-save-and-quit)
    - [ZQ Quit without checking changes](#zq-quit-without-checking-changes)
- [Existing insert mode](#existing-insert-mode)
    - [Esc \ <C - [> Exit insert mode](#esc-%5C-c----exit-insert-mode)
    - [<C - C> Exit insert mode, and abort current command](#c---c-exit-insert-mode-and-abort-current-command)
- [Clipboard](#clipboard)
    - [x Delete character](#x-delete-character)
    - [dd Delete lineCut](#dd-delete-linecut)
    - [yy Yank lineCopy](#yy-yank-linecopy)
    - [P Paste](#p-paste)
    - [p Paste before](#p-paste-before)
    - ["*p / "+p Paste from system clipboard](#p--p-paste-from-system-clipboard)
    - ["*y / "+y Paste to system clipboard](#y--y-paste-to-system-clipboard)
- [Find & Replace](#find--replace)
    - [:%s/foo/bar/g Replace foo with bar in whole document](#%25sfoobarg-replace-foo-with-bar-in-whole-document)
- [Navigating](#navigating)
    - [h j k l Arrow keys](#h-j-k-l-arrow-keys)
    - [<C-U> / <C-D> Half-page up/down](#c-u--c-d-half-page-updown)
    - [<C-B> / <C-F> Page up/down](#c-b--c-f-page-updown)
    - [Words](#words)
        - [b / w Previous/next word](#b--w-previousnext-word)
        - [ge / e Previous/next end of word](#ge--e-previousnext-end-of-word)
    - [Line](#line)
        - [0 Start of line](#0-start-of-line)
        - [^ Start of lineafter whitespace](#%5E-start-of-lineafter-whitespace)
        - [$ End of line](#-end-of-line)
    - [Character](#character)
        - [fc Go forward to character c](#fc-go-forward-to-character-c)
        - [Fc Go backward to character c](#fc-go-backward-to-character-c)
    - [Document](#document)
        - [gg First line](#gg-first-line)
        - [G Last line](#g-last-line)
        - [:{number} Go to line {number}](#number-go-to-line-number)
        - [{number}G Go to line {number}](#numberg-go-to-line-number)
        - [{number}j Go down {number} lines](#numberj-go-down-number-lines)
        - [{number}k Go up {number} lines](#numberk-go-up-number-lines)
    - [window](#window)
        - [zz Center this line](#zz-center-this-line)
        - [zt Top this line](#zt-top-this-line)
        - [zb Bottom this line](#zb-bottom-this-line)
        - [H move to top of screen](#h-move-to-top-of-screen)
        - [M move to middle of screen](#m-move-to-middle-of-screen)
        - [L move to bottom of screen](#l-move-to-bottom-of-screen)

<!-- /TOC -->
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