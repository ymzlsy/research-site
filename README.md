# Research Hub · research.karaithy.com

杨明哲的深度调研合辑 — AI 应用、企业数字化、前线工程方法论。

## 子站信息

| 项 | 值 |
|---|---|
| **线上地址** | https://research.karaithy.com |
| **Cloudflare Pages** | `research-site` → `research-site-cwd.pages.dev` |
| **GitHub** | [ymzlsy/research-site](https://github.com/ymzlsy/research-site) |
| **本地目录** | `~/Desktop/karaithy/research-site/` |
| **技术栈** | 纯静态 HTML + CSS，无构建工具 |
| **部署方式** | `git push origin main` → Cloudflare Pages 自动部署 |

## Kar<span style="color:#d97706">ai</span>thy 品牌规则

- 字标中 `ai` 两个字母使用 Claude 暖橙色 `#d97706` 强调
- 拆分渲染：`Kar` + `ai` + `thy`

## 快速开始

```bash
# 本地预览
cd ~/Desktop/karaithy/research-site
python3 -m http.server 8780
# 访问 http://127.0.0.1:8780/

# 发布
git add -A && git commit -m "update: ..." && git push
# Cloudflare Pages 自动构建部署
```

## 目录结构

```
research-site/
├── index.html                    # 首页
├── articles/
│   └── fde-deep-dive/            # FDE 深度调研（第一篇）
│       └── index.html
├── assets/
│   └── css/main.css              # 设计系统
├── docs/
│   ├── project-spec.md           # 项目规格书
│   └── article-template.html     # 文章模板
├── CLAUDE.md                     # AI 协作规范
└── README.md                     # 本文件
```

## 已发布文章

1. **[FDE 深度调研](https://research.karaithy.com/articles/fde-deep-dive/)** — Forward Deployed Engineer：从 Palantir 到捷安高科的落地可行性研究（12,000+ 字）

## 新增文章流程

1. 复制 `docs/article-template.html` 到 `articles/<slug>/index.html`
2. 填充内容
3. 在 `index.html` 首页添加文章卡片
4. 本地预览 → `git push` → 自动上线

## 维护须知

- **改内容** → 编辑 `articles/<slug>/index.html`，push 即生效
- **加文章** → 按上方流程操作
- **改样式** → 编辑 `assets/css/main.css`，全站生效
- **换账号** → 读 `CLAUDE.md` + `docs/project-spec.md`，5 分钟接手
- **换域名** → 改 Cloudflare Pages Custom Domain + 站内链接

## 环境依赖

- 无构建工具、无 Node.js 依赖
- 仅需 Python 3（本地预览用）
- Cloudflare 账号（Ymzlsy@gmail.com）
