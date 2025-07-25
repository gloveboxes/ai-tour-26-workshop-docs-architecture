# 实验室 1：研讨会入门

这是一个示例实验室，展示了内容作者如何使用 MkDocs 粘性选项卡创建多语言研讨会内容。

## 您将学到什么

在本实验室中，您将：

- 为研讨会设置您的开发环境

- 连接到示例数据库并验证数据访问

- 创建您的第一个 AI 驱动的应用程序

- 了解模型上下文协议 (MCP) 的基本架构

- 使用简单的查询和响应测试您的设置

## 介绍

模型上下文协议 (MCP) 是一个标准化接口，它将大型语言模型 (LLMs) 连接到外部工具和数据源（例如数据库和 API），从而实现更智能、更可扩展的 AI 应用程序。

在本入门实验室中，您将：

- 为 Python 或 C# 开发配置您的开发环境

- 使用 MCP 连接到 Zava DIY 零售数据库

- 创建一个可以查询销售数据的基本代理

- 验证您的设置是否正常工作，然后再转向高级主题

## 实验室练习

在本实验室中，您将设置第一个支持 MCP 的应用程序并将其连接到示例数据库。

=== "Python"

    ### 步骤 1：配置您的 Python 环境

    1. 在您的工作区中打开 `src/python/workshop` 文件夹。

    2. 创建一个名为 `my_first_agent.py` 的新文件：

        ```python
        import asyncio
        from mcp_client import MCPClient
        
        async def main():
            """创建您的第一个支持 MCP 的代理。"""
            client = MCPClient()
            
            # 连接到 MCP 服务器
            await client.connect("localhost:8000")
            
            # 测试基本连接
            response = await client.query("SELECT COUNT(*) FROM products")
            print(f"产品总数：{response}")
        
        if __name__ == "__main__":
            asyncio.run(main())
        ```
