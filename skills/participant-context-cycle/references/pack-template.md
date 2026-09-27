# Participant context cycle — pack template

Use this exact structure. Keep headings, section numbers, order and table columns unchanged (a companion HTML tool parses them). Fill every section; if a section has no content write `None this cycle.` or, if a stage could not run, `NOT RUN — <reason>` and add a §7 item. Dates are DD/MM/YYYY.

---

## 0. Header

> **AI DRAFT — S34.** Compiled by Claude at Andrew's direction. Not a record. Andrew rewrites in his own voice before anything reaches Notion, Astalty, a participant or a provider (EU AI Act Art. 50). Balances and plan dates are point-in-time.

- **Participant:** <Surname, First>
- **NDIS #:** <9 digits> (identity confirmed against: <source / Notion / Astalty / PACE>)
- **Cycle date:** <DD/MM/YYYY>
- **Window:** <from DD/MM/YYYY (Context Layer compile marker)> – <to DD/MM/YYYY>
- **Sources used:** <e.g. Astalty notes export (n parts, n pages); Astalty tasks export (NDIS column: yes/no); Notion Context Layer (marker "notes #1–#N, to DD/MM/YYYY"); Outlook mail + calendar; portal named explicitly — "PACE my NDIS provider portal" or "myplace provider portal › View Plan" (live / Andrew's screenshots) — or "handoff" per stage>
- **Channels not searched:** <e.g. Teams, SMS, phone, Fieldy>

## 1. Changelog

| Date | Source | Change |
|---|---|---|
| <DD/MM/YYYY> | <Astalty note #n / email / PACE / Notion> | <exact change to make on the page, incl. compile-marker bump #old -> #new as "#1–#M (to DD/MM/YYYY HH:MM)"; flag any marker drift; tag delta notes "already reflected" / "new"> |

## 2. Context Layer insert blocks

| Target section | Insert text |
|---|---|
| <existing page section, e.g. People & providers / Timeline — current phase / Active issues / Funding> | <ready-to-insert text, draft wording> |

## 3. Gap analysis

| Date | Channel | Counterparty | Summary | Matched task | Status | Note |
|---|---|---|---|---|---|---|
| <DD/MM/YYYY> | <Email in / Email out / Calendar> | <person, organisation> | <one line> | <Astalty task/note name or "—"> | <Matched / Gap / Not-actionable> | <reason; for Gap, the action owed> |

Gaps: <n> · Matched: <n> · Not-actionable: <n>

**Reverse list** (logged tasks/notes with no Outlook trace): <items or "None">
**Pre-window** (relevant comms before the window): <items or "None">

## 4. PACE Verification

| Verified-on date | Fact | Value | Where verified | Point-in-time flag |
|---|---|---|---|---|
| <DD/MM/YYYY or UNVERIFIED> | <e.g. IDL available balance; or a Stage 1–2 fact with verdict CONFIRMED / CONTRADICTED / NOT VISIBLE> | <value, exact cents> | <portal used — "PACE my NDIS provider portal" or "myplace provider portal › View Plan" — > tab; "(screenshot)" if from Andrew's screenshots> | <Yes — point-in-time / n.a.> |

Heading stays "PACE Verification" even when the source is myplace. **NOT VISIBLE on portal:** <e.g. diagnosis, funding periods, service bookings, FCA outcomes — these stay UNVERIFIED>

## 5. Active Issues

- **<Issue title>** — <structural, non-transient finding; why it matters; what would close it>

## 6. Task drafts

| Priority | Task name | Participant | NDIS # | Support item | Billable | Owner | Due | Short description |
|---|---|---|---|---|---|---|---|---|
| <P1/P2/P3> | <P1 – Theme-Topic> | <Surname, First> | <NDIS #> | SC-L2 | <Y/N> | <Andrew Heynes / SC of record> | <DD/MM/YYYY> | <what/why, one or two lines> |

Astalty Create Task has one date field (the picker labelled "Start time") and no Due date or Period field: "Due" maps to it. Duration is left at 0; Completed unchecked; no documents unless §7 says otherwise.

## 7. Handoff / next steps

- [ ] Pre-flight: identity confirmed on NDIS # (<how>)
- [ ] Stage 2 exit: compile marker bumped in §1
- [ ] Stage 3 exit: every comm classified
- [ ] Stage 4 exit: every relied-on fact verified or listed here as UNVERIFIED
- [ ] Stage 5 exit: Andrew reacted to §6
- [ ] Stage 6: first task created hand-in-hand (screenshot approved), rest created and confirmed on Task Board
- [ ] Andrew rewrites §1–§6 wording in his own voice before it lands (S34)
- [ ] <any handoff item: e.g. "Verify X in PACE Route B (no Chrome this session)">
- [ ] <reverse-list / pre-window / NOT VISIBLE items — one line each (the JSON import has no section for them)>
