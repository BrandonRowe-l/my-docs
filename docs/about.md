# 关于本项目

## 项目目标

实现从 Markdown 文档到公开网站的自动化发布。

## 技术组成

| 工具 | 作用 |
| --- | --- |
| Markdown | 编写文档内容 |
| MkDocs Material | 将文档构建成静态网站 |
| GitHub Actions | 自动执行安装、构建和部署 |
| GitHub Pages | 托管并提供网站访问地址 |

## 工作流程

整个项目的发布链路可以概括为下面的步骤：

1. 在 `docs/` 目录中编写或修改 Markdown 文件。
2. 将改动提交并推送到 GitHub 仓库的 `main` 分支。
3. GitHub Actions 检测到与文档相关的文件发生变动，自动启动工作流。
4. 工作流中的 `build` 任务安装依赖并执行 `mkdocs build`，生成 `site/` 目录。
5. `deploy` 任务把构建产物发布到 GitHub Pages，网站随之更新。

## 技术选型体会

选择 MkDocs Material 主要有三点原因：一是它对中文支持友好，配置 `language: zh` 后搜索和界面文案都能正常本地化；二是它自带导航、搜索、代码高亮等文档站必备能力，几乎不需要额外开发；三是它与 GitHub Pages 的官方 Actions 工作流配合成熟，`actions/upload-pages-artifact` 和 `actions/deploy-pages` 可以直接消费构建产物，无需自己编写部署脚本。

相比在服务器上手工部署，这种"推送到仓库即发布"的模式把环境配置固化到了工作流文件中，任何一次部署都是可复现的，也方便日后回溯某一次发布对应的具体配置。
