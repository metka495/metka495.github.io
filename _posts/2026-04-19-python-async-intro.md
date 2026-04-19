---
layout: post
title:  "Python 异步编程入门"
date:   2026-04-19 10:30:00 +0800
categories: Python 异步编程 教程
tags: python asyncio async-await
---

## 什么是异步编程？

异步编程是一种编程范式，允许程序在等待某些操作（如网络请求、文件 I/O）完成时继续执行其他任务。这与传统的同步编程形成对比，同步编程在执行 I/O 操作时会阻塞整个程序。

## Python 中的异步编程

Python 3.5+ 引入了 `async` 和 `await` 关键字，使得异步编程变得更加直观。

### 基本语法

```python
import asyncio

async def fetch_data():
    print("开始获取数据...")
    await asyncio.sleep(2)  # 模拟耗时操作
    print("数据获取完成！")
    return {"data": "示例数据"}

async def main():
    result = await fetch_data()
    print(f"结果: {result}")

# 运行异步函数
asyncio.run(main())
```

### 并发执行多个任务

```python
import asyncio
import time

async def task(name, delay):
    print(f"任务 {name} 开始")
    await asyncio.sleep(delay)
    print(f"任务 {name} 完成")
    return f"{name} 的结果"

async def main():
    start_time = time.time()
    
    # 并发执行多个任务
    results = await asyncio.gather(
        task("A", 2),
        task("B", 1),
        task("C", 3)
    )
    
    end_time = time.time()
    print(f"所有任务完成: {results}")
    print(f"总耗时: {end_time - start_time:.2f} 秒")

asyncio.run(main())
```

### 使用 aiohttp 进行异步 HTTP 请求

```python
import aiohttp
import asyncio

async def fetch_url(session, url):
    async with session.get(url) as response:
        return await response.text()

async def main():
    urls = [
        "https://api.github.com",
        "https://api.github.com/users",
        "https://api.github.com/repos"
    ]
    
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        
        for i, result in enumerate(results):
            print(f"URL {i+1} 响应长度: {len(result)}")

asyncio.run(main())
```

## 异步编程的优势

1. **提高性能**：在 I/O 密集型任务中显著提高性能
2. **节省资源**：相比多线程，异步编程使用更少的系统资源
3. **更好的可扩展性**：适合处理大量并发连接

## 注意事项

- 异步编程并不适合所有场景，CPU 密集型任务可能更适合使用多进程
- 需要使用支持异步的库（如 aiohttp、asyncpg 等）
- 调试异步代码可能比同步代码更复杂

## 总结

Python 的异步编程为处理 I/O 密集型任务提供了强大的工具。通过合理使用 `async` 和 `await`，你可以构建高效、可扩展的应用程序。

开始在你的项目中尝试异步编程吧！
