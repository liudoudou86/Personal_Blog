---
title: 将chatGPT引入个人工作流的一种探索
date: 2023-06-05 17:24:30
comment: false
tags: VSCode插件
categories: 提效工具
---

### 背景介绍

> 2023 年上半年可能最热门的话题就是 chatGPT，这个能融入实际工作中的 NLP 工具，已经让很多大厂看到了它商用的价值，本文将提供一种可以辅助个人工作流的实际应用思路，以便拓展我们对 chatGPT 的应用范围和使用方法

---

### VSCode 插件

#### 核心的代码就是以下部分

![img](/images/DocumentGPT/code.png)

> _💡 主要原理就是将问题通过 API 发送至 chatGPT 并将回答打印到当前激活的文档编辑器中_

#### 安装和配置

- 打开扩展并安装插件

  ![img](/images/DocumentGPT/20230804135716.png)

- 配置插件参数分两种：

  - 第一种就是通过 Settings 的界面

    ![img](/images/DocumentGPT/20230804140337.png)

  - 第二种就是通过 Settings 的 json

  ```json
  {
    "documentGPT.url": "https://api.aigcfun.com/api/v1/text", // API请求接口
    "documentGPT.key": "FCYLFSDJ47RHP9JG2N", // API请求Key
    "documentGPT.prompt": "我想让你充当前端开发专家。我将提供一些关于Js、Node等前端代码问题的具体信息，而你的工作就是想出为我解决问题的策略。" // 新增prompt模板可以自行修改
  }
  ```

#### 插件使用

- 打开一份空白文档最好是.md 格式, 当然其他格式也支持:

![img](/images/DocumentGPT/20230802103408.png)

- Document Start 选项:

  - 第一种使用方式: 如果当前文档无鼠标选中内容则会打开一个输入框

    - 将你想问的问题输入到弹出框中

      ![img](/images/DocumentGPT/20230605174447.png)

    - _耐心等待 ing..._

    - 在我们等待 1 天之后, 可以看到插件已经将 chatGPT 的回答写入当前文档

      ![img](/images/DocumentGPT/20230605174637.png)

  - 第二种使用方式: 如果当前文档存在鼠标选中的内容则会将内容直接提交 GPT

    ![img](/images/DocumentGPT/20230804141324.png)

    - _⚠️ 此时请耐心等待 GPT 返回结果_

- Document Clear 选项:

  - 清除当前会话所有内容，再进行 GPT 询问时即会开启新的会话

- Document Custom 选项:

  - 为响应 chatGPT 的提示工程, 增加思维链提示(COT)入口

  - 使用 Prompt 模板进行固定角色的 GPT 询问，此询问结果会更具有专业领域的价值

    ![img](/images/DocumentGPT/20230804141751.png)

    - 可以看到通过和上图对比相同的问题, 此时 chatGPT 的回答更具有针对性(当前的提示为测试开发专家)

    - 当然我们要记得自己将 Prompt 模板根据定制角色输入到 Settings 中

#### 应用场景

- 日常问题都可以进行相关询问

- 修复 Bug 之后可以使用 chatGPT 进行代码分析并提供测试用例示例

- 日常开发工作对业务代码的代码实例输出

> _⚠️ 通过以上方法我们就可以通过 VSCode 很容易的完成和 AI 的智能交互_
