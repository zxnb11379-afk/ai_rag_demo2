# ai_rag_demo2
# 基于 Dify + 本地大模型的 RAG 知识库问答系统

## 📌 项目简介

本项目基于 **Dify 工作流 + 本地大模型（Ollama）** 构建，实现了一个企业招聘场景下的 **RAG（检索增强生成）知识库问答系统**。

系统支持：

* 📄 本地知识库构建（上传文本）
* 🔍 语义检索（Embedding）
* 🤖 大模型问答（LLM）
* 🔗 工作流编排（Workflow）
* 🧩 Prompt 可控输出

---

## 🚀 技术栈

* **Dify**（工作流 + RAG）
* **Ollama**（本地模型部署）
* **deepseek-r1:7b**（LLM）
* **Embedding 检索**
* **RAG（Retrieval-Augmented Generation）**

---

## 🧩 系统架构

```text
用户问题
   ↓
知识检索（Knowledge Retrieval）
   ↓
上下文拼接（Context Injection）
   ↓
大模型生成（LLM）
   ↓
返回答案
<img width="1640" height="361" alt="image" src="https://github.com/user-attachments/assets/6ac8163a-7997-442b-9369-e531ccb5097d" />

```

---

## 📂 知识库示例

```text
周勋是南京工业大学计算机专业2026届毕业生，掌握Python和Java，有Web开发项目经验。
周勋投递的是AI开发工程师岗位，对RAG和Agent有基本了解。
周勋毕业于南京工业大学。
周勋擅长Python开发，有AI项目经验。
周勋曾参与RAG系统开发。
```

---

## 示例问答

**输入：**

```text
周勋毕业于哪所大学？
```

**输出：**

```text
南京工业大学
```
<img width="942" height="346" alt="image" src="https://github.com/user-attachments/assets/0e9fa467-9c78-4f2d-b521-0e8bb9d2d525" />

---

## ⚙️ Prompt设计（核心）

```text
你是企业招聘知识库问答助手。

【参考资料】
{{知识检索.result[0].content}}

【用户问题】
{{sys.query}}

【要求】
1. 必须只使用参考资料中的信息回答
2. 回答必须能在参考资料中找到原文依据
3. 禁止使用已有知识或推理补充
4. 如果无法从参考资料中找到答案，必须回答：资料中没有相关信息

【回答要求】
- 直接给出答案
- 不要解释
- 不要补充

请回答：
```

---

## 项目亮点

* ✅ 完整实现 RAG 流程（检索 + 生成）
* ✅ 本地大模型部署（Ollama）
* ✅ 支持 Prompt 可控输出（避免幻觉）
* ✅ 掌握 Dify 工作流编排
* ✅ 能独立排查 AI 系统问题（变量、数据流、模型行为）

---

## ⚠️ 遇到的关键问题 & 解决方案

### 模型出现幻觉

**问题：**
模型编造不存在的信息（如错误大学）

**原因：**
使用推理模型（deepseek-r1）

**解决：**

* 或加强 Prompt 约束

---

### 知识库变量未生效

**问题：**

```text
{{知识检索.result[0].content}}
```

未被替换

**原因：**

* 手写变量
* 节点未连接

**解决：**
必须使用 **变量选择器插入**

---

### 取错字段

**错误：**

```text
{{knowledge.text}}
```

**正确：**

```text
{{知识检索.result[0].content}}
```

---

## 📈 项目优化方向

* 🔄 多轮对话（Agent）
* 🧠 工具调用（Function Calling）
* 📊 多文档检索（Top-K）
* 🎙️ 语音交互（ASR / TTS）
* 🏢 企业知识库系统

---

## 总结

> 本项目基于Dify实现了一个完整的RAG知识库问答系统，支持本地大模型部署。在开发过程中，我重点解决了模型幻觉、Prompt约束、变量绑定及数据流问题，提升了系统的稳定性与可控性。

---

## 📎 项目运行

1. 启动 Ollama
2. 配置 Dify 模型
3. 导入知识库
4. 运行工作流

---


