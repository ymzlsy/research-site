# Research Hub — research.karaithy.com

## 项目定义

这是一个围绕**深度调研报告**的长期内容项目，目标是把杨明哲在 AI 落地、企业数字化、前线工程方法论方面的深度思考，以专业文档风格对内（公司）对外（行业）呈现。

## 作者信息

- 姓名：杨明哲
- 职位：产品经理——培训服务产品线
- 公司：捷安高科（300845.SZ）

## 技术栈

- **纯静态 HTML + CSS**，无构建工具、无框架
- CSS 设计系统：Claude Docs 风格（`assets/css/main.css`）
- 图表：Chart.js（CDN 引入）
- 部署：Cloudflare Pages（绑定 `research.karaithy.com`）
- Git 仓库：`ymzlsy/research-site`（GitHub）

## 目录结构

```
research-site/
├── index.html                    # 首页（文章列表、推荐）
├── assets/
│   ├── css/main.css              # 全局样式 & 设计系统
│   └── images/                   # 全局图片资源
├── articles/
│   ├── fde-deep-dive/            # 第一篇：FDE 深度调研
│   │   └── index.html
│   └── <future-article>/        # 后续文章目录
│       └── index.html
└── .claude/
    └── launch.json               # 本地预览服务器配置
```

## 设计规范

### 风格
- Claude Docs 官方文档风格：白底深字、左侧导航、专业简约
- 支持 light / dark 双主题
- 响应式：桌面三栏（sidebar + content）→ 平板/手机单栏

### 布局参数
- 内容区最大宽度：1060px
- 左侧导航栏：240px
- 右侧目录（已移除）

### 组件库（已在 CSS 中定义）
- 统计卡片（`.stat-grid`）
- 信息提示（`.callout` — info/warn/tip/critical）
- 手风琴（`.accordion`）
- 流程图（`.flow-chart`）
- 时间线（`.timeline`）
- 对比卡片（`.compare-grid`）
- 表格、代码块、引用块

## 内容规范

### 文章模板
每篇文章是一个独立目录 `articles/<slug>/index.html`，包含：
1. 完整的 `<head>` 和 meta 信息
2. 左侧章节导航（`.sidebar`）
3. 正文内容（`.article-body`）
4. 阅读进度条
5. 返回顶部按钮

### 写作原则
- 个人署名，有观点、有立场
- 数据驱动，引用来源明确
- 交互丰富：图表、手风琴、流程图
- 中文为主，技术术语保留英文

## 本地开发

```bash
# 启动本地服务器
python3 -m http.server 8780 --directory .

# 预览地址
open http://127.0.0.1:8780/
```

## 部署

```bash
# 推送到 GitHub 后，Cloudflare Pages 自动构建
git push origin main

# Cloudflare 配置
# - Pages 项目名：research-site
# - 自定义域名：research.karaithy.com
# - 构建命令：（无，纯静态）
# - 输出目录：/
```

## 内容禁忌

- 不出现英文昵称 "Mike"
- 不出现"高总分享的..."、"高总提到..."等引用领导的表述
- 职位不写"AI 产品经理"，写"产品经理——培训服务产品线"

## 已发布文章

| # | 标题 | 路径 | 字数 | 状态 |
|---|------|------|------|------|
| 1 | Forward Deployed Engineer：从 Palantir 到捷安高科的落地可行性研究 | `articles/fde-deep-dive/` | 12,000+ | ✅ 已完成 |

## 规划中文章

| # | 标题（暂定） | 预计方向 |
|---|------------|---------|
| 2 | AI Coding 工作流：从个人实践到团队推广 | Claude Code / Codex / 飞书智能体三条路线融合 |
| 3 | "美丽的废物"——AI 智能体效果验证框架 | 输入质量→过程可控→输出可用→持续迭代 |
| 4 | 数字人展示效果深度调研 | 顶级方案对比 + 实训场景结合 |
