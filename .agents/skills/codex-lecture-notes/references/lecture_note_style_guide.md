# Lecture Note Style Guide

Use this guide when producing Chinese Quarto lecture notes with `codex-lecture-notes`.

## Core Shape

Default to a lecture-note series, not a one-off summary, when the topic is broad enough to need multiple chapters. A topic may correspond to a series, and each note may correspond to one chapter.

Develop a new series through the full learning-first workflow:

1. Propose and confirm the learning directory in conversation.
2. Teach and discuss the confirmed units one at a time.
3. After the user requests full note assembly, propose and confirm a detailed final outline.
4. Create or update `series_index.qmd` only after that confirmation when it adds value or the repository requires it.
5. Write one `chapter_<slug>.qmd` at a time unless the user explicitly requests a batch.

For an ongoing task, allow staged assembly: propose and confirm an outline for only the discussed units, write that batch, update `_codex_notes.md`, and then continue with the next eligible learning unit. Do not regenerate the complete learning directory or pull future units into the current batch.

For an explicitly bounded summary, transition, caption, terminology correction, or local heading change, use the scoped-revision route from the main skill instead of forcing the full sequence.

Keep the source-backed coverage rules from the main skill. Lecture style changes the organization and teaching rhythm; it does not relax citation, evidence, or uncertainty-disclosure requirements.

## Series Index

After the detailed final outline is confirmed, use `series_index.qmd` to make the course-like plan explicit when the repository or topic benefits from a persistent series index:

```markdown
# 主题标题

## 主题定位

## 先修知识

## 学习目标

## 讲义目录

| 章 | 标题 | 内容精要 | 关键概念 | 主要材料 |
|---:|---|---|---|---|
| 1 | ... | 1-2 个自然段 | ... | ... |

## 建议附录

## 参考来源说明
```

Each chapter synopsis should be 1-2 substantive paragraphs. State the core question, why the chapter belongs in the series, the main concepts or results, and the intended transition to later chapters. Do not collapse this into a bare bullet list.

## Chapter Rhythm

A chapter should read like a patient technical lecture. Prefer this progression unless the source material forces another order:

1. Begin with the motivating question and why naive approaches are insufficient.
2. Introduce the minimum notation and definitions needed for the next step.
3. State the key idea before dense derivations.
4. Develop propositions, theorems, algorithms, or mechanisms in a logical order.
5. Use examples, toy cases, figures, or tables to make each abstraction concrete.
6. Add remarks for scope, intuition, variants, historical notes, or pitfalls.
7. End with a compact summary and, when useful and compatible with recorded user preferences, exercises or reflection questions.

Avoid source-inventory chapters such as `用户材料`, `外部检索资料`, or `资料列表`. Source status belongs inline, in local notes, or in `# 参考来源`.

## Learning Units and Heading Granularity

Keep teaching granularity separate from writing granularity.

- Use learning units to control conversational scope and prerequisites.
- Consolidate several related units into one coherent QMD section when they form a single argument.
- Do not create a heading for every definition, distinction, example, or teaching turn.
- Prefer natural paragraphs, bold lead-ins, and purposeful callouts when the material is only one part of a larger chapter.
- Preserve the mapping between learning units and QMD destinations in `_codex_notes.md`, including skipped, deferred, and renumbered units.

## Lecture Components In QMD

Use these components as rhythm anchors. Number them within each chapter when helpful.

### Key Idea

Use a callout for the central conceptual move:

```markdown
::: {.callout-note title="Key Idea 1：对象作为向量"}
生成对象可以先被表示为向量 $z \in \mathbb{R}^d$，随后生成任务就可以转写为从数据分布中采样。
:::
```

### Remark

Use remarks for extra resources, subtle assumptions, implementation cautions, or scope limits:

```markdown
::: {.callout-note title="Remark 1：适用范围"}
这一定义只覆盖连续空间中的对象；离散文本建模需要单独处理。
:::
```

### Summary

Use summaries at the end of chapters or dense sections:

```markdown
::: {.callout-tip title="Summary：本章要点"}
1. ...
2. ...
3. ...
:::
```

### Definitions, Theorems, Propositions, Examples

Use fenced Divs with stable IDs:

```markdown
::: {#def-data-distribution}
## 定义：数据分布

...
:::

::: {#thm-flow-existence}
## 定理：流的存在唯一性

...
:::

::: {#prp-conversion-formula}
## 命题：转换公式

...
:::

::: {#exm-linear-vector-field}
## 例子：线性向量场

...
:::
```

For proofs or derivations:

```markdown
::: {.proof}
证明。

...
:::
```

State conditions, notation, and consequences before the proof. After the proof, add a short paragraph explaining why the result matters for the chapter's main line.

### Algorithms

Use pseudocode for procedural content. Include inputs, outputs, assumptions, and the role of each non-obvious step.

````markdown
```text
Algorithm 1: 用 Euler 方法从流模型采样
Require: 向量场 u_theta, 步数 n
1. Set t = 0 and h = 1 / n
2. Sample X_0 ~ p_init
3. For i = 1, ..., n:
   a. X_{t+h} = X_t + h u_theta(t, X_t)
   b. t = t + h
4. Return X_1
```
````

Immediately after the algorithm, explain what it computes, which quantity is learned versus simulated, and where approximation error enters when the sources support it.

### Figures

Before producing a figure, define its learning objective, non-negotiable facts or mathematical constraints, style references, planned caption, alt text, and destination.

Prefer ImageGen for the first generation attempt. Inspect the result for both visual quality and conceptual correctness. Switch to Python or another reproducible renderer only when the user requests code, ImageGen fails, or required quantitative or geometric precision cannot be achieved reliably. Reuse the project's existing environment and asset conventions when code is needed.

Do not insert an ad hoc generated figure before the user approves it. A figure included in a confirmed writing outline may be inserted after it passes conceptual and visual checks.

When the image itself is unavailable or will be produced later, insert a figure placeholder instead of silently omitting the figure:

```markdown
::: {.callout-note title="Figure Placeholder：概率路径的边缘化直觉"}
**建议图题**：从条件概率路径到边缘概率路径。

**建议 caption**：左侧展示给定数据点 $z$ 的条件路径，中间展示多个条件路径混合后的样本云，右侧展示由边缘向量场诱导的轨迹。该图用于说明为什么条件对象经过边缘化后可以得到可采样的生成过程。

**来源状态**：待用户检索或生成；若改编自具体材料，需在最终图注中标明来源。
:::
```

Every figure or placeholder must explain what the reader should learn from it.

## Appendices

Use appendices when material is useful but would interrupt the main chapter flow:

- prerequisite reminders, such as probability theory or linear algebra;
- full proofs for results stated in the main chapters;
- implementation details or alternative perspectives;
- literature guides, historical lineage, or related formulations.

Start each appendix with a short note explaining whether it is required for the main line:

```markdown
# Appendix A：概率论回顾

本附录用于补齐阅读第 2-3 章所需的概率论记号；如果你已经熟悉条件期望和密度函数，可以先跳过。
```

## Chinese Style

- Use Chinese headings, prose, and explanations.
- Keep technical terms bold when first introduced or when they anchor the section, for example **数据分布**, **边缘向量场**, **score function**.
- Keep mathematical notation in LaTeX and define symbols near first use.
- Prefer "为什么需要这个概念 -> 如何定义它 -> 它解决什么问题 -> 有什么限制" over isolated definitions.
- Do not copy the original lecture's English wording. Imitate the organization, pacing, and explanatory discipline.
