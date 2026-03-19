# Refine无羡 · 认知军火库

> 一个从 Excel 创作台生长出来的个人知识库网站。735 篇文章，8 种体裁，16 个主题专栏，完整记录一位认知探索者的思想演化。

**在线访问 / Live Site**: [https://yuzhixuan191-glitch.github.io/cognitive-arsenal/](https://yuzhixuan191-glitch.github.io/cognitive-arsenal/)

---

## 项目简介 | About

这个项目的起点是一个 Excel 文件——「2025年-创作台-12月.xlsx」。文件里有 21 个 sheet 页，每个单元格都是一篇独立的文章：原创长文、认知纪要、AI 协作协议、创作剧本、复盘归档……它们散落在表格的各个角落里，像一座尚未被整理的认知矿场。

这个网站就是那座矿场的精炼厂。

This project started as a single Excel file — "2025年-创作台-12月.xlsx" — containing 21 sheets with articles scattered across individual cells: original essays, cognitive meeting minutes, AI collaboration protocols, creative scripts, and review archives. They sat in a spreadsheet like an unprocessed cognitive mine.

This website is the refinery.

---

## 功能特性 | Features

### 智能分类系统 | Smart Classification

- **体裁分类 (Genre)** — 自动识别 8 种写作体裁：原创文章、认知纪要、Prompt/协议、剧本/蓝图、复盘/归档、对话/投喂、系列规划、其他/杂记
- **主题专栏 (Topic)** — 跨体裁聚合为 16 个主题：巴别塔·悬搁哲学、艾梵·认知协处理器、健身·肉身道场、协议栈·写作系统……
- **创作时间线 (Timeline)** — 保留 Excel 原始 sheet 页的时间维度

### 首页数据仪表盘 | Dashboard

6 张 ECharts 交互式图表：

| 图表 | 说明 |
|------|------|
| 体裁分布 | 环形图，展示各体裁占比 |
| 主题分布 | 横向柱状图，按文章数排序 |
| 字数分布 | 柱状图，从 <500 字到 >20k 字 |
| 创作时间线 | 折线面积图，各时间段产出量 |
| 体裁×主题热力图 | 交叉维度分析 |
| 主题累计字数 | 各专栏总字数对比 |

### 文章工具栏 | Article Toolbar

- **一键复制** — 复制全文（标题+正文）到剪贴板
- **分享菜单** — 微信、QQ、微博、抖音、复制链接
- **生成卡片** — flomo 风格精美卡片图，可下载 2x 高清 PNG

### 其他 | More

- **全文搜索** — 按标题、摘要、体裁、主题实时检索
- **上传文章** — 粘贴内容后自动识别体裁和主题，保存到浏览器本地
- **明暗主题** — 深色（默认）/ 浅色切换
- **按需加载** — 文章索引 427KB 启动加载，正文按时间线分片按需拉取
- **响应式设计** — 桌面端和移动端均可使用
- **键盘快捷键** — `/` 聚焦搜索，`Esc` 关闭弹窗，`←` `→` 切换文章

---

## 技术栈 | Tech Stack

| 层面 | 技术 |
|------|------|
| 渲染框架 | 纯原生 HTML/CSS/JS，零构建依赖 |
| 数据可视化 | ECharts 5 |
| Markdown 渲染 | marked.js |
| 卡片图导出 | html2canvas |
| 字体 | Noto Serif SC + Noto Sans SC + JetBrains Mono |
| 部署 | GitHub Pages (静态托管) |
| 数据格式 | JSON (索引 + 分片内容) |

---

## 项目结构 | Structure

```
cognitive-arsenal/
├── index.html              # 主页面（约 52KB）
├── data/
│   ├── index.json          # 文章索引：标题、分类、摘要（427KB）
│   ├── manifest.json       # 分片映射表
│   ├── chunk_0.json        # 巴别塔（16 篇）
│   ├── chunk_1.json        # 蓝战非（4 篇）
│   ├── ...                 # 共 21 个内容分片
│   └── chunk_20.json       # 游泳健身复盘（48 篇）
├── docs/                   # 构建过程文档
│   └── build-journal.md    # 从 Excel 到网站的完整记录
└── README.md
```

---

## 数据概览 | Data Overview

| 指标 | 数值 |
|------|------|
| 文章总数 | 735 篇 |
| 累计字数 | ~438 万字 |
| 体裁类型 | 8 种 |
| 主题专栏 | 16 个 |
| 原始分类 (Excel sheets) | 21 个 |
| 时间跨度 | 2025.12 — 2026.02 |

---

## 本地运行 | Run Locally

```bash
git clone https://github.com/yuzhixuan191-glitch/cognitive-arsenal.git
cd cognitive-arsenal
python3 -m http.server 8080
# 访问 http://localhost:8080
```

> 注意：由于使用了 `fetch()` 加载 JSON 数据，直接双击打开 `index.html` 会因为 CORS 限制无法加载数据。请使用任意 HTTP 服务器。

---

## 设计理念 | Design Philosophy

**视觉**: 深色工业风底色 + 黄铜/金色强调色。灵感来自"认知军火库"这个名字——像一间灯光昏暗但秩序井然的军械室，每件武器都有自己的编号和位置。

**架构**: 数据与视图分离。文章索引（标题、分类、摘要）在启动时一次性加载，文章正文按时间线分成 21 个分片，点击阅读时按需拉取并缓存。这让首屏加载从 10MB 降到了 ~500KB。

**分类**: 不破坏原始 Excel 的时间线结构，在此基础上叠加体裁和主题两个新维度。三种视角，同一份数据。

**Visual**: Dark industrial base + brass/gold accents. Inspired by the name "Cognitive Arsenal" — like a dimly lit but meticulously organized armory where every weapon has its number and place.

**Architecture**: Data-view separation. Article index (titles, categories, previews) loads at startup; full content is split into 21 timeline-based chunks, fetched on demand and cached. This reduced first-load from 10MB to ~500KB.

**Taxonomy**: The original Excel timeline structure is preserved, with genre and topic dimensions layered on top. Three perspectives, one dataset.

---

## 许可 | License

本项目内容为个人创作，仅供学习参考。未经授权请勿转载文章内容。

The articles in this repository are personal creative works. Please do not reproduce without permission.

---

*Built with care by AI-human collaboration. From a messy Excel spreadsheet to a structured knowledge base — this is what cognitive refining looks like.*
