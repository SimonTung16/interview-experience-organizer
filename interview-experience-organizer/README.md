# 面经整理助手 Skill

面经整理助手是一个用于整理面经截图和面试记录的 Codex Skill。

它可以读取用户提供的截图、文本、Markdown、PDF 或 Word 文档，从中提取真实出现的面试问题，并根据用户指定的目标岗位进行去重、分类和答案生成，最终输出一份结构化的面试复习文档。

## 这个项目解决什么问题

在准备暑期实习、秋招、春招或社招时，很多人会从牛客、脉脉、小红书、知乎、微信群、飞书文档、博客等渠道收集大量面经。

这些材料通常存在以下问题：

* 截图太多，无法搜索；
* 问题重复，整理成本高；
* 不同岗位的问题混杂在一起；
* 原始面经只有问题，没有系统答案；
* 复习时难以判断优先级；
* 很难追踪某个问题来自哪张截图或哪份材料。

本 Skill 的目标是将这些零散材料整理成一份可复习、可追溯、可继续扩展的面试准备文档。

## 核心原则

本 Skill 采用材料驱动原则：

> 只整理用户提供材料中真实出现，或可以由 OCR 关键词明确推断的问题。
> 默认不额外补充材料中没有出现的岗位题库。

也就是说：

```text
材料里出现的问题 → 提取、去重、分类、生成答案
材料里没有出现的问题 → 默认不补充
```

目标岗位只用于调整：

* 分类方式；
* 答案视角；
* 代码语言偏好；
* 面试官追问方向；
* 项目题、场景题、案例题的回答重点。

例如，截图中出现了 `RAG chunk size`，并且目标岗位是 `AI Agent 开发工程师`，Skill 会将其整理为与 RAG 工程实践相关的问题，并生成面向 AI Agent 岗位的答案。

但如果截图中没有出现 `LangChain`、`多 Agent`、`Prompt Injection` 等内容，Skill 默认不会主动补充这些问题。

## 支持岗位

当前支持以下目标岗位：

* AI Agent 开发工程师
* LLM 应用开发工程师
* RAG 应用开发工程师
* 算法工程师
* 机器学习工程师
* 深度学习工程师
* 大模型算法工程师
* 前端开发工程师
* 后端开发工程师
* 客户端开发工程师
* Android 开发工程师
* iOS 开发工程师
* 测试开发工程师
* 软件测试工程师
* 产品经理
* 数据分析师
* 数据开发工程师
* 通用技术岗

## 主要功能

* 从截图中提取 OCR 文本；
* 从 `.txt`、`.md`、`.pdf`、`.docx` 文件中读取文本；
* 从原始材料中识别面试问题；
* 对相似问题进行合并去重；
* 保留问题的来源文件和原始表达；
* 根据目标岗位进行分类；
* 为每道题生成资深面试官视角的答案；
* 标注问题来源类型；
* 标注材料内出现频次；
* 标注面试重要性和难度；
* 输出 Markdown 复习文档；
* 可选导出 Word 文档。

## 适合谁使用

适合以下用户：

* 正在准备暑期实习的学生；
* 正在准备秋招、春招的求职者；
* 想整理牛客、脉脉、小红书等面经截图的人；
* 想把零散面试记录整理成系统文档的人；
* 想根据目标岗位生成复习答案的人；
* 想保留“问题来自哪里”的面经整理需求者。

## 安装与准备

克隆项目：

```bash
git clone https://github.com/your-username/interview-experience-organizer.git
cd interview-experience-organizer
```

安装 Python 依赖：

```bash
pip install -r requirements.txt
```

依赖示例：

```text
pillow>=10.0.0
pytesseract>=0.3.10
python-docx>=1.1.0
pymupdf>=1.23.0
tqdm>=4.66.0
```

说明：

* `pytesseract` 是 Python 调用库，不是 OCR 本体；
* 如果需要识别截图，需要本地安装 Tesseract OCR；
* 如果需要识别中文截图，需要安装 Tesseract 的中文语言包，例如 `chi_sim`；
* PDF 文本提取依赖 `pymupdf`；
* Word 文档读取和导出依赖 `python-docx`。

## 使用方式

在 Codex 中使用时，可以这样输入：

```text
请使用 interview-experience-organizer skill。

目标岗位：AI Agent 开发工程师
输入材料：./面经截图
输出语言：中文
输出格式：Markdown + Word

要求：
1. 只整理截图和文件中出现的问题。
2. 不要额外补充岗位常见题。
3. 根据目标岗位调整分类和答案视角。
4. 每道题需要包含：来源、考察点、回答框架、标准回答、常见追问、易错点、面试表达建议。
5. 如果是代码题，需要给出思路、参考代码和复杂度。
6. 如果 OCR 不完整，需要标注该问题是根据关键词推断的。
```

如果你要整理前端岗位面经，可以写：

```text
目标岗位：前端开发工程师
输入材料：./frontend_interview_screenshots
```

如果你要整理算法岗位面经，可以写：

```text
目标岗位：算法工程师
输入材料：./algorithm_interview_notes
```

如果你要整理产品岗位面经，可以写：

```text
目标岗位：产品经理
输入材料：./pm_interview_materials
```

## 输入材料格式

支持以下文件类型：

```text
.png
.jpg
.jpeg
.webp
.bmp
.txt
.md
.markdown
.pdf
.docx
```

示例输入目录：

```text
面经截图/
├── niuke_01.png
├── xiaohongshu_02.jpg
├── interview_notes.md
├── rag_interview.txt
└── product_case.pdf
```

## 处理流程

整体流程如下：

```text
截图 / 文本 / PDF / Word
        ↓
OCR 与文本提取
        ↓
原始文本整理
        ↓
问题识别与去重
        ↓
按目标岗位分类
        ↓
生成每道题的答案
        ↓
输出 Markdown 文档
        ↓
可选导出 Word 文档
```

## OCR 与文本提取

脚本位置：

```text
scripts/extract_interview_materials.py
```

运行命令：

```bash
python scripts/extract_interview_materials.py --input "./面经截图" --output interview_outputs
```

输出文件：

```text
interview_outputs/
├── 01_extracted_raw_text.md
└── extracted_items.json
```

其中：

| 文件                         | 说明              |
| -------------------------- | --------------- |
| `01_extracted_raw_text.md` | 原始文本提取结果，方便人工检查 |
| `extracted_items.json`     | 结构化提取结果，方便后续处理  |

OCR 结果会受到截图清晰度、字体大小、图片背景、语言包配置等因素影响。如果 OCR 不完整，Skill 会将相关问题标注为 `OCR 碎片推断`。

## Markdown 转 Word

脚本位置：

```text
scripts/md_to_docx.py
```

用途：

* 将最终 Markdown 面经复习文档转换为 Word 文档；
* 保留标题、段落、列表、表格和代码块；
* 方便打印、分享和离线复习。

运行命令：

```bash
python scripts/md_to_docx.py \
  --input interview_outputs/03_grounded_interview_review_document.md \
  --output interview_outputs/04_grounded_interview_review_document.docx
```

输入文件：

```text
interview_outputs/03_grounded_interview_review_document.md
```

输出文件：

```text
interview_outputs/04_grounded_interview_review_document.docx
```

## 输出结果

默认输出目录：

```text
interview_outputs/
```

典型输出文件：

```text
interview_outputs/
├── 01_extracted_raw_text.md
├── 02_extracted_question_bank.md
├── 03_grounded_interview_review_document.md
├── 04_grounded_interview_review_document.docx
└── extracted_items.json
```

主文档是：

```text
interview_outputs/03_grounded_interview_review_document.md
```

Word 文档是：

```text
interview_outputs/04_grounded_interview_review_document.docx
```

## 输出文档内容

最终文档通常包含：

* 材料概览；
* 从材料中提取的问题总览；
* 问题分类整理；
* 每道题的来源文件和来源表达；
* 每道题的面试官考察点；
* 回答框架；
* 标准回答；
* 深挖原理或方法论；
* 工程实践或业务落地；
* 常见追问；
* 易错点或风险点；
* 面试表达建议；
* 面试前速记版；
* 复习优先级建议；
* 原始材料索引。

## 问题来源类型

每道题都会标注来源类型。

### 原文直接问题

材料中存在完整问题。

示例：

```text
说一下 HashMap 的底层实现？
```

### 原文主题短语

材料中存在主题词，但不是完整问句。

示例：

```text
RAG chunk size
```

可能整理为：

```text
RAG 系统中 chunk size 应该如何选择？
```

### OCR 碎片推断

截图 OCR 不完整，但关键词足够明确，可以谨慎推断问题。

示例：

```text
... Redis ... 雪崩 ... 击穿 ...
```

可能整理为：

```text
Redis 缓存雪崩、缓存击穿和缓存穿透分别是什么？
```

### 同义合并

多个相似表达被合并为一个标准问题。

示例：

```text
HashMap 原理
说一下 HashMap
HashMap 底层
```

合并为：

```text
HashMap 的底层实现原理是什么？
```

## 示例

假设输入材料中出现：

```text
RAG chunk size 怎么选
embedding
召回不准怎么办
```

Skill 可以整理为：

```markdown
#### Q1：RAG 系统中 chunk size 应该如何选择？

**来源类型：原文主题短语**
**来源表达：RAG chunk size 怎么选**

...

#### Q2：Embedding 在 RAG 中起什么作用？

**来源类型：原文主题短语**
**来源表达：embedding**

...

#### Q3：RAG 召回不准应该如何优化？

**来源类型：原文主题短语**
**来源表达：召回不准怎么办**

...
```

但不会自动补充：

```text
LangChain 的优缺点是什么？
多 Agent 如何协作？
Prompt Injection 如何防护？
```

除非这些内容也出现在输入材料中，或者用户明确要求额外补充岗位高频题。

## 额外补充题

默认情况下，本 Skill 不会额外补充材料之外的问题。

如果你希望在截图问题之外补充岗位高频题，需要明确写：

```text
请在截图问题之外，额外补充该岗位高频题。
```

此时 Skill 会单独创建：

```markdown
## 附录：非截图来源的岗位补充题
```

这样可以避免“材料中出现的问题”和“额外补充题”混在一起。

## 使用注意事项

请避免将真实面经截图、微信群截图、聊天记录、个人简历、手机号、邮箱、微信号、公司内部面试记录等隐私或敏感材料放入公开仓库。

建议只在本地处理真实材料。

如果需要测试项目效果，可以使用虚构的 demo 材料。

## 常见问题

### 1. 这个项目会自动补充岗位题库吗？

默认不会。

它只整理输入材料中出现的问题。如果需要额外补充岗位高频题，需要在 prompt 中明确说明。

### 2. 截图 OCR 不准怎么办？

可以尝试：

* 使用更清晰的截图；
* 放大截图中的文字；
* 确认本地安装了 Tesseract OCR；
* 确认中文截图安装了 `chi_sim` 语言包；
* 对 OCR 结果进行人工检查。

### 3. 可以只用 Markdown，不导出 Word 吗？

可以。

Word 导出是可选步骤。主文档是 Markdown 文件：

```text
interview_outputs/03_grounded_interview_review_document.md
```

### 4. 可以整理多个岗位的材料吗？

可以，但建议一次指定一个目标岗位。

如果材料中混合多个岗位的问题，Skill 会优先按照用户指定的目标岗位进行分类和回答。

### 5. 答案来自哪里？

问题来源来自用户提供的材料。

答案由 Codex 根据问题和目标岗位生成。也就是说，问题必须有材料依据，答案可以使用通用专业知识进行解释和扩展。

## 设计理念

这个 Skill 不是岗位题库生成器，而是面经材料整理器。

它强调：

1. 来源可追溯；
2. 不凭空添加问题；
3. 对截图和文件中的问题进行整理；
4. 根据目标岗位调整答案视角；
5. 区分原文问题、主题短语、OCR 推断和同义合并；
6. 支持 Markdown 和 Word 复习文档输出。