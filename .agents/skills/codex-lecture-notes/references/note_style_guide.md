# Note Style Guide

Use this guide when planning, drafting, or revising Chinese Quarto lecture notes. Also load `lecture_note_style_guide.md` for series-level structure and lecture components.

## Language and Tone

- Write in Chinese.
- Use a style close to rigorous technical lecture notes: patient, motivating, mathematically explicit when needed, and organized around concepts rather than source order.
- Prefer precise, objective STEM prose. Keep motivating tasks in the exposition, but avoid conversational scene-setting, direct appeals to the reader, rhetorical questions used in place of analysis, and metaphorical or promotional wording.
- Use concise, conventional academic headings that identify the section's subject, such as `问题背景`, `研究历史`, `基本定义`, `模型设定`, `估计方法`, `数值结果`, and `目录`. Put narrative transitions in prose rather than headings such as `从一道……开始`, `一条由……推动的……`, or `讲义地图`.
- Avoid excessive colloquial language.
- Avoid empty AI-style generalizations such as "这些材料主要介绍了若干重要内容" without concrete content.
- Keep the source author's concept boundaries, distinctions, and reasoning order whenever possible.
- Optimize structure for learning, review, and knowledge reconstruction as a chapter in a larger series, but do not change source meaning.
- Do not remove details merely to make the notes shorter.

## Source Separation

Make source status visible in the prose, inline citations, local paragraphs, or `# 参考来源`; do not create a standalone source inventory, source log, or evidence-map chapter in formal `.qmd` notes.

- 用户提供材料: claims, examples, definitions, or arguments from the user's supplied sources.
- 外部证据: claims from searched papers, official docs, blog posts, datasets, or other materials.
- 解释性综合: your explanation that connects sources, clarifies mechanisms, or fills learning context.
- 需人工复核: inaccessible, ambiguous, contradictory, weakly supported, or extraction-uncertain content.

Use short source labels consistently, such as `[用户材料 A]`, `[外部来源 2]`, or inline Markdown links. Do not overload the notes with citations after every sentence, but cite each important claim, definition, empirical result, disputed point, and supplement.

## Target Files and Series Context

When the task targets an existing `.qmd`, edit that file rather than creating a generic new note. Inspect its YAML, links, bibliography, adjacent notes, and series index before changing structure.

When notes belong to a series:

- Reuse established notation, background, bibliography, and terminology.
- Do not repeat long unified notation, likelihood, estimation, or model-comparison sections from the index or general chapter.
- Briefly point to the general chapter, then focus on what this chapter uniquely adds.
- Identify whether material belongs in the index, general/theory chapter, current note, adjacent notes, appendices, or later software/reporting chapters.
- Preserve relative links, YAML style, `order`, and naming conventions already used by the site.

When synthesizing a learning dialogue into a note:

- Follow the user-confirmed final outline rather than the chronological order of the chat.
- Preserve substantive questions and answers, later examples, corrections, distinctions, and source additions.
- Use the latest accepted formulation when the discussion corrected an earlier statement.
- Re-read the current QMD before each staged write. Treat user-authored changes as the new baseline and do not restore superseded assistant drafts.
- Keep an earlier misconception only when contrasting it with the corrected view improves learning.
- Exclude process negotiation and other non-knowledge-bearing dialogue.

Persist durable user preferences in `_codex_notes.md` and apply them across later units and writing batches until the user changes them. Examples include excluding exercises, limiting mathematical detail, deferring method details, preferring fewer headings, or requesting a specific summary length.

## Coverage Principles

- Preserve definitions, classifications, formulas, figures, tables, cases, examples, derivations, assumptions, limitations, exceptions, cautions, and author-emphasized distinctions.
- Preserve lecture-relevant components when the material supports them: Key Idea, Remark, Summary, definitions, propositions, theorems, proofs, algorithms, examples, figure placeholders, appendices, and literature pointers.
- For uncertain but potentially important content, keep it and mark `需人工复核`.
- When paraphrasing copyrighted source material, preserve the knowledge structure through explanation and reformulation rather than long verbatim copying.
- Add explanatory thinking where helpful: why a concept matters, how a derivation works, what a figure shows, and how the next concept follows from the current one.
- When external sources disagree with the provided materials, describe the disagreement and likely reason instead of forcing a false consensus.

## Narrative Structure

Before drafting, choose a single smooth lecture line such as `主题定位 -> 核心问题 -> 关键思想 -> 定义与记号 -> 命题/定理 -> 推导/证明/算法 -> 例子与图表 -> 局限/分歧 -> 小结`. Each section should make the next section feel necessary. Avoid mechanical headings whose only function is to sort sources.

Prefer headings that sound like a lecture or technical note, not file-management metadata. Avoid headings such as `# 本篇定位`, `# 章节说明`, `# 可复用结论`, or `# 可复用结果` unless the source itself uses that language or the user asks for it. These usually expose file-organization intent instead of giving the reader a natural lecture structure. Avoid "...视角" headings when a direct method heading is clearer.

Do not map teaching units one-to-one onto QMD headings. When several units form one conceptual chain, combine them into a smaller number of sections and use natural paragraphs, bold lead-ins, or callouts for local distinctions.

After inserting or revising content, read the final paragraph before the change and the first paragraph after it. Repair abrupt transitions, duplicated definitions, numbering drift, and premature discussion of later sections.

For each chapter, prefer a narrative explanatory pattern:

```markdown
# 问题驱动的主题标题

## 本章要解决的问题

## 为什么这个问题需要被讨论

## Key Idea：本章的核心转写

## 定义、记号与基本对象

## 命题、定理或机制

## 推导、证明或算法如何一步步展开

## 例子、图表与应用

## Remark：注意事项、适用范围与常见误区

## Summary：本章小结
```

Adjust headings to fit the source, but preserve the logical functions. Do not use source-category labels as top-level sections in the final notes.

## Algorithms and Derivations

When sources contain algorithms, methods, formulas, or derivations, explain the process rather than only the broad idea:

- State the problem the method solves and why simpler ideas are insufficient.
- List inputs, outputs, assumptions, notation, and boundary conditions when available.
- Walk through intermediate derivation steps or algorithm phases in order.
- Explain why each transformation, update rule, approximation, or design choice is introduced.
- Include pseudocode when it helps reconstruct the method.
- Explain computational cost, convergence conditions, failure modes, or applicability limits when sources support them.
- Use a concrete example or toy calculation when the source provides one or when it can be safely derived from the source.
- If a derivation is too long, unreadable, or not fully available from the sources, mark omitted steps as `需人工复核` instead of replacing them with a vague summary.

Use algorithm blocks only when they add real explanatory value:

- Add an algorithm block when the source or user asks for a standalone procedure, or when the steps themselves are the object of study.
- Do not add a generic EM/Newton/Marquardt block to a specialized chapter if the same algorithm is already explained in the series general chapter.
- When only the distribution- or model-specific part changes, integrate those differences into the relevant subsection, such as the M-step, log-density, score, Hessian, constraints, or numerical optimization details.
- Keep algorithm explanations theory-first unless the user asks for software usage.

## Local Placement of Formal Material

Definitions, propositions, formulas, derivations, and algorithmic facts should appear near the concept that motivates them.

- Put a formal definition after the surrounding model pieces have been introduced, so it reads like a local synthesis.
- Put a proposition or formula immediately after the likelihood, model component, or argument it explains.
- Put posterior classification, EM, gradient, or Hessian facts in the estimation section where they are used, not in a detached "reusable results" section.
- Avoid collecting useful formulas into a meta section merely because later notes may cite them. If later reuse matters, add stable anchors to local definition/proposition blocks instead.

## Special Markers

Use Quarto callouts for explanations, key ideas, remarks, summaries, cautions, source conflicts, and review cues:

```markdown
::: {.callout-note title="说明"}
...
:::

::: {.callout-note title="Key Idea 1：..."}
...
:::

::: {.callout-warning title="容易混淆处"}
...
:::

::: {.callout-tip title="Summary：本章小结"}
...
:::

::: {.callout-important title="证据分歧"}
...
:::

::: {.callout-caution title="需人工复核"}
...
:::
```

Use labeled fenced Divs for definitions, examples, propositions, theorems, and proofs when the source contains formal material:

```markdown
::: {#def-short-id}

## 概念名称

定义内容。

:::
```

## Formulas, Figures, and Examples

- Keep formulas in LaTeX and explain each important symbol when ambiguity is possible.
- Explain each important formula in nearby prose: what it computes, what assumptions it relies on, and what conceptual role it plays.
- For derivations, preserve the main steps and intermediate logic instead of jumping directly to the conclusion.
- For figures and tables, include the source caption or a paraphrased caption, then explain what the figure or table demonstrates.
- If a figure is needed but not yet available, include a Quarto callout placeholder with suggested title, caption, source status, and what the figure should teach.
- For examples and cases, state the setup, result, and why the example clarifies the argument.

## Scientific Note Style

Aim for scientific lecture notes in the spirit of rigorous public technical writing: patient reasoning, mathematical or conceptual clarity, explicit motivation, formulas introduced as part of the prose, and enough detail for a careful reader to reconstruct the argument. Do not imitate personal voice or biographical style; imitate the commitment to derivation, detail, and explanatory structure.
