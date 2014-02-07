---
layout: post
title: "How to use Octopress Vim Plugin - vim-octopress"
date: 2014-02-07 15:04:38 +0800
comments: true
categories: octopress
---

octopress的vim插件本身比较轻量。主要是对Markdown格式的高亮和一些Octopress
常用rake命令的集成. 下面是安装vim-Octopress 的一些简单步骤.

``` bash 'Install vim-octopress' https://github.com/tangledhelix/vim-octopress
cd ~/.vim/bundle/
git clone https://github.com/tangledhelix/vim-octopress
```

下载之后，需要在.vimrc中加入
``` plain
autocmd BufNewFile,BufRead *.markdown,*.textile set filetype=octopress
```
