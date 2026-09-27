---
name: "participant-context-cycle"
description: "Andrew's primary end-to-end participant loop: case context (Astalty export, emails, notes) -> Notion Context Layer delta -> Outlook gap analysis -> PACE verification -> Astalty follow-up tasks, delivered as one S34 import-ready pack. Use when Andrew hands over a participant's case context and wants the full cycle run, or says to resume a cycle from an existing pack."
---

# Participant context cycle (v2)

Context -> issue/task capture -> Astalty setup. Runs the component skills in order; each stays authoritative for its own stage. Output is **one pack** in the exact format of `references/pack-template.md` (example: `references/worked-example.md`). Attended only — this cycle reads mail and live PII, so it is never scheduled (S39; Gate A).

## Governance (whole cycle — unchanged from v1, never weakened)

- **Identity on NDIS number, not name.** Confirm a single match and cross-check the NDIS # before any write. STOP on ambiguity.
- **S34 / EU AI Act Art. 50.** Everything produced is an AI DRAFT — Andrew rewrites in his own voice before it reaches a record, participant, or provider. Never paste Claude output verbatim into a record.
- **Andrew is the actor and the only one who sends emails.** Create records/tasks only on his explicit go-ahead; do the first write of a batch hand-in-hand (screenshot the filled form for his OK), then run the rest and give a verified summary.
- **Plan here, build there.** Plan and verify in-session; hand bulk to Notion / import-ready files. Avoid heavy connector loads.
- **Balances & plan dates:** verify in PACE/Astalty and flag as point-in-time; never assert them from case notes. Astalty wins over Notion on conflict.
- Agents stay read-only on governance/instruction surfaces (S36); PACE is read-only; credentials are never entered.

## Pre-flight (do before Stage 1; record results in pack §0 and §7)

1. **Inputs present:** participant name **and NDIS #**; the case-context source(s) (Astalty notes export PDF/zip, xlsx task list, email thread, note); today's date. Missing NDIS # -> ask; do not proceed on name alone.
2. **Identity confirmed:** one participant, NDIS # matches across source, Notion page and (when reached) Astalty/PACE. Name collision or mismatch -> STOP.
3. **Existing pack?** If Andrew supplies or references a partly filled pack, go to **Resuming** below instead of starting over.
4. **Tool check — pick the mode per stage and write it into §0 "Sources used":**

| Stage | Needs | If unavailable (e.g. cloud session, no Chrome) |
|---|---|---|
| 1 Ingest | shell + `pdftotext` on disk | Ask Andrew for a smaller export or text copy; never load raw PDFs in context |
| 2 Context Layer | Notion connector (single read) | Andrew pastes the page's compile marker + section headings; pack still built |
| 3 Gap analysis | Microsoft 365 (Outlook mail + calendar) | Andrew supplies an exported thread list; else §3 marked `NOT RUN — no mail access` and a §7 item added |
| 4 PACE | Claude in Chrome + Andrew's live PRODA session | Andrew's portal screenshots (see Stage 4); else **handoff checklist**: each fact goes into §4 as `UNVERIFIED — verify in PACE (Route A/B)` and into §7 |
| 6 Astalty | Claude in Chrome + Astalty session | **Handoff checklist**: §6 drafts are the build sheet; §7 lists each task for Andrew to create and confirm on the Task Board |

Cloud-session pattern that worked (first live run): Stages 2 and 3 in parallel; Stage 4 from Andrew's screenshots; Stage 5 by a higher-reasoning pass; Stage 6 `NOT RUN` -> handed to a Claude-in-Chrome session running [[astalty-followup-task]].

## Stages — each has STOP conditions and an exit check

**1. Ingest context.** Process large PDFs on disk (per [[astalty-context-layer-sync]] steps 1–2). Extract logged tasks/actions (date, author, title), contacts, dates, open issues.
- STOP: a note appears to concern a different participant; source NDIS # differs from the confirmed one.
- Notes-export date = date *entered*, not event date — say so where it matters. The tasks export may have no NDIS column: identity there rests on name + title alignment with the notes; state that in §0.
- A note about another person (misfiled) is STOP-worthy: flag it for removal from the file; never carry its content forward.
- Exit: index built; record count + date span stated; logged-task list ready for Stage 3.

**2. Context Layer delta — [[astalty-context-layer-sync]].** Read the Notion page once; capture its **compile-through marker** (e.g. "notes #1–#381, to 11/09/2026"). Offer the cut as a structured choice (default: current plan period). Produce §1 Changelog + §2 insert blocks matched to the page's own sections. No bulk Notion edits via connector.
- STOP: no compile marker found (ask Andrew for the boundary — do not guess); page belongs to a different NDIS #.
- **Marker drift:** resolve the boundary by note number **and** date. If the marker's date ≠ note #N's date in the export, or the page already holds notes beyond #N (a top-up without a marker update), use the note-number boundary, tag each delta note `already reflected` or `new`, flag the drift in §1, and propose the new marker as `#1–#M (to DD/MM/YYYY HH:MM)`.
- A previous AI-compiled Context Layer pasted into the export as a note is reflected content, not new material; if it was sent externally verbatim, flag an S34 exception.
- Exit: §1 includes the compile-marker bump (#old -> #new, date); every §2 block names an existing target section.

**3. Outlook gap analysis (method).**
- **Window:** from the compile-marker date (Stage 2) to today, inclusive. Write it in §0.
- **Collect:** Outlook mail (sent + received) and calendar events in the window where the participant's name, NDIS #, nominee or known provider contacts (from the Context Layer "people & providers") appear. Read headers/snippets; open bodies only where needed.
- **Match** each comm to a logged Astalty task/note when all hold: date within **±3 days** (see Open Questions), same counterparty (person or organisation), same topic (funding / SA / provider / review / etc.).
- **Classify** every comm, one row each in §3:
  - **Matched** — a logged task/note covers it; name it in "matched task".
  - **Gap** — a coordination/funding action or commitment with no matching task. Say what action is owed.
  - **Not-actionable** — newsletter, auto-reply, FYI cc, duplicate in the same thread, clinical-only content (stays in the case file). Give the reason.
- **Also record:** the channels **not** searched (Outlook-only misses Teams / SMS / phone / Fieldy); a **reverse list** (logged tasks/notes with no Outlook trace); a **pre-window** list (relevant comms just before the window). A task still open in the tasks export -> check Outlook for evidence it was actually completed.
- STOP: mail access would require sending, forwarding or altering mail (read-only only).
- Exit: every in-window comm has exactly one status and a note; Gap count stated; not-searched channels named.

**4. PACE verification — [[pace-participant-lookup]].** For each Gap/issue that turns on a fact (diagnosis recording, funding available, plan- vs agency-managed, plan dates) verify read-only. Zoom to confirm cents. Record in §4 with verified-on date and point-in-time flag.
- STOP: Andrew not logged in (ask him to log in; never enter credentials); PACE NDIS # differs; any action control would need clicking; a recent "plan continued" notice (flag before relying on balances).
- **Portal labelling:** the plan may still be myplace-era (the myplace provider portal shows a banner that PACE plans can't be viewed there). Record per §4 row which portal was used — "myplace provider portal › View Plan" or "PACE my NDIS provider portal" — keeping the §4 heading "PACE Verification". "Still on myplace, not PACE" is a §5 Active Issue candidate.
- List what is **NOT VISIBLE** on the portal (e.g. diagnosis, funding periods, service bookings, FCA outcomes); those facts stay UNVERIFIED.
- **Screenshots** from Andrew are an acceptable input (cloud session, no browser): transcribe every figure, check spent + remaining = approved per category, and give every UNVERIFIED fact from Stages 1–2 a verdict: CONFIRMED / CONTRADICTED / NOT VISIBLE.
- Exit: every fact that a §6 task relies on is either verified in §4 or marked UNVERIFIED with a §7 item.

**5. Draft issues + tasks.** (a) Structural, non-transient findings -> §5 Active Issues. (b) One row per action -> §6 (priority prefix, participant + NDIS #, SC-L2, billable, owner, due, short description). Present compactly for Andrew to react.
- STOP: owner/SC of record unclear (Andrew vs Faye) — ask.
- Exit: every Gap in §3 maps to a §6 task or is explicitly declined in §3 note; Andrew has reacted to §6.

**6. Astalty task setup — [[astalty-followup-task]].** On explicit go-ahead only. First task hand-in-hand (screenshot the filled form for his OK), then the rest; confirm each on the Task Board and give a verified summary. Field mapping: §6 "Due" goes in the single date picker (labelled "Start time"); there is no Due or Period field. Paste the Stage 6 outcome block back into §7 of the pack (identity check, tasks created/confirmed, billable flags, existing open tasks left untouched, S34 rewrite still owed).
- STOP: no go-ahead; Astalty NDIS # mismatch; first-task screenshot not yet approved.
- Exit: §7 records each task as created + confirmed (or handed off).

**Deliver** the pack (plan here, build there) — see Pack delivery. Close with: note range covered, gap count, tasks drafted/created, open §7 items, and the reminder that it is an AI DRAFT to rewrite.

## Pack delivery

Deliver as `.md` (template §0–7) **and** `.json` in the import format of ark-tools `ark-context-pack.html` (Import JSON button). Validate by importing in headless Chromium and checking per-section row counts and the Gap/Matched/Not-actionable counts. Known schema gaps: channel has no email direction (use "Email" + `In:`/`Out:` prefix in summary); no section for the reverse, pre-window or NOT VISIBLE lists (carry them as §7 checklist items, in full in the `.md`); identity-confirmation text goes in "Other source(s)".

## Resuming a partly complete cycle

The pack is the state. Read §0 and §7, then find the first stage whose exit check fails:
- §1/§2 empty or no compile bump -> Stage 2. §3 empty or rows lacking status -> Stage 3 (reuse §0 window; extend "to" date to today and re-run only the new days).
- §4 has UNVERIFIED rows -> Stage 4. §6 rows not marked created in §7 -> Stage 6.
Re-confirm identity (NDIS #) on resume. Never re-create a task §7 marks created; re-check the Task Board first. Add a §1 changelog row for the resume date.

## Notes

- Keep clinical detail in the case file; the cycle stays on coordination/funding actions.
- Data-quality gotchas to flag (not rely on): placeholder contact emails, stale free-text vs structured fields, a participant listed once per role, a "plan continued" notice that may reset balances, notes by a prior SC filed under Andrew, misfiled notes.

## Open Questions for Andrew

Still open — the first live run used the defaults shown; confirm or change.
- Match tolerance for the gap analysis — default used: ±3 days.
- P1/P2/P3 mapping — default used: Urgent / Near-term / Watch (astalty-followup-task pattern).
- Pack also as a Drafting Bay row (S33)? — default used: file only.
- Gap-analysis channels: add Teams / Fieldy? — default used: Outlook only (not-searched channels stated in §3).
- Should plan-extension's Lead SC STOP-rule list (e.g. plan expiry within 30 days unconfirmed, provider red flag) also gate this cycle? — no default; not applied.
