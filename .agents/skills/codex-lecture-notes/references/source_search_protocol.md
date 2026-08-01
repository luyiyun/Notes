# Source Search Protocol

Use this protocol before searching or selecting external sources for `codex-lecture-notes`.

## Search Requirement

Search for external sources when the task introduces substantive new knowledge, important theoretical or empirical claims, source comparison, requested related literature, or potentially updated information, unless the user explicitly forbids browsing or external supplementation. If search tools are unavailable, continue with user-provided materials only and state the limitation when materially relevant.

Use browsing/search especially when:

- The user asks for "相关文献", "博客", "结合搜索", "最新", "state of the art", or source comparison.
- The topic is technical, medical, legal, financial, policy-related, fast-changing, or otherwise likely to have important updated sources.
- The provided material contains claims that need verification, context, or comparison.

Do not initiate or repeat external search for:

- a summary of content already grounded and cited;
- a local transition, caption, terminology correction, or heading consolidation;
- Quarto configuration, preview repair, or editor configuration;
- a staged write that adds no new factual claim beyond the confirmed learning record.

## Query Strategy

- Start from the user's exact topic terms, titles, author names, product names, paper titles, URLs, or quoted phrases.
- Search in both Chinese and English when the topic is cross-lingual or technical.
- Use targeted queries for concepts, formulas, methods, objections, and examples found in the user's materials.
- Search for updates or critiques when a claim appears dated, controversial, or domain-sensitive.
- Prefer opening sources rather than relying on search snippets.

## Source Priority

Prefer sources in this order when relevant:

1. Primary sources: official documentation, standards, specifications, original papers, laws or regulations, datasets, author pages, and project repositories.
2. High-quality secondary sources: review papers, textbooks, reputable technical blogs, institutional explainers, and course notes.
3. Contextual sources: conference talks, well-maintained tutorials, expert essays, issue discussions, and forum threads.
4. Low-confidence sources: SEO summaries, unsourced blogs, reposts, generated content, and pages with unclear authorship.

Use lower-priority sources only for examples, community context, or when better sources are unavailable. Mark weak evidence clearly.

## Working Source Log

Create a working source log before detailed teaching. Maintain it as an internal learning and drafting aid, not as a section to copy into formal `.qmd` notes.

| Label | Source | Type | Role | Key Contribution | Caveat |
|---|---|---|---|---|---|

Use roles such as:

- Confirms: supports a claim from the user-provided material.
- Clarifies: explains a concept, mechanism, formula, or example.
- Extends: adds related evidence or a useful adjacent concept.
- Contrasts: gives a different framing, assumption, or terminology.
- Updates: supersedes or revises older information.
- Challenges: contradicts or weakens a claim.
- Background: useful context but not central evidence.

Do not copy the detailed working source log into `_codex_notes.md`. Record only source-related task status there, such as “primary source verification pending”.

## Citation Rules

- Cite important claims, definitions, empirical results, algorithms, formulas, disputes, and historical or date-sensitive facts.
- Include title, organization or author when available, URL or DOI, and publication date or access date when relevant.
- Use Markdown links, source labels, footnotes, or Quarto citations consistently.
- Keep source labels and citations inline or in `# 参考来源`; do not create a standalone evidence-map, source-log, or source-inventory chapter in the final notes.
- Avoid long verbatim quotations. Prefer paraphrase and concise explanation.
- If a source is paywalled, inaccessible, or only visible through snippets, mark it as `需人工复核` and do not treat it as verified.

## Conflict Handling

When sources disagree:

- Identify the exact claim under disagreement.
- State which source says what, with citations.
- Compare scope, date, method, assumptions, and evidence quality.
- Explain whether the disagreement is a real contradiction, terminology difference, version difference, or context difference.
- Do not force consensus. Preserve the uncertainty if the evidence does not resolve it.

## Unsupported Synthesis Guardrails

- Do not invent definitions, results, formulas, or examples that are absent from the sources.
- Do not present a synthesis as source-backed fact unless the cited sources support it.
- If you add an explanatory bridge, make it clear that it is explanatory synthesis.
- If an external source only loosely relates to the user's topic, say so instead of overstating relevance.
- Keep the user's provided materials as the anchor, even when external sources are richer or more polished.
