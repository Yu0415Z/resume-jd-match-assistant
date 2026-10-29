# 简历 × JD 匹配助手

一个用于求职准备的轻量级 AI 应用：粘贴简历和岗位描述，查看匹配技能、可能的差距、简历优化建议与模拟面试问题。

## 功能

- 本地关键词初筛：无需 API Key，文本只在本地应用进程中处理。
- 大模型分析：支持 OpenAI SDK 兼容接口，可填写模型名与 Base URL。
- 结构化结果：匹配参考分、已体现技能、差距、建议、面试练习题。
- JSON 导出，便于保存与后续分析。
- 简体中文界面与隐私提示。

## 快速启动

需要 Python 3.10 或更新版本。

```bash
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate.ps1
# macOS / Linux: source .venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

浏览器打开 Streamlit 显示的本地地址。不开启“大模型分析”即可使用本地初筛。

## 配置模型

可以在应用侧边栏临时填写 Key，或复制 `.env.example` 为 `.env` 后填写：

```env
OPENAI_API_KEY=your_api_key
OPENAI_BASE_URL=
OPENAI_MODEL=gpt-4o-mini
```

`.env` 已列入 `.gitignore`，不要将真实密钥提交到 GitHub。若使用兼容服务，请按服务商文档设置 Base URL 和模型名。

## 项目结构

```text
app.py                 Streamlit 界面、关键词分析与模型调用
requirements.txt       Python 依赖
.env.example           环境变量模板（不含密钥）
.streamlit/config.toml  主题设置
```

## 技术方案

- Python + Streamlit：快速构建可交互的中文 Web 应用。
- OpenAI Python SDK：调用支持 Chat Completions 与 JSON 输出的模型服务。
- 提示词约束：要求模型仅依据用户材料分析，并返回固定 JSON 字段。
- 降级体验：无 API Key 时仍可本地关键词初筛。

## 当前限制与后续迭代

- 本地关键词覆盖有限，不能理解技能熟练度、项目上下文或同义表达。
- 模型分数是辅助参考，不是客观录用概率；模型可能遗漏或误判。
- 后续可添加 PDF/DOCX 解析、技能同义词映射、岗位要求权重、历史分析对比和人工评估集。

## 演示方式

1. 先用本地初筛演示“无 Key 也可用”的基本流程。
2. 再配置你自己的模型服务，展示结构化提示词与结果。
3. 面试讲解时说明隐私边界、输出校验、降级策略和当前局限。

## License

MIT
