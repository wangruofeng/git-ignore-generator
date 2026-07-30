# git-ignore-generator — 项目约定（给 AI 协作时参考）

纯前端、单文件的 .gitignore 生成工具。面向人类的说明见 `README.md`；本文件记录**改代码时必须知道的红线与约定**。

## 红线（不要破坏）

- **单文件、零构建、零依赖**：全部 HTML / CSS / JS 都在 `index.html` 一个文件里。**禁止**引入打包器（Vite/Webpack 等）、框架（React/Vue 等）、npm 依赖或构建步骤。新增能力用原生 JS 实现。
- **纯前端、无后端**：所有模板与生成逻辑在浏览器本地完成，不上传任何数据。
- 主题用根元素 `html.dark` 类切换，配色全部走 `:root` / `html.dark` 里的 CSS 变量。新增颜色请复用已有变量，不要硬编码。
- 动态渲染请使用 `createElement` / `textContent`，避免使用 `innerHTML` 拼接用户可能接触的内容。

## 文件结构

- `index.html` — 全部代码（结构 + 样式 + 脚本）。
- `favicon.svg` — 站点图标。
- `.github/workflows/deploy.yml` — GitHub Pages 部署：仓库根即站点根，push 到 `main` 自动部署。
- `README.md` — 面向用户的功能说明与在线访问地址。
- `CLAUDE.md` — 本文件，项目约定与红线。

## UI 约定

- **按钮文案保持极简**：每个按钮都带 SVG 图标，图标已承担表意，文字尽量短（如「全选常用」「清空」「复制结果」「下载」）。
- 工具栏：全选常用 / 清空 / 复制结果 / 下载 / 统计。
- 页头右侧两个图标按钮：GitHub 源码链接（仓库 `https://github.com/wangruofeng/git-ignore-generator`，新标签页打开）、深浅色主题切换。
- localStorage key：`gig-theme`（主题）、`gig-selected`（已选模板）、`gig-custom`（自定义规则）。

## 在线地址

已部署到 GitHub Pages：https://blog.wangruofeng007.com/git-ignore-generator/
