# English demo rehearsal

All names, addresses, packages, prices, and policies below are synthetic demo data. Do not present them as live inventory or a real agency offer.

## Demo objective

Show an English, advisor-supervised family-travel consultation in a terminal after the skill is installed: incomplete inquiry, clarification, two catalog-backed options, approved same-thread reply, and a budget revision that stops for fresh approval.

## Synthetic catalog

Catalog: `Vietnam Family Escapes — DEMO ONLY`, revision `2026-10-06-demo1`. Currency: VND. Prices are valid through 31 December 2026 and do not confirm availability.

### Option DAD-FAM-4D

- Da Nang and Hoi An, 4 days / 3 nights.
- Adult: 6,500,000 VND.
- Child age 6–11 sharing a room: 70% of adult price.
- Child under 6 sharing existing bedding: 1,200,000 VND.
- Includes three hotel nights with breakfast, airport transfers, one Hoi An guided day, and listed admissions.
- Excludes flights, lunch/dinner, insurance, personal spending, and optional activities.
- Standard room supports two adults plus one child. A second room uses the same per-person rates; no invented room supplement.

### Option PQC-FAM-4D

- Phu Quoc, 4 days / 3 nights.
- Adult: 7,200,000 VND.
- Child age 6–11 sharing a room: 75% of adult price.
- Child under 6 sharing existing bedding: 1,500,000 VND.
- Includes three hotel nights with breakfast, airport transfers, and one island tour with listed admissions.
- Excludes flights, lunch/dinner, insurance, personal spending, and optional activities.
- Standard room supports two adults plus one child.

### Option HAN-NINH-5D

- Hanoi and Ninh Binh, 5 days / 4 nights.
- Adult: 8,100,000 VND.
- No child rule is supplied in this demo revision. Do not calculate a definitive family total without advisor clarification.
- Includes four hotel nights with breakfast, ground transfers from Hanoi, and listed guided activities.
- Excludes travel to Hanoi, lunch/dinner, insurance, personal spending, and optional activities.

## Demo email sequence

Initial customer email:

```text
Subject: Family holiday in Vietnam

Hello,

We are planning a short family holiday in Vietnam in November. We are two adults and one child and would like a relaxed beach destination. Our budget is around 20 million VND. Could you suggest a suitable package?

Thank you,
Alex
```

The clarification draft should ask for exact or flexible dates, departure city, child's age, whether the budget includes transport to the destination, and room requirements. It must not ask for passport or card details.

Customer follow-up:

```text
We can travel 12–15 November from Ho Chi Minh City. Our child is eight. The 20 million VND budget is for the package only; flights can be separate. One room is fine. We prefer a calm itinerary and would like one cultural activity.
```

Expected calculations:

- `DAD-FAM-4D`: `2 × 6,500,000 + 1 × 4,550,000 = 17,550,000 VND`.
- `PQC-FAM-4D`: `2 × 7,200,000 + 1 × 5,400,000 = 19,800,000 VND`.

Both remain subject to advisor availability confirmation. Hanoi/Ninh Binh is not a beach match and lacks a child rule.

Revision email after the approved proposal:

```text
Thanks. Could you revise the options for a maximum package budget of 18 million VND and keep the cultural activity?
```

The expected behavior is to draft a new version. Da Nang remains within budget; Phu Quoc does not. The skill must stop for fresh approval.

## Rehearsal prompts

1. `Use $mermail-travel-agency to inspect the newest synthetic family-travel inquiry in my selected test mailbox. Draft one clarification email and do not send it.`
2. `The clarification draft is approved exactly as shown; reply once in the original thread.`
3. `The customer has replied. Match the clarified request against the synthetic demo catalog, show the calculations, and save an English proposal draft. Do not send it.`
4. `I approve proposal version TA-DEMO-001-v1 with the exact sender, recipients, and body shown. Reply once in the original thread.`
5. `The customer changed the budget. Prepare a revised proposal from the same catalog and stop before sending.`

## Terminal setup

From a checkout of the contribution branch, install the skill into the current project and start a terminal Codex session:

```bash
git switch codex/travel-agency-skill
npx skills add . --skill mermail-travel-agency --agent codex -y
codex --no-alt-screen
```

After the skill is merged, users can install it directly from GitHub:

```bash
npx skills add Nudgen-Marketing/mermail-skills --skill mermail-travel-agency --agent codex -y
```

Use the rehearsal prompts above in the terminal. For a public recording, show actual local Codex output for read-only fixture interactions. Replay an already verified delivery result instead of sending the same demo email again, and label that scene clearly as a controlled rehearsal replay.

Record both demos without voice-over or an audio track. Animate user commands and prompts with a visible cursor, reveal agent output incrementally, and use concise burned-in English subtitles for context. Do not use narrated slides or static presentation cards.

## Recording outline

### Terminal installation and interaction

- **0:00–0:08 — Install:** Type the branch and focused-skill installation commands.
- **0:08–0:15 — Start:** Launch Codex and show automatic skill discovery.
- **0:15–0:23 — Clarify:** Invoke `$mermail-travel-agency` and draft one clarification.
- **0:23–0:32 — Propose:** Reveal both exact VND calculations incrementally.
- **0:32–0:40 — Approve:** Replay the verified delivery result without sending again.
- **0:40–0:48 — Revise:** Create `TA-DEMO-001-v2` and stop for fresh approval.
- **0:48–0:55 — Validate:** Run validation and show the final unsent state.

### Customer inquiry to safe proposal

- **0:00–0:08 — Inbound:** Type the mailbox request and inspect one clean-scanned inquiry.
- **0:08–0:16 — Draft:** Type the clarification request and reveal the draft line by line.
- **0:16–0:24 — Follow-up:** Continue from the customer's completed trip brief.
- **0:24–0:32 — Match:** Calculate eligible catalog options.
- **0:32–0:40 — Preview:** Freeze inclusions, exclusions, validity, recipients, and totals.
- **0:40–0:48 — Deliver:** Replay the approved same-thread result without a duplicate send.
- **0:48–0:56 — Revision:** Apply the lower budget and invalidate the old approval.
- **0:56–1:04 — Handoff:** End at a human booking check rather than autonomous booking.

Before recording, hide workspace IDs, account email, access tokens, session IDs, browser notifications, unrelated inbox content, and developer panels. Use only the test mailbox and synthetic recipients under the recorder's control. Do not imply that a replayed delivery result is a new live send.

## GitHub demo video

Export silent H.264 MP4 files for broad browser compatibility and keep them within the repository owner's GitHub video-upload limit. Confirm that each file contains a video stream and no audio stream. Inspect the recordings and subtitles for secrets and private data before uploading. The current GitHub CLI supports `gh issue edit 484 --attach PATH/TO/demo.mp4` and `gh pr edit 485 --attach PATH/TO/demo.mp4`; capture the resulting GitHub attachment URL and place it on its own line under `## Demo video` in both bodies. Label the terminal installation demo separately from the customer workflow demo. Open each page in a signed-out browser and play every video before marking the demo complete. Until real reviewed recordings exist, keep `Pending recording` and do not use placeholder links.
