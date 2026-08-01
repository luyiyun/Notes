---
name: codex-lecture-notes
description: Guide users through a stateful Chinese learning workflow and create or revise high-coverage Quarto lecture notes from chapters, books, PDFs/OCR, existing .qmd notes, webpages, papers, transcripts, slide decks, or mixed research materials. Use for new lecture-note topics, ongoing unit-by-unit learning, staged QMD assembly, scoped revisions within an active lecture-note task, source-backed expansion, or explicit restructuring. Maintain project-local progress and temporary preferences in `_codex_notes.md`. Do not use for standalone short summaries unrelated to an active lecture-note task, marketing copy, reading reflections, or unsupported opinion pieces.
---

# Codex Lecture Notes

## Purpose

Use a learning-first workflow while matching the process to the user's current task:

- **Full learning**: `学习目录确认 -> 逐节讲解与讨论 -> 用户要求整理 -> 最终大纲确认 -> 写入 QMD`.
- **Continuing and staged assembly**: teach confirmed units, assemble and write only the requested batch, then resume learning.
- **Scoped revision**: directly revise an explicitly bounded summary, transition, caption, term, heading, or local explanation after inspecting its context.
- **Project maintenance**: handle Quarto configuration, preview, navigation, and asset-path work without restarting the learning workflow; use the relevant companion skill when available.

Use supplied materials as anchors, add credible external evidence when it materially improves the note, and contribute clearly identified explanatory synthesis. Preserve important definitions, distinctions, formulas, figures, tables, examples, derivations, algorithms, limitations, cautions, and disagreements.

## Load Resources Proportionally

Load only the resources needed for the selected route:

- Read `references/note_style_guide.md` before detailed teaching, outline design, substantive drafting, restructuring, or style-sensitive revision.
- Read `references/source_search_protocol.md` before searching, selecting external sources, or comparing evidence. Do not load it for purely local wording, structure, formatting, or project-maintenance tasks.
- Read `references/lecture_note_style_guide.md` when designing learning units, a lecture-note series, staged chapter assembly, `series_index.qmd`, or chapter components.
- Read `references/quarto_qmd_conventions.md` before designing a QMD outline, modifying `.qmd`, integrating a note into a Quarto project, or validating a render.
- Use `assets/codex-notes-template.md` only when initializing project state.

## Guard Collaboration Mode

Check the active collaboration mode before starting or continuing the interactive learning workflow.

- If plan mode is active, explain that it interferes with the conversational learning process and ask the user to switch to default mode.
- Stop the learning workflow while plan mode remains active. Do not inspect learning materials, produce a directory, teach units, or write notes.
- Resume only after the environment reports default mode.

## Initialize and Maintain Project State

At the start of every lecture-note task, locate the project root in this order:

1. Use the Git repository root containing the target note or current working directory.
2. If no Git root exists, use the nearest ancestor containing `_quarto.yml`.
3. Otherwise use the current working directory.

At that root:

1. Read `_codex_notes.md` if it exists. Treat it as project-local workflow state, not as a formal note or source.
2. If it does not exist, create it from `assets/codex-notes-template.md`.
3. In a Git project, add the exact root rule `/_codex_notes.md` to `.gitignore` when absent. Preserve all existing ignore rules and never add the rule twice.
4. Modify only the managed region between the template markers. Preserve any user content outside that region.
5. If the root is not writable, continue with an internal state record and tell the user that persistent state could not be created.

Keep project preferences once, then maintain a task index plus one independent record per lecture-note task.

- Give every task a stable English kebab-case task ID. Reuse the ID when the target note and learning objective match; do not derive a new ID merely because the conversation changed.
- Use task statuses `planned`, `active`, `paused`, `blocked`, and `completed`. At most one task may be `active`; any number may be `planned` or `paused`.
- Resolve the current task from the user's explicit request, target note, and task index. If exactly one record matches, select it even when it is paused. Ask only when multiple records plausibly match and choosing incorrectly would change the work.
- When switching to a different task, change the previously active unfinished task to `paused`, preserve its full record, and mark the selected task `active`. Do not overwrite, rename, merge, or discard another unfinished task.
- Update only the selected task record plus its task-index row. Preserve every unrelated task record verbatim unless the user changes a project-wide preference.
- When an older `_codex_notes.md` contains a single `Active task`, `Paused task snapshot`, or equivalent legacy sections, migrate each distinct task into the task index and its own task record before the next state update. Preserve statuses, resume points, decisions, unit mappings, and pending work.
- When a task is completed, mark its record `completed` and clear the active-task pointer if it points to that task. Do not automatically activate another task without a user request.

Keep every task record concise and factual. Record:

- topic, target note, workflow route, note state, task status, current unit, and last QMD synchronization;
- the learning-unit status and its QMD section mapping;
- accepted corrections, skipped or deferred content, and superseded formulations;
- the current writing batch, pending figures, and next action.

Record project-wide temporary preferences only in the shared project-preferences section. Do not duplicate them inside every task.

Use these unit statuses consistently: `planned`, `current`, `discussed`, `confirmed`, `written`, `skipped`, and `deferred`.

Update the managed state after:

- the learning directory is confirmed or revised;
- a unit is discussed, confirmed, skipped, deferred, renumbered, or written;
- the user states or changes a persistent preference;
- the user corrects an explanation or manually edits the QMD;
- a staged writing batch starts or finishes;
- a figure is planned, generated, approved, inserted, rejected, or replaced;
- the task is completed or paused.

Never store hidden reasoning, raw chat transcripts, credentials, personal sensitive data, or a complete working source log in `_codex_notes.md`. On completion, retain the file, mark the task `completed`, preserve project preferences, and keep it ignored by Git.

## Select the Workflow Route

Choose the route before proposing a directory or editing a note.

### Full Learning

Use for a new topic, a new chapter with substantial learning, or an explicit comprehensive rewrite. Require both the initial learning-directory confirmation and the final QMD-outline confirmation.

### Continuing and Staged Assembly

Use when a confirmed learning task is already in progress or the user asks to write only the units discussed so far. Select the matching task record by its task ID, target note, and topic; do not default to whichever record appears first. Reuse that record and the current QMD as the baseline. Do not regenerate the full directory unless the user changes the overall scope.

For each requested batch:

1. Identify only the confirmed units included in the batch.
2. Propose a batch-level writing outline that includes their destination and consolidation into QMD sections.
3. Wait for explicit confirmation of that batch outline.
4. Write the batch, update state, and resume from the next non-skipped unit.

Do not pull deferred, skipped, future, or merely previewed material into the batch.

### Scoped Revision

Use when the user explicitly bounds a local change, such as a one- or two-paragraph summary, section introduction, transition, figure explanation, terminology correction, or heading adjustment.

- Treat the explicit target and constraints as scope confirmation.
- Inspect the target passage and its immediate predecessor and successor.
- Make the requested revision directly without rebuilding the learning directory or requiring a separate final outline.
- Do not broaden a local revision into a chapter rewrite.

### Project Maintenance

Use when the request concerns `_quarto.yml`, preview failures, navigation, bibliography paths, assets, or editor configuration.

- Inspect and repair the project integration directly.
- Use Quarto or other relevant companion skills when available.
- Do not restart teaching or require learning-directory confirmation.
- Keep editor-specific configuration outside the lecture-note content workflow.

## Classify the Note State

Within the selected route, classify the note as:

- **New note**: use the accessible user materials, relevant external evidence, and explanatory synthesis within the confirmed scope.
- **Incremental continuation**: treat the current QMD and `_codex_notes.md` as the learned baseline; teach and write only new or changed knowledge.
- **Explicit restructuring**: enter only when the user asks to restructure, comprehensively rewrite, or relearn the existing note.

If the difference between incremental continuation and restructuring would materially change the result and cannot be resolved from the repository or state file, ask the user.

## Ground and Clarify

Inspect user-provided materials, the target QMD, project context, YAML, links, bibliography, adjacent notes, series index, naming conventions, and established coverage in proportion to the selected route.

Search externally for new substantive knowledge, important theoretical or empirical claims, requested related literature, updates, disputes, or source comparison. Do not repeat external searches for a summary of already sourced material, a local transition, structural consolidation, formatting, preview repair, or editor configuration.

Ask only questions that materially affect scope, depth, source boundaries, mathematical detail, examples, figure intent, or series structure and cannot be answered from the materials, project, or `_codex_notes.md`.

## Propose and Maintain the Learning Directory

For full learning, return a pedagogical directory for confirmation before detailed teaching. Include the central question, learning units, important concepts or results, and planned examples, derivations, comparisons, or figures.

Treat the confirmed directory as a versioned learning plan:

- update its state mapping when the user removes, reorders, renumbers, skips, or defers a unit;
- preserve the distinction between learning-unit numbers and final QMD section numbers;
- record durable changes in `_codex_notes.md`;
- do not repeat unchanged baseline content when continuing an existing note.

The learning directory controls teaching order; it is not the final QMD heading structure.

## Teach and Discuss One Unit at a Time

Before each unit, read the current unit and the next eligible unit from the selected task record. Explain only the current unit.

- Motivate the problem, define concepts and notation, develop formulas or mechanisms, show intermediate reasoning, and discuss assumptions and limitations.
- Use examples, counterexamples, comparisons, or figures when they materially improve understanding.
- A transition may name the next unit's question, but must not teach its definitions, taxonomy, derivations, or main claims.
- Separate `introduce now`, `bridge only`, and `defer to later` content explicitly when adjacent units are easy to merge.
- When the user expresses confusion, distinguish concepts along their purpose, mathematical form, training effect, and failure conditions instead of relying only on terminology.

Maintain the latest accepted explanation. Treat later corrections and user-authored QMD edits as authoritative over superseded drafts. Persist durable preferences such as “不需要思考题”, “减少小节”, or “该方法只作概念介绍” and apply them until the user changes them.

If a new conversation lacks earlier dialogue, use the matching task record in `_codex_notes.md` and the current QMD first. Ask for the transcript or a detailed summary only when the user expects recovery of important discussion that was never recorded.

Do not modify QMD during teaching unless the user explicitly triggers staged assembly or a scoped revision.

## Assemble and Write QMD

After a full-learning assembly trigger, synthesize the accepted learning record and propose a detailed final outline. After a staged trigger, propose only the current batch outline. Wait for the confirmation required by the selected route.

Before every write:

1. Re-read the current QMD and the selected task record.
2. Treat user manual edits as authoritative and preserve unrelated content.
3. Map learning units into a smaller number of coherent QMD sections. Do not create one heading per teaching unit by default.
4. Prefer natural paragraphs, bold lead-ins, and purposeful callouts over fragmented headings when the material is only part of a larger note.

After every write:

1. Re-read the last paragraph before the change, the changed passage, and the first paragraph after it.
2. Fix duplicated definitions, premature discussion of later material, numbering drift, and weak transitions.
3. For a new note, verify `_quarto.yml`, navigation or sidebar entries, relative links, bibliography paths, and series indexes as applicable.
4. Run the narrowest relevant Quarto render and fix warnings or errors.
5. Update the selected task record in `_codex_notes.md` with the written mapping and next action.

Never edit generated Quarto output.

## Create and Integrate Figures

Before generating a figure, define a short figure brief containing:

- the concept or relationship the reader should understand;
- facts, formulas, labels, or geometric constraints that must remain correct;
- the intended style and any existing visual references;
- the planned caption, alt text, and destination.

Prefer ImageGen for figure creation, including conceptual diagrams and first attempts at mathematical illustrations. Inspect the generated result for visual quality and conceptual correctness. Do not claim that a figure is accurate merely because it looks plausible.

Switch to Python or another reproducible renderer only when:

- the user explicitly requests code;
- ImageGen fails or is unavailable;
- necessary quantitative, coordinate, functional, or geometric precision cannot be achieved reliably.

When using code, reuse the project's existing environment and conventions, such as uv, `_codes/`, and `assets/images/`, when present. Retain the generation script and appropriate raster or vector output.

Do not insert an ad hoc generated figure into QMD before the user approves it. A figure already included in a user-confirmed writing outline may be inserted after it passes conceptual and visual checks. Explain in nearby prose what the reader should notice.

## Handle Sources and Uncertainty

- Distinguish user-provided material, external evidence, and explanatory synthesis.
- Keep the detailed working source log internal; do not place it in `_codex_notes.md` or expose it as a formal note chapter.
- Cite important claims, definitions, empirical results, algorithms, formulas, disputes, and time-sensitive facts.
- Compare source scope, date, assumptions, method, and evidence when sources disagree.
- Mark inaccessible, extraction-uncertain, contradictory, or weakly supported content as `需人工复核` when it remains useful.

## Writing Requirements

- Write in Chinese with a rigorous, patient lecture-note or public technical-writing style.
- Explain why a concept is needed, how it is defined, what it solves, and where it fails.
- Keep formulas in LaTeX and explain important symbols, assumptions, transformations, and conceptual roles nearby.
- Use Key Idea, Remark, Summary, definitions, propositions, theorems, proofs, algorithms, examples, exercises, figures, and appendices only when they add teaching value and do not conflict with recorded user preferences.
- Place formal material near the concept that motivates it.
- Avoid meta headings such as `本篇定位`, `章节说明`, `可复用结论`, or `可复用结果` unless explicitly required.

## Done When

Apply completion criteria according to the selected route:

- **Full learning**: the user confirmed the learning directory and final QMD outline; the confirmed scope was taught, written, integrated, rendered, and recorded.
- **Staged assembly**: the requested batch outline was confirmed; only that batch was written and mapped; the next eligible unit remains clear.
- **Scoped revision**: the requested local change is complete, surrounding transitions remain coherent, and the target renders.
- **Project maintenance**: the concrete integration or preview problem is resolved and verified without altering unrelated note content.

For every route, preserve user corrections and manual edits, distinguish source roles, respect repository conventions, and avoid coverage-audit artifacts.

## Anti-Patterns

Do not:

- force every task through the full workflow;
- teach the next unit while answering the current one;
- confuse learning-unit numbering with QMD section numbering;
- turn every teaching unit into a separate heading;
- write skipped, deferred, future, or rejected material;
- overwrite user manual edits or unrelated worktree changes;
- regenerate a full directory for a bounded local revision;
- search externally for purely structural or formatting work;
- use code-generated figures before ImageGen unless a fallback condition applies;
- insert an unapproved ad hoc figure into QMD;
- duplicate `/_codex_notes.md` entries in `.gitignore`;
- replace an unfinished task record when starting or resuming another task;
- change multiple tasks to `active` or silently choose between ambiguous task records;
- store hidden reasoning, raw chats, sensitive data, or a complete source log in project state;
- present synthesis as source-backed fact, invent unavailable source content, or silently drop important uncertainty;
- add a visible source inventory, working source log, coverage audit, or audit directory to formal notes.
