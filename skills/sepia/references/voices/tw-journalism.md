# Voice profile — Taiwan long-form journalism (built-in, experimental, professional routes only)

Status: a built-in voice profile for the experimental interface in `voice-skills.md`. It loads only when the user opts in with the exact phrase `apply the Taiwan journalism voice` or 「套用台灣深度報導 voice」, optionally followed by a shape name from the tables below (for example 「，場景導入型」). It never loads on the fiction route, declares no intent triggers, and produces no `Voice fit:` line (professional-route Voice fit is tracked in issue #227). Everything in `voice-skills.md` governs: sepia's architecture decisions first (here, `domains/journalism.md`), 3–5 voice moves per piece, uniformity findings at full strength, venue precedence, never invent. When a shape is named, moves come from that shape's table plus the cross-shape table; when none is named, sepia picks the shape from the decision table and says which.

**Closing line (this body's own rule).** A write or recreate under this voice ends with one line, outside the prose: `Voice applied: tw-journalism/<shape> — moves: <3–5 move names>`. Review and refactor stage 1 print their normal report and add nothing; this line exists so a reader can check the selection rule without re-deriving it.

Evidence tiers, kept apart: (T) one private human-side measurement of Traditional Chinese long-form journalism, ledger `ZH-NEWS-CORPUS-2026`, whose numbers live only in `languages/zh.md` §1b; (C) a close reading of 169 articles from the same corpus, cited as counts of 169 (a sample size, not a corpus size); (I) Sepia inference. There is no author-testimony tier and no machine-side measurement: nothing here says what a machine does, only what this register does. The corpus is about two thousand articles from one unnamed Taiwanese publication, spanning about ten years, human text only, not distributed. No sentence of any article appears in this file; every example is synthetic.

## The precondition is reporting

Every shape below needs facts the writer actually has. A scene needs scene facts (who, where, what they were doing, when); a number needs its comparison basis; a two-sided layout needs two sides on the record; a timeline needs timestamps. Under this voice the specificity rules stay at full strength (SKILL.md "Never invent specifics"; `professional-pass.md` check 5): a missing fact is a TODO or a question to the user, never a sentence. A shape whose precondition is not met is not chosen.

## Choosing a shape

| What the reporting has | Shape | Precondition that must hold |
|---|---|---|
| A place someone can stand in, and a person doing something there | 場景導入 (scene lead) | scene facts with a time of day |
| A result that happened today or this week | 倒金字塔 (inverted pyramid) | date, actor, outcome, count |
| One person whose time span carries the piece | 人物弧線 (person arc) | at least three dated episodes |
| A policy or number gap to take apart | 論證式 (argument) | two parties on the record |
| A dataset the reporter built or obtained | 數據驟動 (data-led) | source, method, a baseline |
| One speaker whose words are the content | 問答 (Q&A) | a transcript |
| Three or more standpoints or sites | 多線並置 (parallel threads) | comparable material per thread |
| A reconstructable sequence of moments | 時間軸 (timeline) | timestamps from documents |
| An image that can hold two paragraphs unnamed | 懸念揭露 (reveal) | rare (C: 1 of 169 pure); use once |

Mixed pieces (C: 98 of 169) pick one spine and borrow at most one move from a second shape.

## Shape tables

Columns: Move / Source / Sepia check it maps to (I unless marked) / Known cost.

### 場景導入 (scene lead)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| Open on one person doing one small thing in one place; the first number arrives in the third paragraph or later | C: scene or person lead in the majority of 169; T: first-paragraph digit share (zh.md §1b) | `discourse-pass.md` §4 machine opening; `journalism.md` rule 1 | Answer-first domains (postmortems, release notes) win by venue precedence; this move is not used there |
| Cut sections by situation (a room, a shift, a road), not by numbered problems | C: 7 of the 9 pure scene pieces | `professional-pass.md` check 3; `journalism.md` rule 2 | Argument-heavy material scatters when cut by situation; use only on the scene sections of a mixed piece |
| Each section enters through the scene and exits through the institution; the institutional sentences do not outnumber the scene sentences | C: scene pieces | `discourse-pass.md` §1 QUD | Density (check 2) will report scene detail; `journalism.md` rule 8 says which detail is information |
| End by returning to the opening person or object at a later moment; the last sentence does not comment | C: endings return to person 20 / suspended 19 of 169; summary 7 of 169 | `professional-pass.md` check 7 | When the reader needs the outcome, an open ending is a missing fact, not a style choice |

### 倒金字塔 (inverted pyramid)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| The first sentence holds who, when, what, how many; only then walk the clock | C: 6 pure, 22 as a component | `journalism.md` rule 1 (standfirst register); domains answer-first | Long first sentences with many commas trip `style-pass.md` §5 if the rest of the piece is uniform |
| Write each provision in full every time (date, amount, deadline); never "as above" | C: inverted-pyramid pieces | check 5 specificity | check 2 will count repeated full names; use in provision-dense sections only |
| Bridge from the main scene to the outside with a run of captions or times, then re-enter with a count and a clock time | C | check 3 | None beyond the general slack rule |
| Updates go in a dated block after the body; the body is not rewritten | C; `journalism.md` rule 6 | check 7 | An update that restates the body is residue; only new facts go there |

### 人物弧線 (person arc)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| Build character from several concrete episodes; no character adjectives | C: 9 pure, 14 component | `style-pass.md` §1 row 5 specificity; §3 inflation adjectives | None |
| After a quotation, one gesture or expression, not an emotion adverb | C: about half of 169 notes record this; T: manner adverb near zero (zh.md §1b) | `narrative-pass.md` §5 emotion mode (named → behavioural); zh.md §2 row | A gesture after every quotation is a metronome; three or four per piece |
| At the emotional peak let the quotation stand whole; do not cut it into fragments | C | rubric Group E dialogue proportion (calibration, not a target) | Long quotations raise the quotation share; keep the count low elsewhere |
| End on the person's own words or an everyday action, without comment | C: endings quotation 47 / return to person 20 of 169 | check 7 | Same as the scene-lead ending cost |

### 論證式 (argument)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| End a paragraph on a question; the next paragraph answers it with a source's data or words, never the reporter's | C: paragraph-end questions are the norm; T: question-ending paragraphs common (zh.md §1b) | `discourse-pass.md` §1 QUD; `journalism.md` tells (self-answered question) | One question per section; more reads as rhetoric |
| Put two or more experts in one section and let one disagree on the record | C: 9 of 11 pure argument pieces | check 4 stance as `journalism.md` rule 7 reads it | Needs two parties on the record; otherwise not available |
| Every number carries a comparison or a conversion; no figure stands alone | C; `journalism.md` rule 4 | check 5, check 6 | None |
| One collecting sentence per section at most, and it names the disagreement rather than settling it | C | check 7 | Two per section is a template |

### 數據驟動 (data-led)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| After each absolute figure, a bracket or clause with the rate, the change, or the prior period | C: 17 of 20 pure data pieces | check 6 | Bracket density in non-data venues reads as over-annotation; one conversion per paragraph |
| Convert unfamiliar units into a referent the reader already knows | C | check 5; `style-pass.md` §1 row 5 | The referent is itself a fact with a source |
| State the method in the body (source, definition, limits) in the first person plural or the outlet's third person | C: about half of data notes | check 5; `journalism.md` rule 4 | Reads as a paper outside data pieces; only when the reporter built the dataset |
| After each figure, one plain-language reading from someone on the ground, not a reporter verdict | C; T: attribution-free quotation share (zh.md §1b, a length proxy) | check 7; `narrative-pass.md` §5 (judgment given to a person) | A quotation after every figure is a metronome; one per section |
| Sections by indicator or region, same skeleton, different content; no connective between them | C: data notes | `style-pass.md` §4 (connectives, here used less); check 9 | Identical skeletons are a uniformity risk; the difference must be in content |

### 問答 (Q&A)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| The preamble carries all background; the exchange repeats none of it | C: 8 pure, 10 component | check 3 | None |
| Keep the speaker's repetition, hesitation, code-switching, self-answering | C: Q&A pieces; `journalism.md` rule 3 | `style-pass.md` §1 row 1 (will flag as awkward; the quotation is load-bearing) | Spoken texture will be reported by the style scan; report it as the voice's cost |
| The reporter's checks or additions go in brackets or an editor's note inside the quotation; the words are not rewritten | C | SKILL.md quoted-material guardrail | None |
| One question per turn; no bundled sub-questions | C | check 8 templatedness | None |

### 多線並置 (parallel threads)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| State the format once ("the following is in each person's own words"); no per-thread reporter lead-in | C: 6 pure, 11 component | check 8 | None |
| Equal room per thread; no thread pre-declared the main one | C | check 4 as `journalism.md` rule 7 reads it | Equal length is a uniformity risk; vary inner shape |
| Switch threads with a subhead, never with 「另一方面」 | C; `journalism.md` rule 2 | zh.md §2 connective stacking | None |

### 時間軸 (timeline)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| Quote the original notice or message and stamp its time; let the reader compute the gap | C: 22 as a component | check 5; `domains/postmortems.md` rule 1 | Quoting documents risks long verbatim runs; cut to what the reader needs |
| Record throughout, judge only in the last section | C | check 4, check 7 | Rarely carries a whole piece (C: 1 pure) |

### 懸念揭露 (reveal)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| Describe the image without naming it for two paragraphs, then a question, then the reveal | C: 1 pure, 2 component | `discourse-pass.md` §4 | A fiction device; once per piece at most, and only when the image is a reported fact |

### Cross-shape moves (usable with any spine)

| Move | Source | Sepia check | Known cost |
|---|---|---|---|
| Two registers: the standfirst gives the result, the first body paragraph places the reader | C: 20+ notes record the split; `journalism.md` rule 1 | `discourse-pass.md` §4 | None |
| Subheads switch; paragraphs do not open on connectives | C; T: 「此外」「然而」 single use register-normal, chains are §2 (zh.md §1b, §5) | zh.md §2; `journalism.md` rule 2 | None |
| A paragraph-end question answered by the next speaker | C: the norm; T (zh.md §1b) | QUD; `journalism.md` tells | One per section |
| The reporter's first person only for method, steering a source, or recording a silence | C: three fixed uses; T: first-person rate falling across eras (direction only) | `journalism.md` rule 5 | Any other first person is stance without reporting |
| A dated update block instead of edits to the body | C; `journalism.md` rule 6 | check 7 | Only new facts |
| No summary ending: stop on the last fact, quotation, person, or open question | C: 7 of 169 summary endings; T: 「總而言之」 0 per 100k (zh.md §1b) | check 7 | When the venue needs the outcome, end on the outcome as a fact |

## Register defaults

Sentence length, punctuation, quotation marks and connective rates for this register are in `languages/zh.md` §1b, the single canonical table; this body repeats none of them. In English journalism none of this is measured; the moves still apply as inference, the numbers do not.

## Voice fit

None on professional routes in this version (#227). The registry entry in `references/voices/registry.md` documents the opt-in only.

## Worked example

Synthetic facts (approved 2026-09-16; nothing else may be used, and any fact missing from this list is a TODO): 2026-03-04, 14:02 to 14:47 (UTC+8); an unnamed regional hospital emergency department in northern Taiwan; the retry queue had no jitter, 412 resends landed inside one 200 ms window, downstream services rate-limited each other; the cause was found at 14:41 and `RETRY_JITTER=full` was set at 14:47; the triage nurse (role only) clipped three paper triage slips to the whiteboard at 14:05 and kept triaging on paper; one synthetic quotation from the nurse, written for this example: 「電腦轉圈，我就先用紙。」; baseline about 3 resends per minute in a normal hour; the on-call platform engineer (role only) said the queue's default had never been reviewed; the default was changed for all queues on 2026-03-06.

Before (synthetic, written to carry the register's departures):

> 本文將探討一起發生在北部某區域醫院急診的系統事故。2026年3月4日下午，該院的掛號與檢傷系統突然變得非常緩慢，值班護理師無奈地表示：“系統一直轉圈圈，我們完全沒辦法作業。”值得注意的是，事故的根本原因——重試佇列缺乏抖動機制——導致在極短時間內產生了大量重複請求，進而引發下游服務相互限流的連鎖反應。技術團隊隨後迅速地進行了排查，並在當天下午成功地修復了問題。總而言之，這起事故凸顯了系統韌性的重要性，也提醒我們在設計重試機制時必須更加謹慎。

After A — 場景導入 (moves: open on a person; scene in, institution out; no summary ending):

> 3 月 4 日下午 2 點 05 分，北部一間區域醫院的急診，值班護理師把三張紙本檢傷單夾到白板上，之後的分級改用手寫。「電腦轉圈，我就先用紙。」
>
> 電腦轉圈的原因在急診之外：院內系統的重試佇列沒有設 jitter，一批失敗的請求在 200 毫秒內重送了 412 次，而平時每分鐘大約只有 3 次；下游服務於是互相限流。
>
> 值班平台工程師在 2 點 41 分找到原因，說這個佇列的預設值從來沒有人檢視過。2 點 47 分，`RETRY_JITTER=full` 設上。
>
> 3 月 6 日，所有佇列的預設值都改了。
>
> Voice applied: tw-journalism/場景導入 — moves: open on a person, scene in institution out, no summary ending

| Change | Move | Check |
|---|---|---|
| 「本文將探討…」 deleted; a time, a place, a person and a recorded action open the piece | Open on a person | `discourse-pass.md` §4; `journalism.md` tells row 1 |
| 「無奈地表示：“…”」 → the recorded action, then the approved quotation in 「」, no attribution verb, no adverb | (register default; `journalism.md` rule 3) | zh.md §2 manner adverb; §1b attribution rows |
| 「——…——」 paired insertion → one plain sentence carrying 412, 200 ms and the 3-per-minute baseline | Scene in, institution out | check 5; zh.md §1b paired-dash row |
| 「非常」「迅速地」「成功地」 deleted | (register default) | zh.md §1b, §2 |
| 「總而言之…重要性…謹慎」 → the last dated fact | No summary ending | check 7 |

Known cost and what the blind review taught: the shape's fourth move, return to the opening person or object at a later moment, is not used, because the approved fact list has no later whiteboard fact; an earlier draft returned to the same 2 點 05 分 moment and the declared-voice review correctly reported it as density, not as the move. Two drafts before that added a gesture and a closing count that were in no fact list, and a review caught both under check 5; one draft wrote 「他」 for an engineer the facts give only by role, caught the same way. The precondition section exists for exactly these.

After B — 數據驟動 (moves: figure with comparison; method in the body; reading from someone on the ground; no summary ending):

> 200 毫秒內 412 次重送。3 月 4 日下午 2 點 02 分起，北部一間區域醫院急診背後的系統把同一批失敗請求連續重送；平時一小時裡每分鐘大約 3 次，這 200 毫秒裡的量相當於平時兩個多小時的總和。
>
> 這個數字來自事故記錄的重試計數。沒有設 jitter 的重試佇列會把所有重送壓進同一個時間窗；下游服務對彼此啟動限流，2 點 41 分才找到原因。
>
> 急診端的值班護理師說：「電腦轉圈，我就先用紙。」2 點 05 分起，她把三張紙本檢傷單夾上白板。
>
> 2 點 47 分 `RETRY_JITTER=full` 設上，事故歷時 45 分鐘。值班平台工程師說，這個佇列的預設值從來沒有人檢視過；3 月 6 日，所有佇列的預設值都改了。
>
> Voice applied: tw-journalism/數據驟動 — moves: figure with comparison, method in the body, reading from the ground, no summary ending

| Change | Move | Check |
|---|---|---|
| 412 and 200 ms lead, with the 3-per-minute baseline and the "two hours" conversion (412 ÷ 3 ≈ 137 minutes, arithmetic on approved facts) | Figure with comparison | check 6 |
| 「這個數字來自…」 as its own paragraph | Method in the body | check 5 |
| The nurse's words after the figures, not a reporter verdict | Reading from the ground | check 7 |
| 45 minutes computed from 14:02–14:47; ending on the 03-06 change | No summary ending | check 7 |

Known cost of After B: the conversion sentence is the kind of arithmetic that check 6 accepts only when both inputs are sourced; here both are in the approved list.

After C — 調查追蹤 (argument spine with a timeline component; moves: question answered by the next speaker; two parties on the record; timestamps from the record; update block):

> 3 月 4 日 14:02，北部一間區域醫院急診背後的系統開始把失敗的請求重送。14:41 才找到原因。中間的 39 分鐘，誰知道發生了什麼？
>
> 事故記錄先回答：重試佇列沒有設 jitter；200 毫秒內同一批請求重送 412 次，平時每分鐘大約 3 次；下游服務對彼此限流。
>
> 急診端的值班護理師 14:05 就把三張紙本檢傷單夾上白板。「電腦轉圈，我就先用紙。」
>
> 值班平台工程師的說法是另一面：這個佇列的預設值從來沒有人檢視過。14:47，他把 `RETRY_JITTER=full` 設上。
>
> 更新（3 月 6 日）：所有佇列的預設值已改。
>
> Voice applied: tw-journalism/論證式 — moves: question answered by the next speaker, two parties on the record, timestamps from the record, update block

| Change | Move | Check |
|---|---|---|
| 「本文將探討」 → two timestamps and a question the record answers in the next paragraph | Question answered by the next speaker | `discourse-pass.md` §1; `journalism.md` tells (self-answered question) |
| The nurse and the engineer each get their own paragraph and their own words | Two parties on the record | check 4 as `journalism.md` rule 7 reads it |
| 14:02 / 14:05 / 14:41 / 14:47 stamped from the record | Timestamps from the record | check 5; `domains/postmortems.md` rule 1 |
| 「總而言之…」 → a dated update line | Update block | check 7; `journalism.md` rule 6 |

Known cost of After C: the opening question is answered by the record rather than by a person; the shape's fuller form has a source answer it.

## Grounding

Blind review of After A (the version printed above, prose only, without its `Voice applied:` line) by a fresh executor (Claude Opus 5) on the professional route, 2026-09-16, once with the voice declared by the exact phrase and once without. Both runs loaded `domains/journalism.md`; only the declared run loaded `voice-skills.md` and this body. Neither run printed a `Voice fit:` line (professional route, #227), as specified.

- Declared: `Passed: 1–10`; `Failed:` only `discourse-pass.md` §1 (QUD sequence "what happened → why → who fixed it when → afterwards" read as a linear interview; the first sentences of the four paragraphs form a clean outline). Style scan: one hedged candidate for connective stacking inside one sentence, counted as register-normal. Rhythm: sentence lengths 55/11/70/32/24/17 characters, no run of three near-equal sentences, the uniformity row did not fire. `Verdict: isolated hits → ship`. The voice's documented cost (scene detail under check 2) was not listed as a defect.
- Undeclared: the same discourse §1 finding, plus `#5 Specificity` (the causal bridge from the emergency department to the retry storm is stated in the reporter's voice before the engineer appears; no year; the 14:02 start is missing) and `#2 Density` in the reverse direction (about 210 characters against a 400-character brief, with the missing facts silently omitted instead of left as TODOs). `Verdict: isolated hits → refactor`.

What the pair shows: with the voice declared the review stops treating the venue's scene detail as filler and reports the shape's real weakness, a linear question order; without it the same text collects specificity and density findings that are about missing facts, which is the correct reading for a text with no declared shape. Three earlier drafts of After A were reviewed the same way and failed check 5 for a gesture, a closing count and a pronoun that were in no fact list; those drafts are gone and the lesson is recorded under the worked example. The write arm (`/sepia:sepia-write` on the approved fact list with the phrase) loaded this body, produced a four-paragraph piece with every fact traceable to the list, listed four TODOs for facts it did not have, and ended with `Voice applied: tw-journalism/場景導入 — moves: open on a person, sections cut by situation, scene in institution out, return to the object`. One worked example and one write, not measured evidence.
