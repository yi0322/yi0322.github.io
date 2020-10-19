---
title: 💿常用镜像
date: 2019-08-16 20:19:42
tags:
---
一些个人常用的国内镜像
Python | Node.js | Homebrew | Ruby | Atom
<!-- more -->

## Python
### 临时使用
```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```
注意，`simple` 不能少, 是 `https` 而不是 `http`


### 设为默认
升级 pip 到最新的版本 (>=10.0.0) 后进行配置：
```
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
如果您到 pip 默认源的网络连接较差，临时使用本镜像站来升级 pip：
```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
```

## npm


### [推荐方法](https://www.yuque.com/u66058/blog/uciz55): 使用 nrm 管理 registry 地址


1. 下载nrm



```bash
npm install -g nrm --registry=https://registry.npm.taobao.org
```


2. 添加registry地址



```bash
nrm add npm http://registry.npmjs.org
nrm add taobao http://registry.npm.taobao.org
```


3. 切换npm registry地址



```bash
nrm use taobao
nrm use npm
```


### [cnpm](https://npm.taobao.org/)


```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
```


或者自定义一个 alias
```bash
echo '\n#alias for cnpm\nalias cnpm="npm --registry=https://registry.npm.taobao.org \
--cache=$HOME/.npm/.cache/cnpm \
--disturl=https://npm.taobao.org/dist \
--userconfig=$HOME/.cnpmrc"' >> ~/.zshrc && source ~/.zshrc
```

## Homebrew


### [Homebrew 源代码仓库 (brew upate)](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)


替换镜像：


```bash
git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git

brew update
```


重置为官方地址：


```bash
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git

git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git

git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git

brew update
```


### [Homebrew 预编译二进制软件包](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew-bottles/)


zsh 用户：


```bash
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc
```


## Ruby


### [RVM](https://ruby-china.org/wiki/rvm-guide)


`echo "ruby_url=https://cache.ruby-china.com/pub/ruby" > ~/.rvm/user/db`


### [RubyGems](https://gems.ruby-china.com/)


```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
gem sources -l
https://gems.ruby-china.com
# 确保只有 gems.ruby-china.com
```


### [使用 Gemfile 和 Bundler](https://gems.ruby-china.com/)


`bundle config mirror.https://rubygems.org https://gems.ruby-china.com`


这样你不用改你的 Gemfile 的 source。


## Atom

### Liunx


```bash
#进入目录
cd /home/你的用户名/.atom

#创建文件并编辑
vim .apmrc

#添加国内源
registry=https://registry.npm.taobao.org

#保存退出

#测试是否成功
apm install --check
```


### Windows


```bash
#进入目录
找到C:\Users\用户名\.atom目录

#创建名为 .apmrc 的文件并编辑
type nul>.apmrc

#添加国内源
registry=https://registry.npm.taobao.org
strict-ssl=false

#保存退出

#测试是否成功
apm install --check
```


