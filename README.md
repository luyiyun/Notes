# Rong's Notes

这是一个用 Quarto 管理的个人笔记网站，用来逐步承接原来在 Obsidian 中维护的笔记。项目使用 Git 做版本管理，日常编辑以 Neovim 为主。

## Directory Map

```text
.
├── src/               # 笔记源文件，内部结构之后再定
├── resources/
│   ├── bibliography/  # BibTeX、CSL 等引用资源
│   └── templates/     # 笔记模板
├── assets/
│   ├── images/        # 图片
│   └── attachments/   # PDF、数据表等附件
├── archive/           # 不再活跃但需要保留的内容
├── _quarto.yml        # Quarto website 配置
├── AGENTS.md          # 给 AI agent 和协作者看的项目规则
└── README.md
```

## Neovim Workflow

在项目根目录打开 Neovim：

```bash
nvim .
```

常用编辑习惯：

- 新笔记放在 `src/` 下，具体子目录结构之后再定。
- 文件名使用英文 kebab-case，例如 `causal-inference.qmd`。
- 笔记内容可以中文、英文或双语；文件开头保留 Quarto YAML front matter。
- 链接使用标准 Markdown/Quarto 链接，例如 `[Causal Inference](causal-inference.qmd)`。

## Quarto Commands

本地预览网站：

```bash
quarto preview
```

渲染整个网站：

```bash
quarto render
```

Quarto 会生成 `_site/`、`.quarto/` 和 `*_files/`，这些目录已经在 `.gitignore` 中排除，不需要提交。

## Publishing Control

当前项目通过 Quarto 的 YAML header 控制笔记是否发布。准备发布的文件不需要额外字段；暂不发布的文件在开头加入：

```yaml
---
title: "Working Note"
draft: true
---
```

`_quarto.yml` 中已经设置 `draft-mode: gone`，因此带 `draft: true` 的页面在正式 `quarto render` 时不会进入导航、搜索、站点地图或列表。预览时仍可用来检查草稿效果。

## Git Workflow

第一次设置后可以按这个节奏管理：

```bash
git status --short
git add .
git commit -m "Initialize Quarto notes project"
```

之后每次整理一批笔记时：

```bash
quarto render
git status --short
git add .
git commit -m "Add notes about <topic>"
```

## Migrating From Obsidian

迁移一篇笔记时建议按这个顺序：

1. 把文件名改成英文 kebab-case，并保存为 `.qmd`。
2. 移入 `src/`，并在文件开头添加 YAML front matter，例如：

   ```yaml
   ---
   title: "过拟合 / Overfitting"
   draft: true
   ---
   ```

3. 将 Obsidian wikilinks 转换成标准 Markdown 链接。
4. 将图片移动到 `assets/images/`，其他附件移动到 `assets/attachments/`。
5. 内容准备发布时删除 `draft: true`。
6. 运行 `quarto render`，确认没有链接错误或渲染警告。
7. 用 Git 提交这次迁移。

## Naming Conventions

- Folders and filenames must be English.
- Use lowercase kebab-case for notes: `model-evaluation.qmd`.
- Keep display titles in YAML, not filenames.
- Prefer small focused notes over very large documents.
- Use relative links so the site works locally and after publishing.
