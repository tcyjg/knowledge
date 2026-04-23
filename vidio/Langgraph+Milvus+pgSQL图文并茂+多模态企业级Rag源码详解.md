# Langgraph+Milvus+pgSQL图文并茂+多模态企业级Rag源码详解

> BV号: BV1K1DxBLEfR | 生成时间: 2026/4/23 20:51:30

<iframe
  src="https://player.bilibili.com/player.html?bvid=BV1K1DxBLEfR&page=1"
  width="800"
  height="450"
  scrolling="no"
  border="0"
  frameborder="no"
  framespacing="0"
  allowfullscreen="true">
</iframe>

## 内容概览

本视频详细讲解了一个基于LangChain与LangGraph构建的企业级多模态RAG系统，重点实现图文并茂的检索与输出。作者指出当前主流RAG以文搜文为主，图文混合输出缺乏成熟方案，因此分享其自研架构：采用Milvus（字幕中误作'new vers'）存储与检索向量、PostgreSQL（字幕中误作'pg circle'）管理元数据；通过LangGraph编排多步骤有状态Agent工作流，利用state机制实现跨节点共享与更新变量（如query重写、对话历史追加）；创新性地将图片转为占位符嵌入文本切片，确保图文位置一致性，并支持向量+关键词（倒排索引/稀疏向量）混合检索。视频同步演示了知识库创建、文档切分（含图片处理）、检索路径追踪及最终图文精准返回效果。

## 分段解析

### [0:02] 项目背景

指出当前RAG多以文搜文为主，图文输出缺乏成熟落地案例，B站相关资源稀缺，因此分享自研的图文并茂+多模态知识库系统实现思路。

![项目背景](https://i.ibb.co/SC0tcGC/aaa8192dc8e3.jpg)

### [0:23] 技术栈介绍

系统基于LangChain和LangGraph框架，向量数据库使用Milvus（字幕称'new vers'），结构化数据存储于PostgreSQL（字幕称'pg circle'），二者分工明确。

![技术栈介绍](https://i.ibb.co/QjqS6TqV/b4f42c2cdbe1.jpg)

### [0:34] LangGraph核心

LangGraph是LangChain生态中专用于有状态、多步骤Agent编排的框架，核心思想是以代码形式定义节点（node）并连接成工作流图。

![LangGraph核心](https://i.ibb.co/XcHNQbb/c4aab8a33677.jpg)

### [1:29] State机制

State是LangGraph中定义全局共享变量的数据结构，各节点可读取并更新state字段，实现数据在工作流中的传递与状态维护。

![State机制](https://i.ibb.co/zWGV4gSS/7cec855c22b9.jpg)

### [3:28] 工作流构建

工作流在用户提问时动态构建：通过graph.py定义节点，用add_node/add_edge串联，支持条件路由（依据上一节点返回值跳转），最后编译成可执行图。

![工作流构建](https://i.ibb.co/hJzdZHFF/71d6d18f0871.jpg)

### [5:06] State初始化

构建图后需初始化state，将原始query及知识库配置参数注入，供后续节点（如query重写）读取使用，确保上下文连贯。

### [6:00] State更新逻辑

默认state更新为覆盖式，但对话历史等需追加场景，通过定义list类型字段+内置reduce函数（如AIMessage）实现消息自动追加而非覆盖。

![State更新逻辑](https://i.ibb.co/S7fDcF6H/0d3e6817f434.jpg)

### [8:45] 知识库创建

演示创建知识库过程：标题字段融入content一同向量化；支持V3/V4嵌入模型；配置向量维度、切片大小（800-1000）、重叠率（约10%）等参数。

### [10:53] 图文切片策略

创新性地将图片转换为占位符嵌入文本切片中，保证向量化与大模型输出时图文位置严格一致，避免图文错位或丢失。

![图文切片策略](https://i.ibb.co/0pZdqQMJ/de417b396222.jpg)

### [13:37] 混合检索设计

content与向量共同存入Milvus，除向量检索外，还构建稀疏向量与倒排索引，支持关键词全文检索，尤其适配长字符串（如错误代码）的精确匹配。

![混合检索设计](https://i.ibb.co/GQZ4N1Fw/cd9e21ec5463.jpg)

### [15:52] 检索路径演示

实际检索流程：query重写→单/多文档分类→混合检索策略判断→组装prompt（含切片+图片占位符）→大模型生成结果，全程可视化追踪。

### [16:40] 图文输出效果

在700+切片中精准定位目标内容，原样返回文字及两张女生图片，且图片位置与原文完全一致，验证图文并茂输出的核心能力。

![图文输出效果](https://i.ibb.co/gZTnBWS2/3f7c7227ed71.jpg)

### [17:13] 下期预告

预告下期主题为‘以图文搜图文’，即多模态知识库的完整实现原理与源码详解，涵盖更复杂的跨模态对齐与检索技术。

---
*由 B站视频速览工具自动生成*