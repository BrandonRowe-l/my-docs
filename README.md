# my-docs

我的 MkDocs 个人文档网站实践项目：使用 Markdown 与 MkDocs Material 编写四页文档，通过 GitHub Actions 自动构建并部署到 GitHub Pages。

- 在线网站：<https://brandonrowe-l.github.io/my-docs/>
- 个人实验报告：[report/README.md](report/README.md)

## 项目结构

```text
my-docs/
├── .github/workflows/deploy.yml   # GitHub Actions 自动部署工作流
├── docs/                          # 网站内容（Markdown）
├── report/                        # 作业实验报告与截图
├── mkdocs.yml                     # MkDocs 站点配置
├── requirements.txt               # Python 依赖
└── .gitignore
```

## 本地预览

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1   # Windows PowerShell；Git Bash 用 source .venv/Scripts/activate
python -m pip install -r requirements.txt
python -m mkdocs serve
```

浏览器打开 `http://127.0.0.1:8000/` 预览。

## 自动部署

推送到 `main` 分支且改动涉及 `docs/**`、`mkdocs.yml`、`requirements.txt` 或工作流文件时，工作流 `Deploy MkDocs to GitHub Pages` 会自动执行：安装依赖 → `mkdocs build --strict` → 上传 `site/` → 发布到 GitHub Pages。也可在 Actions 页面通过 `workflow_dispatch` 手动触发。
