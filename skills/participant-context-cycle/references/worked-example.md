# Worked example — fictional, de-identified

Everything below is invented to show the format. The participant, NDIS number, providers, contacts and figures are not real. The shape follows `pack-template.md` exactly.

Scenario: a cloud session with Outlook and Notion access but no Chrome, so PACE and Astalty stages ran as handoffs.

---

## 0. Header

> **AI DRAFT — S34.** Compiled by Claude at Andrew's direction. Not a record. Andrew rewrites in his own voice before anything reaches Notion, Astalty, a participant or a provider (EU AI Act Art. 50). Balances and plan dates are point-in-time.

- **Participant:** Sample, Jordan
- **NDIS #:** 43XXXXXXX (identity confirmed against: Astalty export header, Notion Context Layer)
- **Cycle date:** 25/09/2026
- **Window:** 01/09/2026 (Context Layer compile marker) – 25/09/2026
- **Sources used:** Astalty notes export (2 parts, 214 pages); Notion Context Layer (marker "notes #1–#118, to 01/09/2026"); Outlook mail + calendar; PACE — handoff (no Chrome); Astalty — handoff (no Chrome)

## 1. Changelog

| Date | Source | Change |
|---|---|---|
| 25/09/2026 | Notion | Bump compile marker: "notes #1–#118, to 01/09/2026" -> "notes #1–#127, to 24/09/2026" |
| 08/09/2026 | Astalty note #121 | Add new OT provider row (Example Allied Health) to People & providers |
| 15/09/2026 | Email in | Add timeline entry: service agreement renewal sent by support worker provider |

## 2. Context Layer insert blocks

| Target section | Insert text |
|---|---|
| People & providers | Example Allied Health — OT, started 08/09/2026. Contact: intake team (email on file; flagged placeholder, verify). |
| Timeline — current phase | 15/09/2026 — Demo Care Services sent a renewed service agreement for review; not yet signed. |
| Active issues | Home-safety OT report due; funding line to be confirmed in PACE before booking the assessment. |

## 3. Gap analysis

| Date | Channel | Counterparty | Summary | Matched task | Status | Note |
|---|---|---|---|---|---|---|
| 08/09/2026 | Email out | Example Allied Health | Referral for OT assessment | OT Referral-NDIS (09/09) | Matched | Task logged next day, within ±3 |
| 15/09/2026 | Email in | Demo Care Services | Renewed service agreement for review | — | Gap | Action owed: review SA against plan and return comments |
| 18/09/2026 | Calendar | Nominee (parent) | Phone check-in booked 22/09 | Check-in (22/09) | Matched | |
| 19/09/2026 | Email in | Sector newsletter | NDIS pricing update | — | Not-actionable | General newsletter, not participant-specific |
| 23/09/2026 | Email in | Example Allied Health | Asks whether IDL funds are plan-managed | — | Gap | Action owed: confirm management type (see §4) |

Gaps: 2 · Matched: 2 · Not-actionable: 1

## 4. PACE Verification

| Verified-on date | Fact | Value | Where verified | Point-in-time flag |
|---|---|---|---|---|
| UNVERIFIED | IDL (Capacity Building) available balance | — | PACE Route B > Budget (handoff) | Yes — point-in-time |
| UNVERIFIED | IDL management type (plan- vs agency-managed) | — | PACE Route B > Funded supports (handoff) | n.a. |

## 5. Active Issues

- **OT funding route unconfirmed** — the OT provider cannot be booked against IDL until the management type is confirmed; if agency-managed, a plan-managed variation is needed first. Closes when §4 rows are verified.

## 6. Task drafts

| Priority | Task name | Participant | NDIS # | Support item | Billable | Owner | Due | Short description |
|---|---|---|---|---|---|---|---|---|
| P1 | P1 – Funding-IDL check | Sample, Jordan | 43XXXXXXX | SC-L2 | Y | Andrew Heynes | 29/09/2026 | Confirm IDL balance and management type in PACE; reply to OT provider. |
| P2 | P2 – Service Agreement-Review | Sample, Jordan | 43XXXXXXX | SC-L2 | Y | Andrew Heynes | 03/10/2026 | Review renewed SA from Demo Care Services against plan; return comments. |

## 7. Handoff / next steps

- [x] Pre-flight: identity confirmed on NDIS # (export header = Notion page)
- [x] Stage 2 exit: compile marker bumped in §1
- [x] Stage 3 exit: every comm classified
- [ ] Stage 4 exit: verify both §4 rows in PACE Route B (no Chrome this session)
- [ ] Stage 5 exit: Andrew reacted to §6
- [ ] Stage 6: create P1 task hand-in-hand (screenshot approved), then P2; confirm both on Task Board
- [ ] Andrew rewrites §1–§6 wording in his own voice before it lands (S34)
