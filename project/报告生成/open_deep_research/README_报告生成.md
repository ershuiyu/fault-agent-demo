# 报告生成项目

本目录包含设备智能故障诊断 Demo 使用的报告生成子项目，基于 LangGraph 和 Open Deep Research 改造，当前默认使用 OpenAI 兼容接口调用 DeepSeek。

## 目录说明

- `src/open_deep_research/`：LangGraph 主图、研究子图、提示词和状态定义
- `langgraph.local.json`：本地 LangGraph 运行配置
- `.env.example`：环境变量模板，不包含任何密钥
- `examples/`：示例研究任务
- `tests/`：原项目测试与评估脚本

## 当前流程

用户输入 → 需求澄清 → 研究任务整理 → 研究负责人分配子任务 → 资料压缩 → 最终报告生成。

设备诊断 Demo 接入时，应将设备台账、算法结果、规则结论和知识库检索结果整理为结构化证据，再传给最终报告生成节点。

## 配置与运行

1. 复制 `.env.example` 为 `.env`。
2. 填写模型接口密钥；密钥只保存在本地或服务器 `.env` 中，不要提交到 Git。
3. 根据实际接口设置 `OPENAI_BASE_URL`，并在 LangGraph Studio 的 Assistant 配置中选择模型。
4. 安装 `pyproject.toml` 中的依赖后，运行：

   ```bash
   langgraph dev --host 127.0.0.1 --port 2024 --config langgraph.local.json
   ```

本目录不包含服务器虚拟环境、运行缓存、日志、API 密钥和用户数据。
