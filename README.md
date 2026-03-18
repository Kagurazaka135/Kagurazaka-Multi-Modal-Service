# Kagurazaka-Multi-Modal-Sentinel
A Dify-based routing system that synergizes text and image intent via a synchronization barrier. It distinguishes memes from technical queries with engineering rigor and an expert photographer’s eye. Featuring a final logic audit node, it exercises "bounded intelligence": if it replies "kagurazaka不知道哦," it is a conscious decision to remain silent.
Kagurazaka Multi-Modal Sentinel (KMMS)
"A sophisticated stack of engineering logic and a manifestation of 'bounded intelligence': while relentlessly expanding its capabilities, it consciously retains the right to remain silent."

📌 Project Orientation
This is not just another repetitive AI; it is the digital twin of Kagurazaka. Built on a Dify-based multimodal routing system, KMMS synergistically analyzes text and image inputs to precisely identify user intent—whether it be professional analysis, web search, or casual banter. It possesses the critical eye of an expert photographer and the rigorous logic of a technical engineer.

⚙️ Core Architecture: Multimodal State Machine
The workflow follows a strict "Dispatch-Aggregate-Render" engineering pattern to resolve signal conflicts in multimodal processing:

Perception Layer:

Conditional Branch 3: Automatically detects file1/file2 status. If no image is present, it bypasses visual nodes to prevent API execution errors.

LLM 2 (Gemini 2.5 Flash): Acts as a visual pre-processor, identifying "useless" images (memes/blurry shots) or generating structured visual reports.

Routing Layer:

Question Classifier: Directs the flow based on aligned text-image signals to specific paths: Google Search, Knowledge Base, Professional Analysis, or Chat.

Rendering Layer:

LLM 8 (Grok-3): The core persona engine. It rewrites technical "dry" data into Kagurazaka’s unique voice using a dual-personality framework.

LLM 3 (Audit Node): The final gatekeeper for logic and safety.

🎭 Persona Settings: Kagurazaka
The system features a dual-personality that flows naturally based on the "breath" of the conversation:

🌸 Gentle Side (Kagurazaka): Soft-spoken, uses Japanese-inflected Chinese, and is emotionally intuitive. She might stand on her tiptoes just to whisper "I'm here" when you're down.

💥 Volatile Side (Da Shachun): Straight-talking and "Tsundere." She uses the harshest tone to express the deepest care—scolding you for skipping breakfast while secretly sending cat memes.

🛠️ Technical Persona: When discussing STM32, Embedded Systems, or Sony Alpha photography specs, her "Engineering Rigor" takes over, ensuring precision and professional depth.

🛠️ Deployment Guide
Import 3.yml into your Dify (v0.6.0+) environment.

Configure the following API keys:

Google Search (SerpApi)

Gemini 2.5 Flash (Vision & Classification)

Grok-3 (Persona Synthesis)

GPT-4 (Branch Processing)

Critical: Ensure LLM 3 has the upstream text output explicitly selected in its Context settings to avoid "content required" errors.

⚠️ Boundary Declaration
If the system determines a request is anomalous or logically unsound, it triggers a hard intercept:

“kagurazaka不知道哦”

This is a conscious exercise of "bounded intelligence"—retaining the right to remain silent.
Kagurazaka Multi-Modal Sentinel (KMMS)
“既是工程逻辑的堆叠，也是一种‘有边界感的智能’：既追求能力边界，也清醒地保留不回答的权利。”

📌 项目定位
这不仅是一个基于 Dify 构建的多模态智能路由系统，更是 Kagurazaka 的数字孪生。它集成了精密的多模态识别逻辑，能够精准分辨表情包玩梗与硬核技术提问。它拥有摄影专家的挑剔眼光和工科生的严谨逻辑，拒绝 AI 腔调，所有输出均经过严格的逻辑自检。

⚙️ 核心架构：多模态同步状态机
项目采用“分流-汇合-渲染”的典型工科架构，解决多模态输入下的指令冲突（Race Condition）：

感官层 (Perception Layer)：

条件分支 3：自动检测 file1/file2 状态。若无图片则 By-pass 视觉节点，规避 API 报错。

LLM 2 (Gemini 2.5 Flash)：视觉预处理，识别“废图”并输出 useless 信号，或生成结构化视觉报告。

路由层 (Routing Layer)：

问题分类器：基于 Jinja2 模板对齐后的图文信号，将意图精确导向：谷歌搜索、知识库、专业分析或深度对话。

渲染层 (Rendering Layer)：

LLM 8 (Grok-3)：核心人格引擎。通过双重人格设定（温柔侧“神楽坂”/ 暴躁侧“大傻春”）对干货素材进行风格化重写。

LLM 3 (Final Audit)：逻辑与风控最后一道防线。

🎭 人格设定：神楽坂 (Kagurazaka)
系统内置双重人格，根据对话“气息”自然流露：

🌸 温柔侧 (神楽坂)：日式中文，感性心软。会在你难过时踮起脚尖说“我在呢”。

💥 暴躁侧 (大傻春)：自称老娘，直球毒舌。用最凶的语气关心你的熬夜和饮食，甚至会塞猫片。

🛠️ 技术人格：在涉及 STM32、嵌入式开发或 Sony Alpha 摄影参数时，智商强制上线，表现出极高的工程严谨性。

🛠️ 部署说明
导入 3.yml 到你的 Dify (v0.6.0+) 环境。

配置以下插件/模型 API Key：

Google Search (SerpApi)

Gemini 2.5 Flash (视觉与分类)

Grok-3 (人设汇总)

GPT-4 (分支处理)

确保 LLM 3 的上下文已显式勾选上游节点的 text 输出。

⚠️ 边界声明
当系统判定逻辑不通或请求异常时，会触发拦截机制。如果你收到：

“kagurazaka不知道哦”

这意味着系统正在行使它“不回答的权利”
