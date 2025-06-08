---
auther: DJLHB
pubDatetime: 2025-06-08T14:31:33Z
modDatetime: 2025-06-08T14:31:33Z
title: 包管理器：从nvm迁移到asdf
slug: Move-nvm-to-asdf
featured: false
draft: false
tags:
  - System Manager
description:
  包管理器：从nvm迁移到asdf
---

*最近闲来无事，就捣鼓起了原来配置好的ArchLinux；在使用nvm包管理器更新后，多个包管理器使用不便，想到之前看到一个可以管理多个开发环境的管理器，就想着来迁移一下。*

首先还是老老实实按照nvm官方文档将nvm给卸载了，因为用的是官方脚本安装。其实卸载起来步骤也不多：
```bash
export nvm_dir="${NVM_DIR:-~/.nvm}"

nvm unload

rm -rf "$nvm_dir"
```
编辑下`zshrc`，删掉这几行就算是卸载完成了：
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
[[ -r $NVM_DIR/bash_completion ]] && \. $NVM_DIR/bash_completion
```

asdf的安装也很简单，毕竟有[文档](https://asdf-vm.com/guide/getting-started.html)在手。。。
这次ArchLinux直接上AUR了：
```bash
yay -S asdf-vm
```
安装好了后还是需要一些配置的：
* 编辑`zshrc`，添加一下保存数据的文件夹位置：
```bash
export PATH="${ASDF_DATA_DIR:-$HOME/.asdf}/shims:$PATH"
```
* 设置命令行自动补全，这个直接使用`oh-my-zsh`的`asdf`插件了：
```bash
omz plugin enable asdf

omz reload
```
这样就算是初步安装完成了，参照官方文档，需要管理版本的话需要根据需要来添加插件。

添加`nodejs`插件：
```bash
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
```
安装最新的`nodejs`：
```bash
asdf install nodejs latest
```
使用安装好的版本：
```bash
# asdf set -u nodejs 16.5.0
asddf set -u nodejs latest
```

看一下效果：
```bash
$ node -v
v24.1.0

$ npm -v 
11.3.0
```

