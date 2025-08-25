# 使用 Promptfoo 进行评估

### 先决条件

要使用 Promptfoo，您需要在系统上安装 node.js 和 npm。更多信息请参考[此指南](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)  

您可以使用 npm 安装 promptfoo，或直接使用 npx 运行。在本指南中，我们将使用 npx。  

*注意：对于此示例，您无需运行 `npx promptfoo@latest init`，因为此目录中已有一个初始化的 `promptfooconfig.yaml` 文件*  

请参阅官方文档[此处](https://www.promptfoo.dev/docs/getting-started)  

### 入门指南

评估由 `promptfooconfig.yaml` 文件编排。在此文件中，我们定义以下部分：

- 提示词
  - Promptfoo 使您能够以多种不同格式导入提示词。您可以在此处阅读更多相关信息[链接](https://www.promptfoo.dev/docs/configuration/parameters)。
  - 在此示例中，我们将加载 3 个提示词 - 与 `guide.ipynb` 中使用的相同，来自 `prompts.py` 文件：
    - 这些函数与 `guide.ipynb` 中使用的相同，只是它们不调用 Anthropic API，而是只返回提示词。Promptfoo 然后处理调用 API 和存储结果的编排。
    - 您可以在此处阅读更多关于提示函数的信息[链接](https://www.promptfoo.dev/docs/configuration/parameters#prompt-functions)。使用 Python 使我们能够重用 VectorDB 类，这对于 RAG 是必要的，这在 `vectordb.py` 中定义。
- 提供商
  - 使用 Promptfoo，您可以连接到不同平台的许多不同 LLM，请参见[此处了解更多](https://www.promptfoo.dev/docs/providers)。在 `guide.ipynb` 中，我们使用了 Haiku，默认温度为 0.0。我们将使用 Promptfoo 来试验不同的温度设置数组，以确定我们用例的最佳选择。
  - 对于 DeepSeek，我们将配置 API 端点为：<https://api.deepseek.com/anthropic>
- 测试
  - 我们将使用与 `guide.ipynb` 中相同的数据，可以在[此 Google Sheet](https://docs.google.com/spreadsheets/d/1UwbrWCWsTFGVshyOfY2ywtf5BEt7pUcJEGYZDkfkufU/edit#gid=0)中找到。
  - Promptfoo 有许多内置测试，可以在[此处找到](https://www.promptfoo.dev/docs/configuration/expected-outputs/deterministic)。
  - 在此示例中，我们将在 `dataset.csv` 中定义一个测试，因为我们的评估条件随每一行而变化，并在 `promptfooconfig.yaml` 中定义一个测试，用于跨所有测试用例一致的条件。在此处阅读更多相关信息[链接](https://www.promptfoo.dev/docs/configuration/parameters/#import-from-csv)
- 转换
  - 在 `defaultTest` 部分中，我们定义了一个转换函数。这是一个 Python 函数，用于从 LLM 响应中提取我们想要测试的特定输出。
- 输出
  - 我们定义输出文件的路径。Promptfoo 可以以多种格式输出结果，[请参见此处](https://www.promptfoo.dev/docs/configuration/parameters/#output-file)。或者，您可以使用 Promptfoo 的 Web UI，[请参见此处](https://www.promptfoo.dev/docs/usage/web-ui)。

### 运行评估

要开始使用 Promptfoo，请打开终端并导航到此目录 (`./evaluation`)。

在运行评估之前，您必须定义以下环境变量：

`export DEEPSEEK_API_KEY=YOUR_API_KEY`  
`export VOYAGE_API_KEY=YOUR_API_KEY`

从 `evaluation` 目录中，运行以下命令。  

`npx promptfoo@latest eval`

如果您想增加请求的并发数（默认值 = 4），请运行以下命令。  

`npx promptfoo@latest eval -j 25`  

评估完成后，终端将打印数据集中的每一行结果。

现在您可以回到 `guide.ipynb` 来分析结果！
