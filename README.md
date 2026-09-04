# MANB109 — Creativity and Innovations

MBA Generic Elective · Semester I · 2 credits · L:T:P 0:0:2
Department of Management Science, Dr. Babasaheb Ambedkar Marathwada University,
Chhatrapati Sambhajinagar (Aurangabad).

An [Academia OS](#) v1.3.0 course workspace. **Scaffold stage** — metadata and the
prescribed syllabus are in place; session content is not yet generated.

## Layout

| Path | Contents |
|---|---|
| `academia.yaml` | Workspace manifest — course identity, pedagogy, accreditation |
| `project.json` | Build state and telemetry |
| `course_profile.{md,json}` | COs, POs, CO-PO matrix, syllabus |
| `TEACHING_PLAN.md` | The 15-session map: arc, CO coverage, where each prescribed activity lands |
| `syllabus_manb109.json` | Per-session learning objectives and studio activities |
| `kb/` | Ingestion sandbox — drop source material here before generating |
| `lectures/` `slides/` | Generated session content and decks |
| `templates/` | 11 authored studio instruments — anchor brief, critique protocol, idea log, pitch structure, Buzan canvas, SCAMPER grid, technique card, three contrasting-cases sheets, facilitator template |
| `worksheets/` | 15 per-session student sheets — what the student holds through the making phase |
| `visuals/` | 4 SVG diagrams and 4 generated images |

## Status

Course profile **complete**. Three units, 2 credits, L:T:P 0:0:2, 30 contact hours
(10 per unit), delivered as 15 weekly 120-minute studio sessions. All four COs and all
three units are transcribed verbatim from the university-prescribed syllabus.

[`TEACHING_PLAN.md`](TEACHING_PLAN.md) maps all 15 sessions. **Session 1 is written** as a
sample facilitator guide (`lectures/lecture_lec_01.{md,json}`) for review before the
remaining 14 are generated. Sessions 2–15, slides, worksheets and visuals are **not yet
generated** — see [`CODEX_BRIEF.md`](CODEX_BRIEF.md), Step 3 onward.

### Pending faculty sign-off

The CO-PO articulation matrix and the Bloom's mapping for 109.2 are generated rather than
prescribed. Both are marked as such in `course_profile.json` under `_scaffold_notes`.

This course carries **no assessment plan and no reading list** by faculty decision —
`assessment_co_po_alignment` is empty, `attainment_targets` is null, `readings` stays empty
on every session, and `rubrics/` and `assessments/` stay empty.

Two findings worth reading before sign-off:

- **CO 109.2** — *"Present creative ideas effectively using storytelling and visual tools"* —
  is not named in any of the three units. It is attained through the presentation component
  of the three prescribed hands-on activities and the final pitch. Worth recording with the
  Board of Studies rather than leaving implicit.
- **PO4** (Ethical, Social and Inclusive Leadership) is mapped 0 by all four COs. Nothing in
  the syllabus addresses it. PO coverage closes at programme level, so this is defensible —
  but confirm before submission.

## How it is taught

A studio course, not a lecture course. The delivery model is recorded in
`course_profile.json → pedagogical_profile.delivery_model` and explained in the
*How This Course Is Taught* section of [`course_profile.md`](course_profile.md). In short:

- **One anchor enterprise** picked in week 1 and carried through all three units — Unit 1
  brainstorms its problem, Unit 2 mind-maps it, Unit 3 SCAMPERs its offering.
- **Diverge in Marathi, converge in English** — ideation in the language students think in,
  the pitch in English.
- **Every session ends with a ~3-minute pitch.** Fifteen sessions, fifteen repetitions, and
  the only attainment path for CO 109.2.
- **Fixed 120-minute rhythm** — 10 warm-up / 15 input / 60 making / 25 critique and pitch /
  10 idea log. Never more than 15 continuous minutes of facilitator talk.
- **Paper first, software second** — nothing depends on a projector or a connection.
- **Feedback without grading** — a peer critique protocol and an ungraded idea log.
- **Seven learning-science moves built in** — retrieval practice every session, worked examples
  before technique practice, contrasting cases before producing, per-session worksheets,
  early-finisher extensions, an owner check-in after Session 5, and technique cards at each
  unit's end.

Five studio instruments in [`templates/`](templates/) are authored rather than generated and
should not be overwritten.

## Generating content

Open this repo in Codex and follow [`CODEX_BRIEF.md`](CODEX_BRIEF.md) step by step. It
carries the schema rules, the CO id convention (`109.N`), and the studio-course constraints
that keep generated output consistent with the rest of the course portfolio.
