# 李泽鑫 ｜ AI 数据标注与模型评测作品集

> 面向 **AI 数据标注 · AI 训练师 · 模型评测** 实习岗位的单页响应式个人作品集。
> 中文为主，突出真实分工、可量化数据指标与可复核的项目证据。

[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)](https://vitejs.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3-38B2AC?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Deploy](https://img.shields.io/badge/Deploy-GitHub%20Pages-222222?logo=githubpages&logoColor=white)](https://pages.github.com)

 **在线预览**：https://amphirion.github.io/lizexin-portfolio/
---

##  项目亮点

- **流动线条背景**：首屏采用 WebGL 着色器实现的流动线条（FloatingLines），深青墨色低透明度叠加白底，文字区加柔光衬底保证可读性。
- **鼠标拖尾效果**：光标移动时跟随迷你项目截图，使用「超级压缩图」（单张 1–13 KB）并在加载时预载进缓存，避免实时并发加载导致破图。
- **精选作品展示**：三个真实项目卡片，含封面、指标卡与「展开项目详情」灯箱（Lightbox），灯箱内展示未裁切原图。
- **证据轮播**：顶部证据流（EvidenceMarquee）首屏预加载，消除首屏卡顿。
- **三渠道即时联系**：底部「邮件联系」按钮支持一键复制 **电话 / 微信 / 邮箱**，并有「已复制」悬浮提示。
- **全端适配**：桌面与移动端分别优化对齐、字号与交互；移动端三处对齐（证件照、页脚、底栏）居中处理。
- **性能优先**：全站图片转为 `.webp`；展示图 `loading="lazy"`，首屏关键图 `fetchpriority="high"` + `<link rel="preload">` 预加载。
- **自包含资源**：图片、图标（深墨「李」印章 favicon）全部本地化，不依赖任何第三方图床或接口。

---

##  页面结构

| 区块 | 内容 |
| --- | --- |
| 首屏 Hero | 自我介绍（严格每行 24 字排版）、状态标签、流动线条背景 |
| 求职方向 Roles | 数据标注 / AI 训练师 / 模型评测 三大方向 |
| 精选作品 Projects | 三个真实项目卡片 + 指标卡 + 灯箱详情 |
| 技能 Skills | 数据标注、模型评测、工具链能力概览 |
| 关于 Profile | 证件照 + 院校 / 竞赛 / 实践信息卡 |
| 证据流 Marquee | 工作流与输出证据滚动展示 |
| 联系 Contact | 电话 / 微信 / 邮箱 一键复制 |
| 页脚 Footer | 导航 + 联系方式 + 站点信息 |

---

## 技术栈

- **框架**：React 19 + TypeScript（严格模式）
- **构建**：Vite 7
- **样式**：Tailwind CSS 3 + 少量自定义 CSS
- **图标**：lucide-react
- **图形**：WebGL2 着色器（流动线条背景）、Canvas（光标拖尾）
- **产物**：纯静态单页应用，无后端、无数据库、无在线 API

---

##  性能与加载策略

| 资源类型 | 策略 |
| --- | --- |
| 展示用项目图 / 证件照 | `.webp` 压缩 + `loading="lazy"` |
| 首屏轮播图（前 4 张）+ 左侧大人像 | `fetchpriority="high"` + `<link rel="preload" as="image">` |
| 光标拖尾小图 | 独立「超级压缩」目录（单张 1–13 KB），挂载时 `new Image()` 预载 |
| favicon | 矢量「李」印章 SVG + 多尺寸 PNG / Apple Touch 图标 |

> **GitHub Pages 部署注意**：本项目以**子路径**方式部署（`user.github.io/repo/`），因此所有静态资源（图片、超级压缩图、favicon、预加载链接）**一律使用相对路径**（`./images/...`、`./super-compressed_images/...`）。绝对路径（如 `/images/...`）在子路径下会被解析到域名根而 404，导致头像与拖尾破图。

---

## 🚀 本地运行

环境要求：**Node.js 20+**、npm 10+。

```bash
# 安装依赖
npm install

# 本地开发（默认 http://localhost:5173）
npm run dev

# 生产构建（产物位于 dist/）
npm run build

# 本地预览构建产物（默认 http://localhost:4173）
npm run preview

# 代码检查
npm run lint
```

---

## 📦 部署到 GitHub Pages

本仓库已构建为静态站点，部署只需上传 `dist/` 目录的全部内容到仓库根（或 Pages 源）。

```bash
# 1. 生成本地构建
npm run build

# 2. 将 dist/ 内的所有文件上传到 GitHub 仓库根目录
#    （含 index.html、assets/、images/、super-compressed_images/、favicon 等）

# 3. 在仓库 Settings → Pages 选择对应分支 / 目录即可
```

- `vite.config.ts` 中已设置 `base: './'`，确保子路径下资源相对解析正确。
- **不要只覆盖部分文件**：每次更新请整目录重新上传 `dist/`，避免旧资源残留导致破图。
- 浏览器对 favicon / 图片缓存顽固，上线后请 **Ctrl + F5** 强刷确认。

---

##  目录结构（构建后）

```
dist/
├── index.html                # 页面入口（含 favicon 与 preload）
├── assets/                   # 打包后的 JS / CSS
├── images/                   # 项目截图 + 证件照（.webp）
├── super-compressed_images/  # 光标拖尾用超级压缩图（.webp）
├── favicon.svg               # 矢量「李」印章
└── favicon-16x32x48.png / apple-touch-icon.png
```

---

##  许可

本作品集为**个人展示用途**。页面内容、文案与视觉设计版权归作者所有，未经许可请勿用于商业用途或整体搬运。

---

<p align="center">用心与数据构建 · 李泽鑫</p>
