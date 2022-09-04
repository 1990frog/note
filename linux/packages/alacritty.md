[TOC]

# 安装
## arch
```
> pacman -S alacrityy
```
## 离线安装
```
> git clone https://github.com/jwilm/alacritty.git
> cd alacritty
> cargo build --release

> cp target/release/alacritty /usr/local/bin
> cp Alacritty.desktop ~/.local/share/applications
```

# 配置
alacritty不会自动创建配置文件，可自行创建：
+ $XDG_CONFIG_HOME/alacritty/alacritty.yml
+ $XDG_CONFIG_HOME/alacritty.yml
+ $HOME/.config/alacritty/alacritty.yml
+ $HOME/.alacritty.yml

[default](https://github.com/alacritty/alacritty/blob/master/alacritty.yml)
[install](https://github.com/alacritty/alacritty/blob/master/INSTALL.md#linux--windows)

/* Terminal colors (16 first used in escape sequence) */
static const char *colorname[] = {

  /* 8 normal colors */
  [0] = '0x123e7c', /* black   */
  [1] = '0xff0000', /* red     */
  [2] = '0xd300c4', /* green   */
  [3] = '0xf57800', /* yellow  */
  [4] = '0x123e7c', /* blue    */
  [5] = '0x711c91', /* magenta */
  [6] = '0x0abdc6', /* cyan    */
  [7] = '0xd7d7d5', /* white   */

  /* 8 bright colors */
  [8]  = '0x1c61c2', /* black   */
  [9]  = '0xff0000', /* red     */
  [10] = '0xd300c4', /* green   */
  [11] = '0xf57800', /* yellow  */
  [12] = '0x00ff00', /* blue    */
  [13] = '0x711c91', /* magenta */
  [14] = '0x0abdc6', /* cyan    */
  [15] = '0xd7d7d5', /* white   */

  /* special colors */
  [256] = "#282a36", /* background */
  [257] = "#f8f8f2", /* foreground */
};


    black:   '0x123e7c'
    red:     '0xff0000'
    green:   '0xd300c4'
    yellow:  '0xf57800'
    blue:    '0x123e7c'
    magenta: '0x711c91'
    cyan:    '0x0abdc6'
    white:   '0xd7d7d5'

  # Bright colors
  bright:
    black:   '0x1c61c2'
    red:     '0xff0000'
    green:   '0xd300c4'
    yellow:  '0xf57800'
    blue:    '0x00ff00'
    magenta: '0x711c91'
    cyan:    '0x0abdc6'
    white:   '0xd7d7d5'

  # dim colors
  dim:
    black:   '0x1c61c2'
    red:     '0xff0000'
    green:   '0xd300c4'
    yellow:  '0xf57800'
    blue:    '0x123e7c'
    magenta: '0x711c91'
    cyan:    '0x0abdc6'
    white:   '0xd7d7d5'
