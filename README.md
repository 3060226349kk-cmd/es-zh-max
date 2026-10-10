# es-zh-max — 西中互译 Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

[中文](#这是什么) · [English](#english)

> 西班牙语与中文互译和润色，主方向是西译中，也做中译西。方法论基于赵士钰《新编汉西翻译教程》，按工作量分三档，附机检脚本（含西语语义假朋友检测）。

## 这是什么

es-zh-max 是一个翻译 skill，Claude Code、DeepSeek Harness 等支持 Agent Skills 的工具都能用。它根据原文语言自动判断方向，产出西中或中西对照译文。

- **方法论基础**：赵士钰《新编汉西翻译教程》（外语教学与研究出版社，1999）。原书是汉译西教程。
  - 中译西直接用书中方法。
  - 西译中的做法由书中规则反推，并补充通行做法。
- **出处标注**：
  - `[chNN]`：依据原书，章节文件里注有原书页码。
  - `[通用]` 和〔通〕：书外补充的通行做法。

**两个方向互为镜像**：
- 汉译西要「形合化」：补关联词、主语和时体式，名词化。
- 西译中要「意合化」：省掉关联词和代词，把名词化结构还原成动词，把层级结构摊平成连动句和流水句。

## 工作流
| 档 | 场景 | 读什么 |
|---|---|---|
| 小 | 聊天里几句、一段 | 只读 SKILL.md，在回复里直接给对照 |
| 中 | 一篇文档 | 加读速查表；西译中再读操作手册，中译西再读错误表和相关章节 |
| 大 | 整本书 | 另建项目目录，配翻译计划和术语表，逐章翻译 |

流程是：定性 → 理解（三读原文）→ 初译 → 校核（对照原文、脱离原文通读、回译抽检）→ 定稿（机检）。

## 安装
```bash
cd ~/.claude/skills/        # 或你的 agent 的 skills 目录
git clone https://github.com/3060226349kk-cmd/es-zh-max.git es-zh-max
```
依赖 Python 3.8+。导出 PDF 时另需 `playwright`。

## 使用
```
西译中：
（西语原文）
```
```
中译西：
（中文原文）
```

## 项目结构
```
es-zh-max/
├── SKILL.md              # 入口：判断方向和工作量、流程、十组镜像规则、章节和主题索引
├── es2zh.md              # 西译中操作手册：西语结构对应的汉语处理、翻译腔症状、专名数字、校核清单、语义假朋友表
├── zh2es-errors.md       # 中译西常见错误（据原书「译文改错」练习归纳）
├── cheatsheet.md         # 一页速查
├── glossary.md           # 中西术语对照
├── register-variety.md   # 西班牙与拉美用词差异、称谓、口语与粗话的语域对照
├── chapters/             # 原书七章逐章提炼（13 个文件，附原书页码和「西译中反推」）
└── scripts/
    ├── check.py               # 机检：标点残留 + 翻译腔信号；--pairs es2zh.md 查语义假朋友
    └── bilingual-to-pdf.py    # 对照 MD → HTML + PDF
```

## 说明
本仓库是对原书方法的提炼与评注。引用的例句只用来说明方法，原书版权归作者和出版社所有。

## 许可
[MIT](LICENSE)

## English
es-zh-max is a Spanish↔Chinese translation skill for agents that support Agent Skills (Claude Code, DeepSeek Harness and others). It defaults to Spanish→Chinese and also handles Chinese→Spanish.

- **Method**: Zhao Shiyu's *Nuevo curso de traducción del chino al español* (FLTRP, 1999), a Chinese→Spanish textbook.
  - Chinese→Spanish follows the book directly.
  - Spanish→Chinese guidance is derived by inverting the book's rules and is marked as such.
  - General practice from outside the book is tagged separately.
- **Tiers**: work is sized in three tiers (snippet, document, book).
- **Check script**: `scripts/check.py zh|es <file> --fix` fixes punctuation and reports translationese signals. `--pairs es2zh.md` flags Spanish false friends such as *actual* → 实际 or *billón* → 十亿.

MIT licensed. Example sentences quoted from the book are used for commentary only.
