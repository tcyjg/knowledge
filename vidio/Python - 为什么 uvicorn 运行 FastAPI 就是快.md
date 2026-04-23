# Python - 为什么 uvicorn 运行 FastAPI 就是快

> BV号: BV1Sj7xzEEmr | 生成时间: 2026/4/23 20:15:08

<iframe
  src="https://player.bilibili.com/player.html?bvid=BV1Sj7xzEEmr&page=1"
  width="800"
  height="450"
  scrolling="no"
  border="0"
  frameborder="no"
  framespacing="0"
  allowfullscreen="true">
</iframe>

## 内容概览

本视频深入解析了Uvicorn作为FastAPI默认ASGI服务器的核心原理与优势。主讲人从Uvicorn的定位（轻量级异步Web服务器）切入，系统阐释ASGI标准的含义——即异步服务器网关接口，强调其非阻塞、高并发、资源高效的特点。视频对比了传统线程模型与ASGI异步模型在处理请求时的性能差异，并通过代码执行流程（如app变量加载、异步事件循环驻留、lifespan生命周期管理）揭示Uvicorn如何维持服务长运行、响应HTTP请求及优雅启停。最后说明Uvicorn与FastAPI的兼容性本质及典型启动命令，帮助开发者理解高性能Python Web服务的底层协作机制。

## 分段解析

### [0:00] 引入Uvicorn

视频开篇介绍Uvicorn是FastAPI项目中常用的Web服务器，用于启动和运行FastAPI应用，引出对其原理和优势的探讨。

![引入Uvicorn](https://i.ibb.co/qLqZPCxT/f2538e095f5b.jpg)

### [0:41] ASGI定义

解释ASGI全称为Asynchronous Server Gateway Interface，是一种标准化接口，使服务器能支持异步请求处理，具备非阻塞、网络控制与流量管理能力。

![ASGI定义](https://i.ibb.co/kg6ZPCwR/2afdbf6a548c.jpg)

### [2:18] Uvicorn角色

明确Uvicorn是一个ASGI兼容的应用服务器，负责承载FastAPI实例；FastAPI本身也遵循ASGI规范，二者天然适配，构成高性能组合。

![Uvicorn角色](https://i.ibb.co/JjqDNyxX/8ee2a4f23651.jpg)

### [3:30] 异步优势

对比同步多线程模型，指出ASGI通过单线程异步事件循环处理大量并发请求，显著降低资源消耗，提升吞吐量与响应效率。

![异步优势](https://i.ibb.co/PZKKkD69/fadc5a0d703d.jpg)

### [4:26] 启动命令

演示典型Uvicorn启动方式：'uvicorn main:app'，说明'main'为Python模块名，'app'为FastAPI实例变量，支持--reload、--port等参数配置。

![启动命令](https://i.ibb.co/cXrN8Jxn/99974c01b223.jpg)

### [5:40] 长运行机制

剖析为何Python脚本执行完未退出：Uvicorn内部启动异步事件循环并维持死循环（如while True或asyncio.run_forever），使进程持续监听请求。

![长运行机制](https://i.ibb.co/LdpvmWfY/a868ae9f6e04.jpg)

### [9:24] Lifespan详解

讲解lifespan异步上下文管理器的作用：在应用启动时执行初始化（如数据库连接），停机时执行清理（如关闭连接），实现资源全生命周期管控。

![Lifespan详解](https://i.ibb.co/nskQCrXW/b28f45b592af.jpg)

### [11:42] 总结价值

归纳Uvicorn+FastAPI组合的核心价值：基于ASGI标准实现高性能、低开销、易扩展的异步Web服务，兼顾开发体验与生产效能。

---
*由 B站视频速览工具自动生成并推送*