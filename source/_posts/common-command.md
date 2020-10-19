---
title: 👌常用命令
date: 2020-10-18 22:04:59
tags:
---

Unix 常用命令
<!-- more -->

## 命令查询网络端口占用情况(转)
### netstat 命令

`netstat -an | grep 3306`
3306替换成需要grep的端口号

### lsof 命令

通过list open file命令可以查看到当前打开文件，在linux中所有事物都是以文件形式存在，包括网络连接及硬件设备。

`lsof -i:80`

`-i`参数表示网络链接，`:80`指明端口号，该命令会同时列出PID，方便kill

查看所有进程监听的端口

`sudo lsof -i -P | grep -i "listen"`

[原文来源](https://www.cnblogs.com/kaiye/archive/2013/05/25/3099393.html)

## FFmpeg 合并视频文件

如果你有这几个视频需要合并:

`1.flv`, `2.flv`, `3.flv`

你只需要建立一个文本文件(e.g.`ff.txt`)，在里面写入:

```bash
# 相对路径、绝对路径均可
file '/path/1.flv'
file '/path/2.flv'
file '/path/3.flv'
```

然后在 terminal 中运行:

```bash
ffmpeg -f concat -i /path/ff.txt -c copy output.mp4

# 参数说明:
# -i 设定输入文件
# -f 设定编码器，这里使用 concat 无损合并
# -c 流选择器，这里选择所有流
# output为所生成文件名，可以任意修改
# 最后可以选择任何可以封装的格式，不一定是 MP4
```

然后就会开始合并了

参考文档: [使用 ffmpeg 拼接 bilibili 客户端所下载的分段 flv 视频](https://blessing.studio/use-ffmpeg-to-concat-flv-videos-downloaded-by-bilibili-client/)


## FFmpeg 提取视频的音频

提取 MP4 音频为 MP3

```bash
ffmpeg -i sample.mp4 -q:a 0 -map a sample.mp3
```

`-ss` 选项指定开始时间戳，使用 `-t` 选项指定编码持续时间，例如从3分钟到5秒钟，持续45秒。

* 时间戳必须采用 `HH：MM：SS.xxx` 格式或以秒为单位。
* 如果你不指定 `-t` 选项，它将会结束。

```bash
ffmpeg -i sample.mp4 -ss 00:03:05 -t 00:00:45.0 -q:a 0 -map a sample.mp3
```


只提取音频流而不进行重新编码（提取格式不能为MP3，可以是aac和m4a），请执行以下操作：

```bash
ffmpeg -i input-video.avi -vn -acodec copy output-audio.aac
```

* `-vn` 没有视频。
* `-acodec copy` 说使用已经在那里相同的音频流。


参考网址
[如何使用ffmpeg从视频中提取音频？](https://cloud.tencent.com/developer/ask/94091/answer/165304)


## 批量重命名 - zsh 专属

例如:把 small 修改为 large

| image_0_small.png | image_1_small.png | image_2_small.png |
| :---: | :---: | :---: |
| image_0_large.png | image_1_large.png | image_2_large.png |


```bash
zmv 'image_(*)_small.png' 'image_$1_large.png'

# 注释
# 第一个参数'image_(*)_small.png'是待替换的文件名，其中(*)是通配规则
# 第二个参数'image_$1_large.png'是替换后的文件名
```

另外需要注意，zsh 并不是一启动就可以直接使用 zmv 命令，需要先执行：

`autoload -U zmv`

为了方便可以把这一行加载 zmv 的代码放到 `~/.zprofile` 中。

参考文档: [命令行下批量重命名文件的三种方法](https://www.jianshu.com/p/c6a838430124)

## axel 下载神器

```bash
axel -n 30 http://example.com/example.dmg

# 注释
# 30 表示线程数，如果电脑性能够强劲的话把30变大也行（别太大，否则cpu受不了，通常几十就行）
```

参考文档: ["王东旭"在" Mac 上有什么比较好用的下载文件?"上的回答](https://www.zhihu.com/question/19552868/answer/126459140)

## tee 保存输出流到文件

有时我们想要在屏幕上执行 command 输出信息

又想保留下输出的信息到指定的文件中

```bash
# 将eg1的cat输出保存到eg2.txt
cat eg1.txt | tee eg2.txt

# 将ls -alt的输出保存到ls.txt
ls -alt | tee ls.txt

#追加到指定文件中,tee的默认模式为覆盖
tee -a

#忽略中断信息
tee -i
```

参考文档: [Linux 既输出到屏幕又保存到文件](https://blog.csdn.net/andy572633/article/details/8081591)

## 解压文件

- 解压 tar.gz 文件

`tar -zxvf filename.tar.gz`

- 解压 tar.bz2 文件

`tar -jxvf filename.tar.bz2`

- 解压 tar.xz 文件

`tar -xvf  filename.tar.xz` 


