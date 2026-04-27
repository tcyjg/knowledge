# 3小时完整教程：LangGraph从入门到实战-基础&进阶

> BV号: BV1PaWgz1Eu6 | 分P: P1 | 生成时间: 2026/4/27 22:06:49

<iframe
  src="https://player.bilibili.com/player.html?bvid=BV1PaWgz1Eu6&page=1"
  width="800"
  height="450"
  scrolling="no"
  border="0"
  frameborder="no"
  framespacing="0"
  allowfullscreen="true">
</iframe>

## 视频内容概览

本视频是面向初学者的LangGraph系统性入门教程，前半部分聚焦于Python类型注解基础（TypeDict、Union、Optional、Any、Lambda）及其在LangGraph中的关键作用，强调类型安全与代码可维护性；后半部分深入讲解LangGraph核心架构元素——State（共享状态）、Node（执行单元）、Graph（工作流拓扑）、Edge（执行流向）、Conditional Edge（条件分支）、Start/End节点、Tool（外部能力）、Tool Node（工具调度节点）、StateGraph（图构建器）和Runnable（标准化组件），并以‘Hello World图’为首个实战案例，手把手演示如何定义状态结构、编写节点函数、构建单节点有向图、编译与调用流程，为后续AI智能体开发奠定坚实语法与概念基础。

## 视频内容分段

### [0:00] 课程导览与学习目标

介绍LangGraph作为构建高级对话式AI工作流的Python库，明确课程目标：帮助零基础学员掌握基于图的复杂对话系统设计、实现与管理能力，最终能构建健壮、可扩展的LLM应用。

![课程导览与学习目标](https://i.ibb.co/zTJFnYPH/fe5a6efc2b17.jpg)

### [0:26] 讲师介绍与学习前提

讲师Viva自我介绍为机器人与AI专业学生，说明课程预设学员了解LangChain但无LangGraph编码经验，因此内容详尽、节奏适中，支持倍速播放，并预告课程包含大量图构建、理论讲解及配套GitHub练习题。

### [1:23] 类型注解基础：TypeDict

从字典的灵活性与结构校验缺陷切入，引出TypeDict（通过类定义带类型约束的字典），强调其在LangGraph中用于明确定义State结构的关键作用，提升类型安全性、可读性与调试效率。

![类型注解基础：TypeDict](https://i.ibb.co/3mQrGMk4/d393472716b0.jpg)

### [4:23] 类型注解进阶：Union与Optional

讲解Union（联合类型）用于声明参数可接受多种类型之一（如int | float），保障运行时类型安全；Optional[T]等价于Union[T, None]，用于可选参数，二者均为LangGraph底层广泛采用的核心类型机制。

![类型注解进阶：Union与Optional](https://i.ibb.co/C3xMwzHY/2e8910da8bf3.jpg)

### [6:30] 类型注解补充：Any与Lambda

介绍Any表示任意类型（牺牲类型检查换取灵活性），Lambda作为匿名函数快捷语法，强调其在数据处理（如map）中的高效性，共同构成LangGraph类型系统的重要组成部分。

### [8:37] LangGraph核心元素概览

系统解析七大核心概念：State（应用记忆/共享上下文）、Node（执行特定任务的函数）、Graph（整体工作流结构）、Edge（节点间执行路径）、Conditional Edge（基于状态的分支逻辑）、Start/End节点（虚拟入口与出口），辅以白板、流水线、路线图、火车轨道等生活化类比。

![LangGraph核心元素概览](https://i.ibb.co/gFRxB9Zf/e1ca18b7e159.jpg)

### [13:58] 工具与组件抽象：Tool、Tool Node与StateGraph

区分Tool（外部功能函数，如API调用）、Tool Node（专用于运行Tool的节点）、StateGraph（图构建与编译核心类，类比建筑蓝图）；同时引入Runnable（标准化可执行单元，类比乐高积木）及五类消息（Human/AI/System/Tool/Function）。

![工具与组件抽象：Tool、Tool Node与StateGraph](https://i.ibb.co/1YLbp6z9/c187d5c08d1d.jpg)

### [18:39] 首个实战：Hello World图编码

开启代码实践，明确本节不构建AI Agent，而是聚焦LangGraph语法入门：导入dict、TypedDict、StateGraph；定义AgentState类继承TypedDict；创建greeting_node节点函数，接收并更新State，强调docstring对后续LLM理解函数语义的重要性。

![首个实战：Hello World图编码](https://i.ibb.co/yFRBNR1N/884f90d98709.jpg)

---
*由 B站视频速览工具自动生成*