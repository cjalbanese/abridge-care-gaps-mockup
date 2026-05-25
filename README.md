# Abridge Prospective Quality — Click-through Prototype

A 4-view HTML mockup of the proposed Care Gaps & Quality product for the Abridge PM case study response. Built to be demo-ready for the Loom walkthrough and the EPD interview.

## How to open

Just double-click `index.html` (or run `open index.html` from this directory). No server, no build step, no install — it's a single self-contained file.

```
open /Users/christopheralbanese/abridge-mockup/index.html
```

Tested in modern Chrome and Safari. Desktop-first (the mockup represents a clinician's Epic surface, not a phone).

## What's in it

Four views, navigable via the top nav bar:

1. **Pre-visit** — Dr. Garcia's morning schedule. Sarah Patel's row is expanded showing the open SPD care gap (Statin Therapy for Patients with Diabetes), why it's open, and that it's closeable in today's visit.
2. **In-visit** — The centerpiece. Live Abridge transcript on the left, auto-generating SOAP note on the right, and the single ambient nudge card appearing mid-conversation. Two CTAs: **Add to plan** or **Dismiss**.
   - **▶ Replay visit (live)** button at the top plays the entire visit in real-ish time (~43s at 1× speed) — transcript scrolls in line-by-line, SOAP note builds section-by-section, and the nudge card slides in with a subtle animation at exactly the moment Dr. Garcia would have wrapped without addressing the gap. Speed controls (0.75× / 1× / 1.5× / 2×) let you match the Loom pace you want.
   - **Show full state** snaps back to the fully-populated static view (default on page load).
3. **Post-visit** — The signed SOAP note with the statin prescription, the Linked Evidence panel showing the exact transcript turns that drove the documentation, and the **structured evidence card** showing the HEDIS SPD numerator being auto-emitted to Highmark BCBS as ECDS supplemental data. State toggle at the top lets you flip between **Nudge accepted** and **Nudge dismissed** to show both outcomes.
4. **Quality dashboard** — What the VP of Value-Based Care at the payvider sees. KPI strip, measure breakdown table, in-visit nudge conversion funnel, clinician trust signals, cost displaced.

## Suggested Loom walkthrough (10 min max)

| Time | View | What to emphasize |
|------|------|-------------------|
| 0:00–1:00 | Intro | Why prospective: retrospective vendors find gaps after the visit; Abridge can close them during it |
| 1:00–2:00 | **View 1** | Gap comes from the payer (Highmark) via clearinghouse rail. Already attributed. Clinician sees "1 gap · closeable today" — not a checklist |
| 2:00–5:00 | **View 2** | Hit **▶ Replay visit (live)** at 1.5× or 2× speed so the audience watches the transcript scroll, the SOAP note build, and the nudge slide in mid-conversation at 14:23. Then click "Add to plan" → goes to View 3. Return and click "Dismiss" → also goes to View 3 (dismissed state). Note: it's not a modal, not a BPA |
| 5:00–7:30 | **View 3** | The magic moment: Dr. Garcia wrote zero quality forms but the SPD numerator is automatically packaged as ECDS-compliant supplemental data with audio + transcript provenance. Toggle states to show both outcomes |
| 7:30–9:30 | **View 4** | The buyer's view. SPD closure rate ↑15.5 pts QoQ, $4.2M projected QBP impact, 82.6% nudge precision, $251K cost displaced. This is what the payvider VBC VP signs the check for |
| 9:30–10:00 | Close | Reiterate: this is v1, point-of-care-closable measures only, ambient-first, payvider-first GTM |

## The example patient

**Sarah Patel** — 54F, Type 2 diabetes, hypertension, hyperlipidemia. On metformin, lisinopril, ASA. **No statin** on med list, no documented intolerance. A1c 7.2 (improving to 7.0 in this visit). LDL 138. Payer: Highmark BCBS (MA). PCP: Dr. Maria Garcia at UPMC Internal Medicine.

She's a clean SPD candidate. Picked because the closure is a single prescription — a clinician audience grasps it instantly, and the gap genuinely is closeable in the room rather than requiring a separate lab order, referral, or screening procedure.

## Visual design choices

- **Color:** white surfaces, near-black text, **red accent** matching Abridge's actual brand identity (not the green I initially assumed). Green is used only for "gap closed" success states.
- **Typography:** Inter (Abridge's custom Display face is marketing-only; UI is standard sans-serif).
- **Layout pattern:** two-panel split (transcript + note) matching Abridge's actual Linked Evidence pattern in Epic Hyperdrive.
- **Epic chrome:** thin top bar showing system/clinician identity + patient header bar on visit views. Just enough to read as "Abridge Inside Epic" without recreating Epic.
- **Button sizing:** ≥44px tall (accessibility convention).
- **The nudge card:** single, dismissible, inline in the existing Abridge note panel. Not a modal. Not an overlay. The whole point is that it's ambient.

## What's explicitly NOT in the mockup

- Real audio playback (visual timestamp marker only).
- Real EHR/FHIR integration. The "Highmark BCBS ECDS feed" status is illustrative.
- All five HEDIS measures with real data. SPD is the worked example; the other measures on the dashboard are plausible-looking but illustrative.
- Mobile responsive layout. This is a desktop clinician surface.
- Cross-browser polish beyond modern Chrome/Safari/Firefox.
- Backend / data persistence.

## Files

```
abridge-mockup/
├── index.html      # the entire mockup (single self-contained file)
└── README.md       # this file
```

To share: zip the directory and email, or drop `index.html` into a sandbox like CodeSandbox / Glitch / a Vercel static deploy if you want a shareable URL.
