# 使用指南

1. 修改 docs 目录中的 Markdown 文件。
2. 在本地预览并检查页面及链接。
3. 提交修改并推送到 main 分支。
4. 在 Actions 页面查看构建与部署状态。
5. 打开网站检查内容是否更新。

## 常用命令

- python -m mkdocs serve：本地预览。
- python -m mkdocs build --strict：构建网站并严格检查警告。

## 本地预览完整步骤

在仓库根目录执行以下命令，创建并激活虚拟环境后启动预览服务器：

```bash
python -m venv .venv
source .venv/Scripts/activate
python -m pip install -r requirements.txt
python -m mkdocs serve
```

启动成功后，在浏览器打开终端提示的地址（通常为 `http://127.0.0.1:8000/`），逐个检查 [首页](index.md)、[关于](about.md)、[API 参考](api.md) 等页面。

## 发布更新

本地确认无误后，执行：

```bash
git add docs
git commit -m "更新文档内容"
git push origin main
```

推送后打开仓库的 Actions 页面，等待 `Deploy MkDocs to GitHub Pages` 工作流运行成功，然后刷新公开网站即可看到最新内容。

## 注意事项

- 不要把自动生成的 `site/` 目录提交到仓库，它已经写入 `.gitignore`。
- `mkdocs.yml` 中的 `nav` 路径相对于 `docs/` 目录书写，不要带 `docs/` 前缀。
- YAML 文件使用空格缩进，不能使用 Tab，否则构建会直接报错。
