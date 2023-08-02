---
title: 将chatGPT引入个人工作流的一种探索
date: 2023-06-05 17:24:30
comment: false
tags: VSCode插件
categories: 提效工具
---

### 将chatGPT引入个人工作流的一种探索

> 2023年上半年可能最热门的话题就是chatGPT，这个能融入实际工作中的自然语言工具，已经让很多大厂看到了它商用的价值，本文将提供一种可以辅助个人工作流的思路

---

#### 自研VSCode插件

- 其实核心的代码就是以下部分
![img](/images/DocumentGPT/code01.png)
- 主要原理就是将问题通过API发送至chatGPT并将回答打印到当前激活的文档编辑器中

#### 安装和使用

- 打开扩展并安装插件
![img](/images/DocumentGPT/20230605174311.png)

- 打开VSCode的设置菜单(右上角切换json显示)，修改配置项
```json
{
  "documentGPT.url": "https://api.aigcfun.com/api/v1/text", // API请求接口
  "documentGPT.key": "FCYLFSDJ47RHP9JG2N", // API请求Key
  "documentGPT.prompt": "我想让你充当前端开发专家。我将提供一些关于Js、Node等前端代码问题的具体信息，而你的工作就是想出为我解决问题的策略。", // 新增prompt模板可以自行修改
}

```

- 打开一个空的文档，鼠标右键可以看到整体的选项目录
![img](/images/DocumentGPT/20230802103408.png)

  - Document Start：

    - 如果当前文档无鼠标选中内容即打开一个对话框

      - 将你想问的问题输入到弹出框中
      ![img](/images/DocumentGPT/20230605174447.png)

      - 可以看到插件已经将chatGPT的回答写入当前文档
      ![img](/images/DocumentGPT/20230605174637.png)
    
    - 如果当前文档存在鼠标选中的内容则会将内容直接提交GPT

      *此时请耐心等待GPT返回结果*
  
  - Document Clear：

    - 清除当前会话所有内容，再进行GPT询问时即会开启新的会话

  - Document Custom：

    - 使用Prompt模板进行固定角色的GPT询问，此询问结果会更具有专业领域的价值

    - 需要自己将Prompt模板根据定制角色输入到setting中


*通过以上方法我们就可以通过VSCode很容易的完成和AI的智能交互*