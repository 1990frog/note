<!-- TOC -->

- [安装](#%E5%AE%89%E8%A3%85)
- [生成默认配置](#%E7%94%9F%E6%88%90%E9%BB%98%E8%AE%A4%E9%85%8D%E7%BD%AE)
- [浏览图片](#%E6%B5%8F%E8%A7%88%E5%9B%BE%E7%89%87)

<!-- /TOC -->

# 安装
```
> sudo pacman -S ranger
```

# 生成默认配置
```
> ranger --copy-config=all
```

# 浏览图片
```
> sudo pacman -S ueberzug
> vim rc.conf

set preview_images true
set preview_images_method ueberzug
```
