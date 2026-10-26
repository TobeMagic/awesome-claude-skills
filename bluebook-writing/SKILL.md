---
name: bluebook-writing
description: Write design-reading books or long technical articles in plain language using the two-layer explanation method. Use when explaining an unfamiliar system, architecture, or open-source project to non-programmers, or when writing "why is it designed this way" content that must avoid AI-flavored prose, package names, and code details.
---

# Bluebook Writing

A methodology for writing design-reading content: explain *why a system is built the way it is*, not *what happens after you install it*. Every section uses a fixed two-layer skeleton — first a zero-terminology story, then the professional layer with formal names, mechanisms, boundaries, and costs.

## When to Use This Skill

- Explaining an unfamiliar architecture, framework, or open-source project to readers who do not write code.
- Writing "why is it designed this way" articles, books, or documentation.
- Rewriting AI-flavored drafts into plain language a non-technical reader can finish.
- Building a book or course where one running real-world story must carry every chapter.

## What This Skill Does

1. **Enforces the two-layer skeleton** — every section tells the same thing twice: a story with zero terminology, then the professional version that adds what the story cannot (formal names, mechanisms, boundaries, costs).
2. **Requires a transferable landing point** — every section ends with "where can I take this", so readers leave with a judgment they can reuse, not a summary.
3. **Runs a terminology firewall** — package names, file paths, code, and statistics never enter the main text; they go to an appendix.
4. **Uses one fixed analogy system** — one everyday story (a repair crew, a workshop, a kitchen) maps every technical term, so abstract ideas always land somewhere concrete.
5. **Applies machine-checkable style limits** — bold density, dash density, second-person frequency, banned filler phrases.

## How to Use

### Basic Usage

Ask for a section with:

> Write section N using the two-layer method: N.1 plain-language story (zero terms), N.2 professional layer (formal name, mechanism in bullets, boundaries, cost), N.3 glossary table of new terms only, N.4 two to four misconceptions (wrong first, then right), N.5 where this can be transferred.

### Advanced Usage

Provide a fixed analogy table before writing. Example mapping used by the book this skill was extracted from (DeepSeek Harness, read as a repair crew):

| Technical term | Everyday saying |
|---|---|
| model | the crew leader's brain (thinks, cannot touch anything) |
| harness | the whole crew |
| tools (read/write files, run commands) | the one who turns screws |
| session log | the one who takes notes |
| permissions and sandbox | the doorkeeper |
| agent loop | the foreman (looks, decides, acts, checks, decides again) |
| assembly manifest | today's shift roster |
| plugin | a temp worker |
| kernel | the head office at the very center |
| event bus / pub-sub | the bulletin board (anyone can post, everyone can see) |

Rules for new analogies: ① something everyone has seen in daily life; ② sayable in one word; ③ registered in the table.

### Section Structure (fixed, do not reorder)

```
N.1  Plain version    One everyday story carries the section's design point.
                      Zero technical terms allowed — one term is a failure.
N.2  Professional     Same content, now with terms: formal name, mechanism
                      (bullet list), applicable boundaries, costs.
N.3  Glossary table   "Plain saying ↔ professional term" — new terms only.
                      (Small sections may drop this.)
N.4  Misconceptions   2–4 items, each wrong understanding first, then the right one.
N.5  Transfer point   1–2 self-check actions the reader can run on their own project.
```

### The Core Test

Delete every package name from a paragraph. If something remains, it is design. If nothing remains, it is a code walkthrough — rewrite.

### Machine-Checkable Style Limits

- Section length 1,400–2,200 characters (Chinese), 2–4 diagrams per section.
- Bold ≤ 2 per thousand characters. Em-dash ≤ 2 per thousand.
- Second person ("you") ≤ 4 per section, ideally 0 — let the subject carry the sentence.
- Banned filler: 综上所述, 值得注意的是, 首先/其次/最后, 强大的, 革命性, 赋能, 众所周知, 不得不说, 简而言之.
- Paragraphs 2–6 sentences, alternating long and short.
- Every section must land on "why designed this way" and "where it transfers" — never end on a bare statement.

### Section Title Rules

1. The title is a question, not an answer.
2. The title contains a concrete object, number, or action.
3. Declarative titles only when the statement is counter-intuitive enough to create suspense.

## Example

**Input**: "Explain why DeepSeek Harness can have an empty kernel — the agent loop itself is a plugin."

**N.1 (plain version, zero terms)**: A repair crew where even the foreman is a temp worker. Pull the foreman out today, hire a new one tomorrow — the rest of the crew clocks in exactly as before, because nobody reports to the foreman personally; everyone reads the shift roster.

**N.2 (professional layer)**: Kernel vacancy. The kernel defines interfaces, not implementations. The agent loop is one plugin among many; replacing it touches only the assembly manifest. Boundaries: this buys reversibility at the price of indirection — the reader pays the complexity the implementer did not. Official quote placed here, not in N.1.

**N.3**: glossary table with 临时工 ↔ plugin, 排班表 ↔ assembly manifest.

**N.4**: wrong — "empty kernel means there is no kernel"; right — the kernel is the thinnest possible interface layer, which is why it can stay empty.

**N.5**: self-check — list your own system's components; ask which one, if pulled out, forces changes elsewhere. That answer is your real kernel.

## Tips

- Write N.1 first and freeze it. If a technical term sneaks in, the story is not done.
- N.2 must add what the story structurally cannot: boundaries, costs, and official wording. Never re-tell the story with new labels.
- Diagrams are the skeleton, not decoration. Each diagram gets a conclusion-style caption (a finding, not a topic) plus a paragraph tying it back to the section's argument.
- Run the banned-phrase and density checks mechanically before delivering; they are cheap and catch most AI flavor.
- Self-containment: no citation lists, no commit hashes, no source attributions in the main text. State the口径 in-line; push details to an appendix.

## Common Use Cases

- Design-reading books for open-source projects (the method behind the Blue Book series' first title, a 34k-character reading of DeepSeek Harness with 42 hand-drawn flow diagrams — see https://github.com/TobeMagic/deepseek-harness-bluebook).
- "Why it is built this way" engineering blog posts and internal architecture docs.
- Onboarding material for non-technical stakeholders.
- Rewriting AI-generated drafts into prose readers finish.
