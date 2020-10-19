---
title: 🚀Proxy Linux
date: 2019-08-09 21:50:38
tags:
---
与时俱进 🤫
<!-- more -->

## Terminal

### 使用 clash 二进制 (强烈推荐)
[下载地址](https://github.com/Dreamacro/clash/releases)

1. 下载解压后拷贝到 `/usr/local/bin` 

2. 对文件使用 `sudo chmod +x ./clash-xxx` 授予权限

3. 然后 `./clash-xxx` 使用，它会自动下载一个几M的文件 `Country.mmdb` ，**有的时候**下载可能比较慢, 耐心等待，提示下一串字符时说明下载完成. 也可以直接下载这个[Country.mmdb.txt](https://www.yuque.com/attachments/yuque/0/2020/txt/182729/1593505250098-72dd0aff-9453-47e8-9a2b-45615cf4542a.txt?_lake_card=%7B%22status%22%3A%22done%22%2C%22source%22%3A%22transfer%22%2C%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2020%2Ftxt%2F182729%2F1593505250098-72dd0aff-9453-47e8-9a2b-45615cf4542a.txt%22%2C%22name%22%3A%22Country.mmdb.txt%22%2C%22ext%22%3A%22txt%22%2C%22size%22%3A3820017%2C%22id%22%3A%22v3n3U%22%2C%22card%22%3A%22file%22%7D) 拷贝到`~/.config/clash` 文件夹

4. 最后可以在 `~/.config/clash` 文件夹中看到两个文件, 其中将 `config.yaml` 替换成自己的配置(一般你的服务商会提供，如果没有提供 clash 配置文件，参考下面的**补充3**进行转换), 然后再运行 `./clash-xxx` 即可

#### **补充**

1. [访问控制面板](http://clash.razord.top/)

2. 后台运行 `nohup clash-xxx`  这样即使关闭终端也会后台运行, gnome 用户可以使用 `Alt + F2` 直接输入 `clash`

3. 结合 [subconverter-规则转换器](https://github.com/tindy2013/subconverter) 使用

#### **错误问题**
有的时候你服务商提供的配置文件比较旧，这时候可以使用老版本的 clash，也可以参考**补充3**进行转换

[clash-linux-amd64-v0.20.0.gz](https://www.yuque.com/attachments/yuque/0/2020/gz/182729/1593505192756-8589dfbf-3777-45e3-92bc-3882ea4be2f2.gz?_lake_card=%7B%22status%22%3A%22done%22%2C%22source%22%3A%22transfer%22%2C%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2020%2Fgz%2F182729%2F1593505192756-8589dfbf-3777-45e3-92bc-3882ea4be2f2.gz%22%2C%22name%22%3A%22clash-linux-amd64-v0.20.0.gz%22%2C%22ext%22%3A%22gz%22%2C%22size%22%3A3608351%2C%22id%22%3A%22wEw7J%22%2C%22card%22%3A%22file%22%7D)


### 使用clash in docker
[clash in docker 使用教程(Linux)](https://www.cnblogs.com/CodeAndMoe/p/clash-in-docker-linux.html)


### 使用 [python-ssr](https://github.com/shadowsocksr-backup/shadowsocksr/tree/manyuser) 搭配 [ssr-helper](https://www.npmjs.com/package/ssr-helper) ( ssr 已废 )


## GUI
### 使用electron-ssr ( ssr 已废 )
看文档进行设置
原作者已经删除了仓库,现为备份
[electron-ssr](https://github.com/qingshuisiyuan/electron-ssr-backup)
[linux 使用ssr上网](https://baorongquan.github.io/2017/09/09/linux-ssr-use/)


## 让终端走代理的几种方法
原文网址: [让终端走代理的几种方法](https://blog.fazero.me/2015/09/15/%E8%AE%A9%E7%BB%88%E7%AB%AF%E8%B5%B0%E4%BB%A3%E7%90%86%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E6%B3%95/)


```bash
alias setproxy="export https_proxy=http://127.0.0.1:7890;export http_proxy=http://127.0.0.1:7890;export all_proxy=socks5://127.0.0.1:7891"

alias unsetproxy="unset https_proxy;unset http_proxy;unset all_proxy"
```