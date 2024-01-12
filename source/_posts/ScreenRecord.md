---
title: 录制屏幕的浏览器工具
date: 2024-01-12 15:34:25
comment: false
tags: Chrome插件
categories: 提效工具
---

### 背景介绍

> 本人小小 Tester 由于工作原因经常需要录制操作视频提交 Bug，各种录制工具都尝试过~ 不是收费就是太难用，忍无可忍当无须再忍。So 自己动手撸了一个浏览器的录制视频工具

---

### 技术栈

- 当前版本使用 chrome 提供的 WebRTC 技术
- 备选方案使用 rrweb + canvas(目前调研中……)

#### 核心的代码就是以下部分

![img](/images/ScreenRecord/code.png)

> _💡 主要原理就是通过 Chrome 提供的接口进行视频流录制，后期可将视频流通过转换格式上传至 OSS_

#### 安装和配置

- 浏览器需要打开开发者模式, 然后加载插件文件夹就可以了

  ![img](/images/ScreenRecord/20240112155257.png)

- 可配置 OSS 的地址实现云存储，当前插件匹配的是 MinIO

  ![img](/images/ScreenRecord/20240112161300.png)

#### 插件使用

- 首先，打开摄像头权限并且配置存储方式

  ![img](/images/ScreenRecord/20240112161417.png)

  - 如果选择本地存储，当录制结束之后，点击【导出】按钮，自动下载至本地

  - 如果选择云端存储，当录制结束之后，点击【导出】按钮，自动生成 URL 可在线观看录制的视频

- 其次，选中需要录制的位置，可选范围为：某一个窗口、整个 windows

  ![img](/images/ScreenRecord/20240112161417.png)

- 以下为完整操作视频

  ![img](/images/ScreenRecord/20240112164852.gif)

#### 注意事项

> _⚠️ Chrome 提供的 WebRTC 录制接口只支持 https 的，如果是 http 协议暂时无法启动录制_
