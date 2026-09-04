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

## Status — gaps closed

The course profile is **complete**. The syllabus is three units, 2 credits, 0:0:2,
30 contact hours (10 per unit), delivered as 15 weekly 120-minute studio sessions,
five per unit. There is no Unit 4.

This course carries **no assessment plan and no reading list** by faculty decision. The
three prescribed hands-on activities are teaching activities, not graded components.
Generate no rubrics, weights, graded artefacts, or citations — leave every `readings`
field an empty array. Do not fill these from the other course repos' patterns.

Steps 1 and 2 are **done**. Start at **Step 3**.

Two things in `course_profile.json` are generated rather than prescribed, and are marked
as such. Do not silently rewrite them:

| Item | State |
|---|---|
| CO-PO matrix, `po_mapping`, `mapping_justification` | Generated, pending faculty sign-off |
| `blooms_level` for 109.2 | Mapped `create` from the non-standard prescribed verb "Develop" |

### Two findings to carry into generation

1. **CO 109.2 is not served by any unit.** "Present creative ideas effectively using
   storytelling and visual tools" appears in no unit's topics. With only three units this
   is permanent, not a missing page. It is attained instead through the **presentation
   component of all three prescribed hands-on activities plus the final pitch**. Every
   session you generate must therefore end with a share-out, pitch, or gallery walk, and
   `109.2` must appear in the `target_cos` of those sessions. If you drop the presentation
   beat, the CO becomes unattainable.

2. **PO4 is mapped 0 across all four COs.** This is deliberate and honest — nothing in the
   syllabus addresses ethical or inclusive leadership. Do not invent PO4 content to fill
   the column.

---

## Steps 1–2 — DONE

Course profile and CO-PO matrix are complete in `course_profile.{json,md}`. Read them
before generating anything; do not regenerate them.

## Step 3 — `syllabus_manb109.json` ← START HERE

The single object in this file is a **shape reference** (`_exemplar: true`). Expand to
**exactly 15 sessions**, `LEC_01` … `LEC_15`, five per unit, each 120 minutes. Copy the key
structure exactly: `lecture_id, title, unit, duration, session_type, target_cos, lo,
active_learning, content, readings`.

Suggested arc within each unit's five sessions: concept and demonstration → guided practice →
independent application → the prescribed hands-on activity → critique and pitch.

- 3–5 learning objectives per session, each with an explicit `blooms` level.
- Every prescribed hands-on activity must appear in `active_learning` **verbatim**, with
  `source: "prescribed_syllabus_unit_N_hands_on_activity"`. Add your own supporting
  exercises alongside it, marked `source: "generated"`.
- Activity minutes should be the majority of the 120.
- Leave `readings` as an empty array on every session — no reading list is prescribed.
- Strip `_exemplar` and `_note` from the finished file.
- Every CO must be hit by at least one session. `109.2` in particular must appear in the
  `target_cos` of every session that ends in a pitch or share-out — that is its only
  attainment path (see finding 1 above).
- Verify all four COs are covered before moving on.

## Step 4 — `lectures/`

One `lecture_lec_NN.json` + `lecture_lec_NN.md` per session. JSON keys, exactly:
`schema_version, lecture_uuid, course_code, lecture_id, lecture_title, duration_minutes,
target_co_ids, content, learning_objectives, pre_requisites, active_learning_components,
readings`. Fresh UUID per session; `duration_minutes: 120`; `course_code: "MANB109"`;
`readings: []`.

Write for BAMU students — many first-generation learners from rural and semi-urban
Marathwada. Use local, low-cost examples (a kirana shop, an SHG, a coaching class, a
workshop in Chhatrapati Sambhajinagar), not Silicon Valley case studies. Mind maps and
SCAMPER should be taught with pen and paper first, software second.

## Step 5 — `slides/`, `templates/`, `worksheets/`, `visuals/`

- **slides/** — `slides_lec_NN.{md,json,html,pptx}`. Carry over the `defensive_guardrails`
  from MANB307M: max 115 words and 8 bullets per slide, ≥40% negative space, min 14pt font.
  A studio session needs few slides — brief, then get out of the way.
- **rubrics/** — **skip.** This course carries no assessment plan by faculty decision;
  `assessment_co_po_alignment` is empty and `attainment_targets` is null. Leave `rubrics/`
  and `assessments/` empty. Do not invent graded components or weights. If an assessment
  scheme is attached later, generate rubrics from it then.
- **templates/** — student-facing worksheets: a mind-map canvas, a SCAMPER grid
  (7 prompts × idea), a storytelling/pitch structure sheet, an idea-log.
- **worksheets/** — per-session exercise sheets, printable, usable offline.
- **visuals/** — diagrams: the creative process stages, mind-map anatomy, the SCAMPER wheel.

## Step 6 — Validate

- Every `target_co_ids` value resolves to a CO in `course_profile.json`.
- CO-PO matrix rows sum to `totals`; no CO is orphaned.
- Unit `hours_allocated` sums to 30 (10 per unit, 3 units).
- Exactly 15 sessions exist, 5 per unit.
- `readings` is empty and `rubrics/` / `assessments/` are empty — both are deliberate.
- `build_telemetry` counts equal files on disk.
- Set `dirty_invalidation_matrix.course_profile` to `false` only when all of the above pass.
