# DeepSeek Cookbook (中文版)

DeepSeek Cookbook 提供了旨在帮助开发者使用 DeepSeek 构建应用程序的代码和指南，提供了可轻松集成到您自己项目中的可复制代码片段。

本项目基于 [anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook)。

API 使用[Deeopth Anthropic 兼容 API](https://api.deepseek.com/anthropic)。

## 关于 DeepSeek API

DeepSeek 支持 OpenAI 和 Anthropic 协议。本文档使用 Anthropic 协议进行交互。

## 先决条件

要充分利用本 cookbook 中的示例，您需要一个 DeepSeek API 密钥。

虽然代码示例主要使用 Python 编写，但这些概念可以适应任何支持与 DeepSeek API 交互的编程语言。

如果您是第一次使用 DeepSeek API，我们建议从基础开始，以获得坚实的基础。

## 进一步探索

寻找更多资源来增强您使用 DeepSeek 和 AI 助手的体验？查看这些有用的链接：

- [DeepSeek 开发者文档](https://api-docs.deepseek.com/)

## 食谱目录

### 技能

- [分类](./skills/classification): 探索使用 DeepSeek 进行文本和数据分类的技术。
- [检索增强生成](./skills/retrieval_augmented_generation): 学习如何使用外部知识增强 DeepSeek 的响应。
- [摘要](./skills/summarization): 发现使用 DeepSeek 进行有效文本摘要的技术。

### 工具使用和集成

- [工具使用](./tool_use): 学习如何将 DeepSeek 与外部工具和函数集成以扩展其功能。
  - [客户服务代理](./tool_use/customer_service_agent.ipynb)
  - [计算器集成](./tool_use/calculator_tool.ipynb)
  - [SQL 查询](./misc/how_to_make_sql_queries.ipynb)

### 第三方集成

- [检索增强生成](./third_party): 使用外部数据源补充 DeepSeek 的知识。
  - [向量数据库 (Pinecone)](./third_party/Pinecone/rag_using_pinecone.ipynb)
  - [维基百科](./third_party/Wikipedia/wikipedia-search-cookbook.ipynb/)
  - [网页](./misc/read_web_pages_with_haiku.ipynb)
  - [网络搜索 (Brave)](./third_party/Brave/web_search_using_brave.ipynb)
- [使用 Voyage AI 创建嵌入](./third_party/VoyageAI/how_to_create_embeddings.md)

### 多模态功能

- [DeepSeek 视觉功能](./multimodal):
  - [图像入门](./multimodal/getting_started_with_vision.ipynb)
  - [视觉最佳实践](./multimodal/best_practices_for_vision.ipynb)
  - [解释图表和图形](./multimodal/reading_charts_graphs_powerpoints.ipynb)
  - [从表单中提取内容](./multimodal/how_to_transcribe_text.ipynb)
- [使用 DeepSeek 生成图像](./misc/illustrated_responses.ipynb): 将 DeepSeek 与 Stable Diffusion 结合使用进行图像生成。

### 高级技术

- [子代理](./multimodal/using_sub_agents.ipynb): 学习如何将 DeepSeek 作为子代理使用。
- [上传 PDF 到 DeepSeek](./misc/pdf_upload_summarization.ipynb): 解析并将 PDF 作为文本传递给 DeepSeek。
- [自动化评估](./misc/building_evals.ipynb): 使用 DeepSeek 自动化提示评估过程。
- [启用 JSON 模式](./misc/how_to_enable_json_mode.ipynb): 确保从 DeepSeek 获得一致的 JSON 输出。
- [创建内容过滤器](./misc/building_moderation_filter.ipynb): 使用 DeepSeek 为您的应用程序创建内容过滤器。
- [提示缓存](./misc/prompt_caching.ipynb): 学习使用 DeepSeek 进行高效提示缓存的技术。

## 使用 mcp 编辑 jupyter notebook

使用的是 [jbeno/cursor-notebook-mcp](https://github.com/jbeno/cursor-notebook-mcp) 工具。

- 安装 mcp 工具：`pip install cursor-notebook-mcp`
- 启动可流式传输的 HTTP 传输协议的 mcp 服务器：

  ```shell
  cursor-notebook-mcp --transport streamable-http --allow-root /path/to/your/notebooks --host 127.0.0.1 --port 8080
  ```

- 配置 AI IDE（如 Cursor、Trae）：

  ```json
  {
    "mcpServers": {
      "notebook_mcp": {
        "url": "http://127.0.0.1:8080/mcp"
      }
    }
  }
  ```
