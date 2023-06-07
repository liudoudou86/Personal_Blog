---
title: 将chatGPT引入个人工作流的一种探索
date: 2023-06-05 17:24:30
comment: false
tags: VSCode插件
categories: 提效工具
---

### 将chatGPT引入个人工作流的一种探索

> 2023年上半年可能最热门的话题就是chatGPT，这个能融入实际工作中的自然语言工具，已经让很多大厂看到了它商用的价值，本文将提供一种可以辅助个人工作流的方案

---

#### 自研VSCode插件

- 其实核心的代码就是以下内容
![img](/images/DocumentGPT/code01.png)
- 主要原理就是将问题通过API发送至chatGPT并将回答打印到当前激活的文档中

#### 安装和使用

- 打开扩展并安装插件
![img](/images/DocumentGPT/20230605174311.png)

- 打开VSCode的设置菜单(右上角切换json显示)，修改配置项
```
{    
  "documentGPT.url": "https://api.aigcfun.com/api/v1/text", // API地址
  "documentGPT.key": "FCC78BJGVUPVLP491P" // API请求的key
}

```

- 打开一个空的文档，鼠标右键可以看到一个选项: Start documentGPT
![img](/images/DocumentGPT/20230605174154.png)

- 将你想问的问题输入到弹出框中
![img](/images/DocumentGPT/20230605174447.png)

- 可以看到插件已经将chatGPT的回答写入当前文档
![img](/images/DocumentGPT/20230605174637.png)

*通过以上方法我们就可以通过VSCode很容易的完成和AI的智能交互*