# Quarto QMD Conventions

Use this guide when producing or editing Quarto `.qmd` notes, especially for notes intended to live near `/Users/rong/Project/notes`.

## Target Files and Naming

- If the user provides a concrete `.qmd`, edit that file.
- If the task is a new note in an existing Quarto project, follow the repository's folder, filename, `order`, bibliography, and link conventions.
- Use English folder and file names in kebab-case for note files.
- Use `series_index.qmd` and `chapter_<slug>.qmd` for new research-series work unless the repository has a stronger naming convention.
- Use `chapter_notes.qmd` only when no target file, project convention, or user-specified filename exists.
- Preserve existing YAML front matter unless a change is needed for the task.
- For series notes, inspect the index and adjacent files before choosing titles, `order`, and links.

## Write Gate

- For full learning, do not create or modify QMD during grounding, directory design, teaching, or discussion. Begin writing only after the user requests assembly and confirms the detailed final outline.
- For staged assembly, write only the units in the user-confirmed batch outline, then return to the learning sequence.
- For an explicitly bounded local summary, transition, caption, terminology correction, or heading change, treat the request itself as scope confirmation and revise directly after inspecting the surrounding content.
- For project maintenance, repair Quarto integration or preview problems without requiring learning-directory or final-outline confirmation.
- Validate the resulting QMD against the confirmation required by the selected route and repository conventions without creating an audit artifact.

## Frontmatter

Start notes with YAML frontmatter when enough metadata is known:

```yaml
---
title: "主题标题"
subtitle: "可选副标题"
description: "一句话说明本篇讲义覆盖的用户材料与外部证据范围"
draft: false
aliases:
  - 关键词
tags:
  - 讲义
date-modified: last-modified
---
```

Omit unknown fields rather than inventing metadata.

When migrating from Obsidian, convert `created` to `date` and replace `updated` with `date-modified: last-modified`.

## Heading Hierarchy

- Use `#` for major note sections.
- Use `##` for stable explanatory-note subsections.
- Use `###` sparingly for local detail.
- Do not create one QMD heading per conversational learning unit. Consolidate units that form one argument.
- When the edited content is only part of a larger note, prefer natural paragraphs, bold lead-ins, and purposeful callouts over fragmented headings.
- Keep headings descriptive and close to the user's materials while allowing a clearer synthesized structure.
- Make headings advance a smooth explanatory main line. Avoid top-level source-inventory headings or source-category headings.
- In `series_index.qmd`, use headings for topic positioning, prerequisites, learning objectives, table of contents, appendices, and reference-source notes.
- In chapter files, use headings for motivating questions, definitions and notation, results, derivations or algorithms, examples and figures, remarks, summary, exercises, and references.

## Series Notes

When editing a note in a series:

- Reuse notation, background, and scope from the series index instead of repeating it.
- Create or update the series index only after the detailed final outline is confirmed.
- Update relative links if files are renamed or moved.
- Keep `order` contiguous when the series depends on numeric ordering.
- Check adjacent notes for references such as "上一篇", "第 3 篇", or explicit filenames.
- Keep bibliography paths consistent with existing notes.

## Project Integration and Validation

Before editing an existing QMD, re-read the target passage and its immediate predecessor and successor. Treat user manual edits as authoritative and preserve unrelated changes.

When creating a new note or moving an existing one:

- inspect `_quarto.yml` for `project.render`, sidebar, navbar, book chapters, or other explicit inclusion rules;
- add the source note to the relevant navigation or render configuration when the project requires it;
- verify relative links, image paths, bibliography paths, `order`, and series-index references;
- never add `_codex_notes.md` to Quarto navigation, a bibliography, or formal note content.

After a QMD change, run the narrowest relevant `quarto render` command. Fix errors and task-relevant warnings, and do not edit `_site/`, `.quarto/`, or `*_files/`.

## Citations and Source Links

Use one of these patterns consistently:

- Markdown links for web sources: `[来源标题](https://example.com)`.
- Short source labels tied to `# 参考来源`: `[外部来源 2]`.
- Quarto citations such as `[@key]` when a bibliography is available or created.

Include a `# 参考来源` or `## 参考来源` section unless the user requests another citation format. Keep source labels and citations inline or in the reference section; do not add a standalone evidence-map or source-log section to the final notes.

## Math

Use inline math with `$...$` and display math with `$$...$$`.

For multi-line derivations, use aligned environments:

```markdown
$$
\begin{align}
a &= b + c \\
  &= d.
\end{align}
$$
```

## Lecture Components

Use Quarto callouts for lecture rhythm:

```markdown
::: {.callout-note title="Key Idea 1：核心思想"}
...
:::

::: {.callout-note title="Remark 1：补充说明"}
...
:::

::: {.callout-tip title="Summary：本章小结"}
...
:::
```

## Definitions, Examples, Theorems, Proofs

Use fenced Divs with IDs for source concepts that need cross-reference-friendly anchors:

```markdown
::: {#def-short-topic}

## 定义名称

定义内容。

:::

::: {#exm-short-topic}

## 例子：短标题

例子内容。

:::

::: {#thm-short-topic}

## 定理：短标题

定理内容。

:::

::: {#prp-short-topic}

## 命题：短标题

命题内容。

:::

::: {.proof}
证明或推导。
:::
```

Prefer short, stable IDs using lowercase English words and hyphens.

## Callouts

Use Quarto callouts for explanatory annotations:

```markdown
::: {.callout-note title="说明"}
...
:::

::: {.callout-warning title="容易混淆处"}
...
:::

::: {.callout-important title="关键区分"}
...
:::

::: {.callout-caution title="需人工复核"}
...
:::
```

## Tables and Figures

Use Markdown tables for compact comparisons:

```markdown
| 概念 | 来源 | 条件 | 作用 |
|---|---|---|---|
| ... | ... | ... | ... |
```

Use Markdown image syntax when a source figure is available and use is appropriate:

```markdown
![图题或说明](path-or-url)
```

After each figure or table, add a short paragraph explaining what it shows and why it matters for the section's argument.

When the figure is planned but not yet available, use a placeholder callout:

```markdown
::: {.callout-note title="Figure Placeholder：图题"}
**建议图题**：...

**建议 caption**：...

**来源状态**：待检索、待绘制或需标注改编来源。
:::
```

## Algorithms

Use fenced code blocks or compact tables for pseudocode. Keep variable names stable and explain inputs, outputs, assumptions, and approximation points immediately after the algorithm.

````markdown
```text
Algorithm 1: 算法名称
Require: 输入
Return: 输出
1. ...
```
````

## Local Style Observed in Notes

The lecture notes favor:

- Chinese explanatory prose with explicit motivation.
- LaTeX formulas and step-by-step derivations.
- Detailed algorithm and method explanations with inputs, outputs, assumptions, notation, and intermediate steps when sources support them.
- Labeled definition/proposition/example blocks.
- Callouts for important distinctions, cautions, source conflicts, and clarifying remarks.
- Tables for comparing sources, concepts, representations, or conditions.
- Section introductions that explain why the next concept is needed.
- Series index pages with chapter synopses before chapter drafting.
- Appendices for prerequisite reminders, full proofs, implementation details, alternative perspectives, and literature guides.
