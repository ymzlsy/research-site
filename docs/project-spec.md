# Research Hub — 项目规格书

> 项目代号：research-site
> 域名：research.karaithy.com
> 仓库：github.com/ymzlsy/research-site
> 创建时间：2026-05-24
> 维护者：杨明哲

---

## 一、项目定位

### 一句话定义
围绕**深度调研报告**的长期内容项目，以专业文档风格呈现杨明哲在 AI 落地、企业数字化、前线工程方法论方面的深度思考。

### 为什么值得做
1. **窗口期价值**：公司领导已关注 FDE/Palantir 等方向，抢先产出深度调研 = 从"跟随者"变"先行者"
2. **复利效应**：每篇调研报告都是长期资产，随时间增值（而非一次性消费品）
3. **品牌建设**：对内展示专业深度，对外构建个人影响力
4. **知识沉淀**：会议洞察、行业调研、技术思考有了永久归宿

### 核心受众
| 受众 | 看什么 | 频率 |
|------|--------|------|
| 公司领导层 | 执行摘要、落地方案、数据佐证 | 按需深读 |
| 公司同事 | 方法论、工具推荐、案例 | 分享时阅读 |
| 行业同行 | 框架思考、独立观点 | 搜索/推荐发现 |
| 自己 | 全部——写作即思考 | 持续维护 |

---

## 二、边界与不做什么

### 做
- 深度调研报告（5,000-15,000 字量级）
- 有数据、有图表、有交互元素
- 有明确观点和个人署名
- 每篇独立成文，可单独分享

### 不做
- 博客碎片（短文、日记、速记）→ 那是 Obsidian 的事
- 教程课程 → 那是 wiki.karaithy.com（VitePress）的事
- 新闻转载 → 只做一手调研和原创分析
- 公司内部机密信息 → 只呈现公开可查的内容

---

## 三、数据结构设计

### 核心实体：文章（Article）

```
Article {
  slug: string            // URL 路径标识，如 "fde-deep-dive"
  title: string           // 完整标题
  subtitle: string        // 副标题（可选）
  tags: string[]          // 标签，如 ["深度调研", "FDE", "Palantir"]
  category: enum          // 分类（见下方）
  author: "杨明哲"
  date: date              // 发布日期
  updated: date           // 最后更新日期
  wordCount: number       // 约字数
  readingTime: string     // 阅读时间
  status: enum            // 状态（见下方）
  abstract: string        // 一句话摘要
  chapters: Chapter[]     // 章节结构
}
```

### 分类体系

| 分类 | 标签色 | 说明 |
|------|--------|------|
| 深度调研 | 紫色 | 行业/公司/模式的全面研究 |
| 方法论 | 蓝色 | 工作方法、框架、思维模型 |
| 技术解析 | 绿色 | 特定技术的深度拆解 |
| 案例分析 | 橙色 | 具体案例的复盘与提炼 |

### 状态枚举

| 状态 | 含义 |
|------|------|
| draft | 写作中，未发布 |
| published | 已发布 |
| updated | 发布后有重大更新 |
| archived | 已归档（内容可能过时） |

### 生命周期

```
构思 → 素材收集 → 大纲定稿 → 写作 → 审校 → 发布 → 持续更新 → 归档
```

---

## 四、网站信息架构

### 首页（index.html）
- Hero 区：一句话定位 + 作者信息
- 最新调研：按时间倒序展示文章卡片
- 每张卡片：标签 + 标题 + 摘要 + 元信息（日期/阅读时间/字数）
- 未来可扩展：分类筛选、搜索

### 文章页（articles/<slug>/index.html）
- 左侧：章节导航（sticky）
- 中间：正文内容（1060px 最大宽度）
- 顶部：阅读进度条
- 底部：返回顶部按钮
- 交互元素：手风琴、图表、流程图、统计卡片

### 不需要的页面（当前阶段）
- 关于页 → 首页的 author-badge 够了
- 标签页 → 文章少于 5 篇时无意义
- RSS → 等文章数 ≥ 3 再考虑

---

## 五、维护流程

### 新增文章
1. 在 `articles/` 下创建新目录 `<slug>/index.html`
2. 复制文章模板，填充内容
3. 在 `index.html` 首页的文章列表中添加卡片
4. 本地预览（`python3 -m http.server 8780`）
5. `git commit` + `git push` → Cloudflare Pages 自动部署

### 更新文章
1. 编辑对应文章的 `index.html`
2. 更新首页卡片的日期/描述（如有变化）
3. 提交推送

### 工具链
- 写作：Claude Code 辅助（基于 CLAUDE.md 规范）
- 预览：本地 Python HTTP Server
- 版本管理：Git + GitHub
- 部署：Cloudflare Pages（自动）
- 域名：Cloudflare DNS CNAME

---

## 六、与 karaithy.com 子站体系的关系

```
karaithy.com
├── wiki.karaithy.com     → VitePress 知识库（教程、学习笔记）
├── ai-pm.karaithy.com    → AI 分享 PPT（单文件 HTML）
├── research.karaithy.com → 深度调研合辑（本项目）
└── (future)              → 更多子站...
```

技术选型差异化有意为之：
- **wiki** 用 VitePress（Markdown 驱动，适合频繁更新的教程）
- **research** 用纯 HTML（每篇文章高度定制交互，无需构建工具）
- **ai-pm** 用单文件 HTML（PPT 特殊需求）

---

## 七、分阶段路线

### Phase 0 — 当前（已完成）
- [x] CSS 设计系统
- [x] 首页框架
- [x] FDE 深度调研报告
- [x] 独立 Git 仓库
- [x] GitHub 创建

### Phase 1 — 本周
- [ ] Cloudflare Pages 部署
- [ ] 绑定 research.karaithy.com
- [ ] 在 AI 分享 PPT 中嵌入链接

### Phase 2 — 下个月
- [ ] 第二篇文章（AI Coding 工作流）
- [ ] 首页增加分类筛选
- [ ] 文章模板标准化

### Phase 3 — 三个月内
- [ ] 3-5 篇文章
- [ ] SEO 优化（meta, Open Graph, sitemap）
- [ ] RSS 订阅
- [ ] 阅读量统计（可选，Cloudflare Analytics）
