# CODEX_BRIEF — MANB109 Creativity and Innovations

Generation instructions for this workspace. Work the steps **in order**; each one consumes
the output of the previous. Do not skip ahead — later artefacts are keyed off IDs fixed
earlier.

---

## Non-negotiable rules

1. **`109.N` is the CO id convention.** Never emit `CO1`, `CO2`, … Every `target_cos` /
   `target_co_ids` value must be one of `109.1`, `109.2`, `109.3`, `109.4`, and must match
   `course_profile.json → course_outcomes[].co_id` exactly.
2. **Never invent prescribed syllabus.** Unit titles, unit topics, CO statements and the
   hands-on activities come from the university. If a unit is missing, stop and ask —
   do not fill the gap.
3. **`schema_version` is `1.3.0`** on every JSON file that carries one.
4. **Institution is `Dr. Babasaheb Ambedkar Marathwada University`** everywhere. Never
   `National Business School`.
5. **This is a 0:0:2 practical course.** No lecture hours exist. Every session is a
   120-minute studio workshop: activity first, framing second. Do not generate 50-minute
   lecture-shaped content.
6. **Read an existing file before writing its sibling.** Open `course_profile.json` before
   writing `syllabus_manb109.json`; open `syllabus_manb109.json` before writing any
   `lectures/*.json`. This is what stops schema drift.
7. **Update `project.json → build_telemetry` whenever you generate.** Counts must equal
   files actually on disk.

---

## Blocking gaps — resolve before Step 3

| # | Gap | Why it blocks |
|---|---|---|
| 1 | **Units 4+ missing.** Source syllabus ended at Unit 3. | Session plan cannot be laid out against 30 contact hours. |
| 2 | **CO 109.2 has no home.** "Present creative ideas using storytelling and visual tools" is not covered by Units 1–3. | The CO-PO matrix will not close; an unattainable CO fails OBE audit. |
| 3 | **Assessment plan absent.** No components, weights, or CO mapping. | Rubrics (Step 5) have nothing to grade against. |
| 4 | **Reference books absent.** | Session `readings` cannot be populated. |
| 5 | **`109.2` cognitive ability is "Develop"** — not a Bloom's Revised level. | `blooms_level` is `null`; decide the mapping (likely `create` or `apply`) before generating LOs for it. |

Steps 1–2 can proceed now. **Step 3 onward needs gaps 1–3 closed.**

---

## Step 1 — Complete `course_profile.json` / `.md`

Fill `syllabus_outline` with the remaining units once supplied. Divide the **30 total
contact hours** across all units and set `hours_allocated` on each (they must sum to 30).
Keep Units 1–3 exactly as they are — they are verbatim from the university.

## Step 2 — CO-PO articulation matrix

For each of `109.1`–`109.4`, set `po_mapping` (`3` strong / `2` moderate / `1` light,
omit zeros) and write a `mapping_justification` naming each PO and its weight, in the style
of MANB304A. Then populate `co_po_articulation_matrix.matrix` (full 4×6 grid including
zeros), `.totals` (per-CO and per-PO sums) and `.attainment_targets`.

Expect PO5 (Communication) and PO6 (Entrepreneurial) to carry this course — it is a studio
elective about expressing and applying ideas, not a strategy or analytics course. Do not
inflate PO2 mappings to make the grid look balanced.

Mirror the result into the `## CO-PO Articulation Matrix` section of `course_profile.md`.

## Step 3 — `syllabus_manb109.json`

The single object in this file is a **shape reference** (`_exemplar: true`). Expand to the
full session list, one object per 120-minute studio session, sequential `LEC_01`, `LEC_02`, …
Copy the key structure exactly: `lecture_id, title, unit, duration, session_type,
target_cos, lo, active_learning, content, readings`.

- 3–5 learning objectives per session, each with an explicit `blooms` level.
- Every prescribed hands-on activity must appear in `active_learning` **verbatim**, with
  `source: "prescribed_syllabus_unit_N_hands_on_activity"`. Add your own supporting
  exercises alongside it, marked `source: "generated"`.
- Activity minutes should be the majority of the 120.
- Strip `_exemplar` and `_note` from the finished file.
- Every CO must be hit by at least one session. Verify before moving on.

## Step 4 — `lectures/`

One `lecture_lec_NN.json` + `lecture_lec_NN.md` per session. JSON keys, exactly:
`schema_version, lecture_uuid, course_code, lecture_id, lecture_title, duration_minutes,
target_co_ids, content, learning_objectives, pre_requisites, active_learning_components,
readings`. Fresh UUID per session; `duration_minutes: 120`; `course_code: "MANB109"`.

Write for BAMU students — many first-generation learners from rural and semi-urban
Marathwada. Use local, low-cost examples (a kirana shop, an SHG, a coaching class, a
workshop in Chhatrapati Sambhajinagar), not Silicon Valley case studies. Mind maps and
SCAMPER should be taught with pen and paper first, software second.

## Step 5 — `slides/`, `rubrics/`, `templates/`, `worksheets/`, `visuals/`

- **slides/** — `slides_lec_NN.{md,json,html,pptx}`. Carry over the `defensive_guardrails`
  from MANB307M: max 115 words and 8 bullets per slide, ≥40% negative space, min 14pt font.
  A studio session needs few slides — brief, then get out of the way.
- **rubrics/** — one per assessment component from Step 1's assessment plan.
- **templates/** — student-facing worksheets: a mind-map canvas, a SCAMPER grid
  (7 prompts × idea), a storytelling/pitch structure sheet, an idea-log.
- **worksheets/** — per-session exercise sheets, printable, usable offline.
- **visuals/** — diagrams: the creative process stages, mind-map anatomy, the SCAMPER wheel.

## Step 6 — Validate

- Every `target_co_ids` value resolves to a CO in `course_profile.json`.
- CO-PO matrix rows sum to `totals`; no CO is orphaned.
- Unit `hours_allocated` sums to 30.
- `build_telemetry` counts equal files on disk.
- Set `dirty_invalidation_matrix.course_profile` to `false` only when all of the above pass.
