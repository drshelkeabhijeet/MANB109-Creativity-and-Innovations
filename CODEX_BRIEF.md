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
8. **Follow `course_profile.json → pedagogical_profile.delivery_model`.** It is binding on
   every session you generate, not advisory. The next section restates it operationally.
9. **The five files already in `templates/` are authored, not generated.** Reference them;
   never overwrite or regenerate them.
10. **Every session ends with a pitch.** No exceptions — it is the only attainment path for
    CO 109.2.

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

---

## Delivery model — binding on generation

Full rationale lives in `course_profile.json → pedagogical_profile.delivery_model` and in
the *How This Course Is Taught* section of `course_profile.md`. Read one of them before
generating. Operationally, these are the constraints:

### 1. One anchor enterprise, three lenses

Each student picks **one real local enterprise in week 1** and carries it through all three
units — Unit 1 brainstorms its problem, Unit 2 mind-maps it, Unit 3 SCAMPERs its offering.

Every session's making phase applies that session's technique **to the student's own anchor
enterprise**. Do not invent generic case companies, and do not give each unit a fresh
scenario. Session 1 uses `templates/anchor_business_brief.md` to select it.

This stays inside the prescribed wording: the syllabus names *a mobile app or website*, and
the anchor's digital surface — WhatsApp catalogue, Google Business listing, simple site — is
that app or website. Say so in the session content; do not silently substitute.

### 2. Diverge in Marathi, converge in English

Brainstorming, mind-map labels, idea log and peer critique run in **Marathi or Hindi**.
The pitch is in **English**. State this explicitly in each session's instructions rather
than leaving it implied. Worksheets carry bilingual labels.

### 3. The pitch is the spine

Every session's last 25 minutes are critique and a ~3-minute pitch per presenter, using
`templates/peer_critique_protocol.md` and `templates/pitch_structure.md`. `109.2` appears in
the `target_cos` of **all 15 sessions** — that is what makes it attainable.

### 4. Fixed 120-minute rhythm

`10 warm-up · 15 input · 60 making · 25 critique and pitch · 10 idea log`

Never more than 15 continuous minutes of facilitator talk. Activity minutes are the clear
majority. If content will not fit the 15-minute input beat, move it into the making phase as
something students discover, not something you tell them.

### 5. Safety before technique

Open each early session with a low-stakes warm-up — deliberately bad ideas, worst-possible-
solution, and similar. Weeks 1–2 are **team-attributed only**; no individual is singled out
before trust exists. Unit 1 teaches barriers to creativity, so the room must model it.

### 6. Paper first, software second

Assume no laptop, no reliable projector, patchy data. A3 sheets, printed grids, markers.
Never write a session that fails without a projector or an internet connection.

### 7. Tools do not retire

Mind mapping stays in use through Unit 3; Unit 1's brainstorming norms hold all semester.
Do not treat a unit's technique as finished when its five sessions end.

### 8. Say the forward links out loud

Each session guide names where the tool is reused in Semester III — mind mapping in
MANB307A, SCAMPER in MANB304A, pitching in MANB307M, decomposition in MANB306A. The mapping
is in `delivery_model.forward_links`. Signposted transfer is retained; unsignposted is not.

### 9. Feedback, not grading

There is no assessment plan. The peer critique protocol and the idea log are the feedback
instruments and are **ungraded**. Never attach marks, weights or rubrics to them.

---

## Steps 1–2 — DONE

Course profile and CO-PO matrix are complete in `course_profile.{json,md}`. Read them
before generating anything; do not regenerate them.

## Step 3 — `syllabus_manb109.json` ← START HERE

The single object in this file is a **shape reference** (`_exemplar: true`). Expand to
**exactly 15 sessions**, `LEC_01` … `LEC_15`, five per unit, each 120 minutes. Copy the key
structure exactly: `lecture_id, title, unit, duration, session_type, target_cos, lo,
active_learning, content, readings`.

Arc within each unit's five sessions: concept and demonstration → guided practice →
independent application → the prescribed hands-on activity → consolidation and pitch.
Session 1 of the semester also runs anchor-enterprise selection using
`templates/anchor_business_brief.md`.

- 3–5 learning objectives per session, each with an explicit `blooms` level.
- Every prescribed hands-on activity must appear in `active_learning` **verbatim**, with
  `source: "prescribed_syllabus_unit_N_hands_on_activity"`. Add your own supporting
  exercises alongside it, marked `source: "generated"`.
- Every session's `active_learning` applies its technique to the student's **anchor
  enterprise**, not to a generic case company.
- Activity minutes are the majority of the 120, per the fixed rhythm above.
- Every session carries a closing pitch entry in `active_learning`
  (`type: "Critique and Pitch"`, `duration: 25`).
- Leave `readings` as an empty array on every session — no reading list is prescribed.
- Strip `_exemplar` and `_note` from the finished file.
- Every CO must be hit by at least one session, and **`109.2` appears in all 15** — every
  session ends in a pitch, and that is its only attainment path (see finding 1 above).
- Verify all four COs are covered before moving on.

## Step 4 — `lectures/` — facilitator guides, not lecture notes

One `lecture_lec_NN.json` + `lecture_lec_NN.md` per session. JSON keys, exactly:
`schema_version, lecture_uuid, course_code, lecture_id, lecture_title, duration_minutes,
target_co_ids, content, learning_objectives, pre_requisites, active_learning_components,
readings`. Fresh UUID per session; `duration_minutes: 120`; `course_code: "MANB109"`;
`readings: []`.

**The `.md` is a facilitator guide.** Follow `templates/facilitator_session_template.md`
exactly — timed phases, what to say, when to stop talking, what good and stuck look like
while circulating, and the nudge for each. Studio teaching is facilitation; generated lecture
prose will not help anyone run the room.

Each guide includes: a materials checklist that assumes no projector, the one idea students
must leave with, the making task in a single sentence, a stuck-and-nudge table, the closing
pitch, and the forward link named aloud.

Write for BAMU students — many first-generation learners from rural and semi-urban
Marathwada. Examples come from their own anchor enterprises, not Silicon Valley case studies.
Mind maps and SCAMPER are taught pen-and-paper first, software second.

## Step 5 — `slides/`, `templates/`, `worksheets/`, `visuals/`

- **slides/** — `slides_lec_NN.{md,json,html,pptx}`. Carry over the `defensive_guardrails`
  from MANB307M: max 115 words and 8 bullets per slide, ≥40% negative space, min 14pt font.
  A studio session needs **few slides** — they serve the 15-minute input beat only. Every
  session must still run if the projector fails.
- **rubrics/** — **skip.** This course carries no assessment plan by faculty decision;
  `assessment_co_po_alignment` is empty and `attainment_targets` is null. Leave `rubrics/`
  and `assessments/` empty. Do not invent graded components or weights. If an assessment
  scheme is attached later, generate rubrics from it then.
- **templates/** — five files already exist and are **authored, not generated**:
  `anchor_business_brief.md`, `peer_critique_protocol.md`, `idea_log.md`,
  `pitch_structure.md`, `facilitator_session_template.md`. Reference them; never overwrite
  them. You may add only the two technique canvases still missing: a **mind-map canvas**
  (A3, centre node pre-drawn) and a **SCAMPER grid** (7 prompts × idea).
- **worksheets/** — per-session exercise sheets. **Printable A4, one page, bilingual
  labels (Marathi + English), usable with no device.** A worksheet that needs a screen is a
  failed worksheet.
- **visuals/** — **room posters, not slide decoration**: the creative process stages,
  mind-map anatomy, the SCAMPER wheel. Legible from the back of a classroom, printable in
  greyscale on A3.

## Step 6 — Validate

- Every `target_co_ids` value resolves to a CO in `course_profile.json`.
- CO-PO matrix rows sum to `totals`; no CO is orphaned.
- Unit `hours_allocated` sums to 30 (10 per unit, 3 units).
- Exactly 15 sessions exist, 5 per unit.
- `109.2` is in the `target_cos` of **all 15** sessions, and each has a closing pitch.
- Each session's making phase names the student's **anchor enterprise**, not a generic case.
- Each session's `active_learning` minutes match the fixed rhythm; talk time ≤ 15 min.
- Each facilitator guide follows `templates/facilitator_session_template.md` and names its
  forward link.
- The five authored `templates/` files are unmodified.
- Worksheets are one-page, bilingual and device-free.
- `readings` is empty and `rubrics/` / `assessments/` are empty — both are deliberate.
- `build_telemetry` counts equal files on disk.
- Set `dirty_invalidation_matrix.course_profile` to `false` only when all of the above pass.
