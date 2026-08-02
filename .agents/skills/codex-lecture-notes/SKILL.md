---
name: codex-lecture-notes
description: Create, restructure, continue, and revise high-coverage Chinese Quarto lecture notes from chapters, books, PDFs/OCR, existing .qmd notes, webpages, papers, transcripts, slide decks, or mixed research materials. Use an outline-first, direct-to-QMD workflow for new notes, comprehensive rewrites, unit-by-unit writing, source-backed expansion, scoped revisions, and Quarto integration. Confirm and lock the complete heading outline, confirm each unit writing outline, then write directly to the target QMD while maintaining project-local state in `_codex_notes.md`. Do not use for standalone short summaries unrelated to an active lecture-note task, marketing copy, reading reflections, or unsupported opinion pieces.
---

# Codex Lecture Notes

## Purpose

Use an outline-first, file-review workflow while matching the route to the task:

- **New note or comprehensive restructuring**: `全篇标题大纲确认并锁定 -> 单元写入大纲确认 -> 直接写入 QMD -> 用户在文件中审阅`.
- **Continuing unit-by-unit writing**: reuse the confirmed outline and current QMD, confirm the next unit writing outline, then write it directly.
- **Scoped revision**: directly revise an explicitly bounded passage after inspecting its context; require an outline revision only when the requested change alters confirmed heading structure or crosses multiple unit boundaries.
- **Project maintenance**: repair Quarto configuration, navigation, preview, bibliography, or asset paths without restarting the content workflow.

Do not draft the full unit prose in chat before writing unless the user explicitly asks to learn, discuss, or review a conversational draft first. Use supplied materials as anchors, add credible external evidence when it materially improves the note, and preserve important definitions, distinctions, formulas, figures, tables, examples, derivations, algorithms, limitations, cautions, and disagreements.

## Load Resources Proportionally

- Read `references/note_style_guide.md` before outline design, substantive drafting, restructuring, or style-sensitive revision.
- Read `references/source_search_protocol.md` before searching, selecting external sources, or comparing evidence. Do not load it for purely local wording, structure, formatting, or project-maintenance work.
- Read `references/lecture_note_style_guide.md` when designing a lecture-note series, complete heading outline, unit writing outline, series index, or chapter components.
- Read `references/quarto_qmd_conventions.md` before designing a QMD outline, modifying `.qmd`, integrating a note into a Quarto project, or validating a render.
- Use `assets/codex-notes-template.md` only when initializing project state.

## Respect Collaboration Mode

Follow the active collaboration mode.

- In plan mode, inspect materials and design a decision-complete implementation plan, but do not modify QMD or project state.
- In default mode, follow the write gates in this skill and perform confirmed writes directly.

## Initialize and Maintain Project State

Locate the project root in this order:

1. When a target note or target directory is known, use its containing Git repository root; otherwise use its nearest ancestor containing `_quarto.yml`; otherwise use the target directory itself.
2. Only when no target location is known, use the Git repository root containing the current working directory, then its nearest ancestor containing `_quarto.yml`, and finally the current working directory.

At that root:

1. Read `_codex_notes.md` if it exists; treat it as workflow state, not as a formal note or source.
2. If absent, create it from `assets/codex-notes-template.md`.
3. In a Git project, add the exact root rule `/_codex_notes.md` to `.gitignore` when absent. Preserve existing rules and never add it twice.
4. Modify only the managed region between the template markers. Preserve user content outside that region.
5. If the root is not writable, keep equivalent internal state and report that persistence is unavailable.

Keep project preferences once, then maintain a task index and one independent record per lecture-note task.

- Give each task a stable English kebab-case ID. Reuse it when the target note and objective match.
- Use task statuses `planned`, `active`, `paused`, `blocked`, and `completed`. Keep at most one task `active`.
- Resolve the current task from the explicit request, target note, and task index. Ask only when multiple records remain plausible and the choice changes the work.
- Pause the previous unfinished task when switching tasks. Preserve unrelated task records verbatim.
- Mark a completed task `completed` and clear the active pointer if needed; do not activate another task without a request.

Record concisely:

- topic, target note, route, note state, task status, current unit, and last QMD synchronization;
- master QMD outline version and status, complete planned heading hierarchy, and approved outline changes;
- the fixed mapping from writing units to one or more adjacent target headings;
- accepted corrections, skipped or deferred content, current unit writing outline, pending figures, and next action.

Use unit statuses consistently:

- `planned`: included in the master QMD outline but not yet prepared for writing;
- `current`: the unit whose writing outline is being prepared;
- `discussed`: conversational teaching occurred because the user explicitly requested it;
- `confirmed`: the unit writing outline is confirmed and authorizes direct QMD writing;
- `written`: the confirmed unit is written and its relevant QMD render succeeded;
- `skipped` or `deferred`: excluded from the current writing sequence as directed.

Update state after the master outline is confirmed or revised; a unit outline is proposed, confirmed, written, skipped, or deferred; the user changes a durable preference or manually edits the QMD; a figure changes state; or a task is paused or completed.

Migrate legacy state only as needed for the next update. Preserve existing statuses, mappings, decisions, and completed structures. Do not force an already progressing task to reconfirm finished headings. Treat the current QMD and recorded accepted decisions as the baseline; confirm only unresolved future structure or a proposed structural change.

Never store hidden reasoning, raw transcripts, credentials, sensitive data, or a complete source log in `_codex_notes.md`. Retain the file on completion and keep it ignored by Git.

## Select the Workflow Route

### New Note or Comprehensive Restructuring

Use for a new topic, a new chapter with substantial content, or an explicit comprehensive rewrite.

1. Ground in the available materials, current QMD, series context, and sources.
2. Propose one master QMD outline containing the note title and every planned Markdown heading at levels 1--3, plus the writing-unit-to-heading mapping.
3. Wait for explicit confirmation and record the outline as a versioned, authoritative baseline.
4. Process one writing unit at a time through its unit writing outline and direct QMD write.

Do not introduce a second “final outline” or full-note assembly gate after units begin.

### Continuing Unit-by-Unit Writing

Use when a task is already in progress or the user asks to continue a particular note or unit.

- Select the matching task record and use the current QMD as the baseline.
- Reuse the confirmed master outline; do not regenerate it merely because the conversation changed.
- For legacy tasks without a stored master outline, treat written headings as fixed. Confirm only proposed future headings that are not already established.
- Continue from the next non-skipped unit after its unit writing outline is confirmed.
- Do not pull deferred, skipped, rejected, or future material into the current write.

### Scoped Revision

Use when the user bounds a local summary, introduction, transition, caption, term, heading, formula explanation, or nearby passage.

- Treat the explicit target and constraints as scope confirmation.
- Inspect the target and its immediate predecessor and successor.
- Revise directly without rebuilding the master outline or requiring a unit outline.
- If the request changes confirmed headings or crosses multiple writing-unit boundaries, propose a master-outline diff and wait for confirmation before editing.

### Project Maintenance

Inspect and repair Quarto integration directly. Use relevant companion skills when available. Do not require a content outline for configuration, preview, navigation, bibliography, asset-path, or editor work.

## Classify the Note State

- **New note**: build within the confirmed master outline using accessible materials, relevant evidence, and explanatory synthesis.
- **Incremental continuation**: treat the current QMD and state as authoritative; write only new or changed knowledge.
- **Explicit restructuring**: enter only when the user requests comprehensive restructuring, rewriting, or relearning.

Ask only when the distinction cannot be resolved from the repository or state and would materially change the result.

## Ground and Clarify

Inspect user materials, target QMD, YAML, links, bibliography, adjacent notes, series index, naming conventions, established coverage, and project state in proportion to the route.

Search externally for substantive new knowledge, important theoretical or empirical claims, requested related literature, updates, disputes, or source comparison. Do not repeat searches for already sourced material, structural consolidation, local transitions, formatting, preview repair, or editor configuration.

Ask only questions that materially affect scope, depth, source boundaries, mathematical detail, examples, figure intent, or series structure and cannot be answered from available context.

## Propose and Lock the Master QMD Outline

For a new note or comprehensive restructuring, present the master QMD outline before substantive writing.

- Include the note title and every planned `#`, `##`, and `###` heading. Omit a level only when no heading at that level is planned.
- Keep headings concise, academic, and reader-facing.
- Map each writing unit to one or more adjacent headings; several units may map to one coherent section, and one unit may cover adjacent headings.
- Note major planned derivations, examples, comparisons, figures, appendices, or source boundaries only where needed to make the structure unambiguous.
- Treat confirmation as approval of both heading hierarchy and unit mapping.

After confirmation, assign a version such as `v1` and treat it as authoritative. Do not add, remove, rename, reorder, promote, demote, split, or merge headings silently. When a structural change becomes necessary:

1. Show the exact heading and unit-mapping diff.
2. Explain the reason briefly.
3. Wait for explicit confirmation.
4. Record the new version and approved change before writing against it.

User-authored heading edits are authoritative. Reconcile state to those edits, but do not reinterpret them as permission for unrelated structural changes.

## Confirm and Write One Unit at a Time

Before each unit, re-read the confirmed master outline, the current QMD, the selected task record, and the next eligible unit. Present only a concise unit writing outline containing:

- exact destination heading or adjacent headings from the master outline;
- concepts and claims to cover, including explicit exclusions and deferred material;
- formulas, derivations, examples, tables, callouts, figures, and citations that are planned;
- intended transition from the preceding text and boundary with the following unit.

Wait for explicit confirmation. Treat that confirmation as the write trigger: write the unit directly into QMD, render it, and update state. Do not insert an additional prose-draft, discussion, batch-outline, final-outline, or assembly-confirmation step.

If the user explicitly requests explanation, discussion, or no file write, teach only the current unit in chat. Record it as `discussed`. When the user returns to writing, propose or revise the concise unit writing outline; after confirmation, write directly. A transition may name the next unit's question but must not teach its main content prematurely.

Maintain the latest accepted explanation. Treat later corrections and user-authored QMD edits as authoritative over earlier formulations. Persist durable preferences such as “不需要思考题”, “减少小节”, or “该方法只作概念介绍”.

## Write and Validate QMD

Treat conversation as working material, never as document prose. Reconstruct accepted explanations, questions, corrections, and examples into self-contained exposition shaped by the note's purpose, confirmed headings, terminology, and surrounding sections. Remove dialogue scaffolding and response framing; do not mention the exchange or preserve its chronology unless that order independently serves the chapter.

Before every write:

1. Re-read the current QMD, master outline, unit writing outline, and selected task record.
2. Preserve user manual edits and unrelated content.
3. Verify that every affected heading exactly matches the confirmed master outline.
4. Keep content within the confirmed unit boundary.

After every write:

1. Re-read the paragraph before the change, the changed passage, and the first paragraph after it.
2. Fix duplicate definitions, premature future material, numbering drift, and weak transitions without changing confirmed headings.
3. For a new note, verify `_quarto.yml`, navigation, relative links, bibliography paths, assets, and series indexes as applicable.
4. Run the narrowest relevant Quarto render and fix task-relevant warnings or errors.
5. Mark the unit `written`, record its heading mapping and synchronization, and set the next action.

Never edit generated Quarto output.

## Create and Integrate Figures

Before generating a figure, define a brief containing its learning objective, non-negotiable facts or mathematical constraints, intended style, caption, alt text, and destination heading.

Prefer ImageGen for the first attempt. Inspect visual and conceptual correctness. Use Python or another reproducible renderer only when the user requests code, ImageGen fails or is unavailable, or precise quantitative, coordinate, functional, or geometric accuracy requires it. Reuse project environments and asset conventions when code is needed.

Do not insert an ad hoc figure before approval. A figure already included in a confirmed master and unit outline may be inserted after conceptual and visual checks. Explain nearby what the reader should notice.

## Handle Sources and Uncertainty

- Distinguish user-provided material, external evidence, and explanatory synthesis.
- Keep the detailed working source log internal; do not place it in state or formal notes.
- Cite important claims, definitions, empirical results, algorithms, formulas, disputes, and time-sensitive facts.
- Compare scope, date, assumptions, method, and evidence when sources disagree.
- Mark useful but inaccessible, contradictory, weakly supported, or extraction-uncertain content as `需人工复核`.

## Writing Requirements

- Write in Chinese with a rigorous, patient lecture-note or public technical-writing style.
- Make QMD prose document-native and self-contained so it remains intelligible without the chat.
- Explain why a concept is needed, how it is defined, what it solves, and where it fails.
- Keep formulas in LaTeX and explain important symbols, assumptions, transformations, and conceptual roles nearby.
- Use Key Idea, Remark, Summary, definitions, propositions, theorems, proofs, algorithms, examples, exercises, figures, and appendices only when they add teaching value and respect recorded preferences.
- Place formal material near the concept that motivates it.
- Avoid meta headings such as `本篇定位`, `章节说明`, `可复用结论`, or `可复用结果` unless explicitly required.

## Done When

- **New note or comprehensive restructuring**: the master QMD outline was confirmed once; every included unit outline was confirmed, written directly, rendered, and recorded; the final headings match the latest approved outline version.
- **Continuing writing**: the requested unit outline was confirmed, that unit was written and rendered, and the next eligible unit is clear.
- **Scoped revision**: the bounded change is complete, surrounding transitions remain coherent, confirmed structure is preserved unless an outline revision was approved, and the target renders.
- **Project maintenance**: the integration or preview problem is resolved without altering unrelated note content.

For every route, preserve corrections and manual edits, distinguish source roles, respect repository conventions, and avoid coverage-audit artifacts.

## Anti-Patterns

Do not:

- require both a learning-directory confirmation and a later final-outline confirmation;
- teach or draft full unit prose in chat before writing unless explicitly requested;
- add another outline or assembly gate after a unit writing outline is confirmed;
- deviate from confirmed headings or unit mappings without an approved outline diff;
- confuse writing-unit numbering with QMD heading numbering;
- turn every unit, definition, or conversational turn into a separate heading;
- write skipped, deferred, future, or rejected material;
- overwrite user manual edits or unrelated worktree changes;
- regenerate a master outline for a bounded local revision or an unchanged continuation;
- copy conversational turns into QMD or frame passages as replies to the user;
- search externally for purely structural or formatting work;
- insert an unapproved ad hoc figure or use code generation before ImageGen without a fallback condition;
- duplicate `/_codex_notes.md` in `.gitignore`;
- replace unfinished task records, activate multiple tasks, or silently choose between ambiguous records;
- store hidden reasoning, raw chats, sensitive data, or a complete source log in project state;
- present synthesis as source-backed fact, invent unavailable source content, or hide material uncertainty;
- add a visible source inventory, working source log, coverage audit, or audit directory to formal notes.
