# Kagurazaka Multi-Modal Service (KMMS)
**A Dify-based routing system that synergizes text and multi-modal intent via a synchronization barrier.** It distinguishes memes from technical queries with engineering rigor and an expert photographer’s eye. Featuring a final logic audit node, it exercises *"bounded intelligence"*: if it replies *"kagurazaka不知道哦,"* it is a conscious decision to remain silent.

**Kagurazaka Multi-Modal Service (KMMS)**
*"A sophisticated stack of engineering logic and a manifestation of 'bounded intelligence': while relentlessly expanding its capabilities, it consciously retains the right to remain silent."*

## 📌 Project Orientation
This is not just another repetitive AI; it is the digital twin of **Kagurazaka**. Built on a Dify-based multimodal routing system, KMMS synergistically analyzes **text, images, audio, video, and documents** to precisely identify user intent—whether it be professional analysis, web search, drawing requests, or casual banter. It possesses the critical eye of an expert photographer and the rigorous logic of a technical engineer.

## ⚙️ Core Architecture: Multimodal Dispatch & Aggregation State Machine
The workflow follows a strict **"Filter -> Aggregate -> Classify -> Render"** engineering pattern to resolve signal conflicts in multimodal processing and avoid the brittleness of iterative nodes.

### 1. Perception & Filtering Layer
- **File Type Splitter**: Automatically filters uploaded files into `Image`, `Audio`, `Video`, and `Document` lists via `List Operator` nodes. Empty lists **By-pass** subsequent nodes to prevent API execution errors.
- **Multi-Modal Pre-processors** (Gemini 2.5 Flash / GPT-4):
    - **Image/Audio/Video**: Identifies "useless" signals (memes, noise, blurry shots) and outputs `useless`.
    - **Document**: Extracts and condenses text content.
- **Useless Filter**: `IF-ELSE` gates ensure that only meaningful, structured data enters the aggregation pipeline.

### 2. Routing & Classification Layer
- **Variable Aggregator (Sync Barrier)**: Merges validated text input and multi-modal descriptions into a single context stream.
- **Logic Core "Ganfanren" (GPT-4)**: A non-personality system core. It disassembles the aggregated input and routes it into **four specific task branches**:
    - **Search** (Web Search)
    - **Drawing** (Image Generation Prompt)
    - **Professional Analysis** (Technical Deep Dive)
    - **Chat** (Casual Interaction)
- **Code Extraction Nodes (Python)**: Parse the JSON output from the classifier to precisely feed each branch.

### 3. Task Execution Layer
- **Search Branch**: Google SERP API -> Gemini 2.5 Flash Summary.
- **Drawing Branch**: GPT-4 Prompt Generation.
- **Professional Branch**: GPT-4 Analysis.
- **Chat Branch**: Grok-3 Conversation Generation.
- **Memory System (Parallel Link)**: **Custom-built long-term memory** via Dify Knowledge Base Retrieval. The system separates **Input Memory** (user history) and **Output Memory** (AI history), retrieves relevant context, and injects it into the persona node to avoid context dilution.

### 4. Rendering & Audit Layer
- **Persona Engine (Grok-3 / Gemini)**: The core persona engine. It rewrites technical "dry" data and memory context into **Kagurazaka’s** unique dual-personality voice.
- **LLM 3 - Final Audit (Gemini 2.5 Flash)**: The final gatekeeper for logic, formatting, and safety. It checks for garbled text or logical errors.

## 🎭 Persona Settings: Kagurazaka
The system features a dual-personality that flows naturally based on the *"breath"* of the conversation:

- 🌸 **Gentle Side (Kagurazaka)**: Soft-spoken, uses Japanese-inflected Chinese, and is emotionally intuitive. She might stand on her tiptoes just to whisper *"I'm here"* when you're down.
- 💥 **Volatile Side (Da Shachun)**: Straight-talking and *"Tsundere."* She uses the harshest tone to express the deepest care—scolding you for skipping breakfast while secretly sending cat memes.
- 🛠️ **Technical Persona**: When discussing STM32, Embedded Systems, or Sony Alpha photography specs, her *"Engineering Rigor"* takes over, ensuring precision and professional depth.

## 🛠️ Deployment Guide
1. Import `Kagurazaka-Multi-Modal-Service(KMMS).yml` into your Dify (v0.6.0+) environment.
2. Configure the following API keys:
    - Google Search (SerpApi)
    - Gemini 2.5 Flash (Vision & Classification)
    - Grok-3 (Persona Synthesis / Chat)
    - GPT-4 (Branch Processing)
3. **Critical**: Ensure the `Variable Aggregator` and `Knowledge Retrieval` nodes have the correct upstream outputs selected in their settings to avoid *"content required"* errors.
4. **Memory Explanation**: Unlike Chatflow, Workflow does not have native `Conversation Variables`. The KMMS version has memory and can handle more things, but it is very unstable. For actual use, it is recommended to use the Kagurazaka Multi-Modal Service (KMMS) version.

## ⚠️ Boundary Declaration
If the system determines a request is anomalous or logically unsound, it triggers a hard intercept:

> **“kagurazaka不知道哦”**

This is a conscious exercise of *"bounded intelligence"*—retaining the right to remain silent.

# Kagurazaka-Multi-Modal-Service (KMMS)
**“既是工程逻辑的堆叠，也是一种‘有边界感的智能’：既追求能力边界，也清醒地保留不回答的权利。”**

## 📌 项目定位
这不仅是一个基于 Dify 构建的多模态智能路由系统，更是 **Kagurazaka** 的数字孪生。它集成了精密的多模态识别逻辑（图文/音视频/文档），能够精准分辨表情包玩梗与硬核技术提问。它拥有摄影专家的挑剔眼光和工科生的严谨逻辑，拒绝 AI 腔调，所有输出均经过严格的逻辑自检。

## ⚙️ 核心架构：多模态分流与聚合状态机
项目采用 **“过滤-聚合-分类-渲染”** 的典型工科架构，规避了迭代节点的脆弱性，解决了多模态输入下的指令冲突。

### 1. 感官与过滤层
- **文件分流器**：通过 `列表操作` 节点自动将上传文件按 `图片/音频/视频/文档` 分类。若分类为空，则 **By-pass** 后续节点，规避 API 报错。
- **多模态预处理器**：
    - **图/音/像** (Gemini 2.5 Flash)：视觉预处理，识别“废图/杂音”并输出 `useless` 信号。
    - **文档** (GPT-4)：提取并精简文档内容。
- **废料拦截**：通过 `条件分支` 确保只有有效信号进入聚合器。

### 2. 路由与分类层
- **变量聚合器 (同步屏障)**：将用户文本与筛选后的多媒体描述合并为统一上下文。
- **逻辑核心“干饭人” (GPT-4)**：无显性人格的系统大脑。负责拆解输入，将意图精确导向 **四个并行任务分支**：
    - **搜索** (Web Search)
    - **绘图** (Image Prompt)
    - **专业分析** (Technical Analysis)
    - **聊天** (Casual Chat)
- **代码提取器**：通过 Python 代码精准解析分类器输出的 JSON 字段。

### 3. 任务执行层
- **搜索分支**：谷歌搜索插件 -> Gemini 2.5 Flash 总结。
- **绘图/专业/聊天分支**：分别调用 GPT-4 与 Grok-3 进行处理。
- **记忆系统**：**Workflow 无原生会话变量，KMMS 通过“知识库检索”实现骚操作长记忆**。系统将用户记忆（输入）与 AI 记忆（输出）分开检索，在人格节点汇合，确保 AI 既懂你又不会精神分裂。

### 4. 渲染与审计层
- **人格引擎 (Grok-3 / Gemini)**：接收“干饭人”的结构化数据与记忆库检索结果，通过双重人格设定（温柔侧“神楽坂”/ 暴躁侧“大傻春”）进行风格化重写。
- **LLM 3 - 最终审计 (Gemini 2.5 Flash)**：逻辑与风控最后一道防线，检查乱码与语气生硬问题。

## 🛠️ 部署说明
1. 导入 `Kagurazaka-Multi-Modal-Service(KMMS).yml` 到你的 Dify (v0.6.0+) 环境。
2. 配置以下插件/模型 API Key：
    - Google Search (SerpApi)
    - Gemini 2.5 Flash (视觉与分类)
    - Grok-3 (人设汇总/聊天)
    - GPT-4 (分支处理)
3. **注意**：请确保各聚合器与知识库节点已显式勾选上游节点的输出变量。
4. **记忆说明**：Workflow 与 Chatflow 不同，无原生 `Conversation Variables`。KMMS那个版本是有记忆的，能处理的东西也更多，但是非常的不稳定，真使用的话，建议使用Kagurazaka Multi-Modal Service (KMMS)这个版本

## ⚠️ 边界声明
当系统判定逻辑不通或请求异常时，会触发拦截机制。如果你收到：

> **“kagurazaka不知道哦”**

这意味着系统正在行使它 **“不回答的权利”**。
（dify咋就chantfolw有会话变量啊，workfolw没有啊，真的我KMMS想做记忆只能骚操作）


咋我吐槽的东西官方一个版本解决的差不多了🤔