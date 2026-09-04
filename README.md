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
| `syllabus_manb109.json` | Per-session learning objectives and studio activities |
| `kb/` | Ingestion sandbox — drop source material here before generating |
| `lectures/` `slides/` | Generated session content and decks |
| `templates/` `worksheets/` `visuals/` | Student-facing studio material |

## Status

Course profile **complete**. Three units, 2 credits, L:T:P 0:0:2, 30 contact hours
(10 per unit), delivered as 15 weekly 120-minute studio sessions. All four COs and all
three units are transcribed verbatim from the university-prescribed syllabus.

Session content (`lectures/`, `slides/`, `templates/`, `worksheets/`, `visuals/`) is
**not yet generated** — see [`CODEX_BRIEF.md`](CODEX_BRIEF.md), Step 3 onward.

### Pending faculty sign-off

The CO-PO articulation matrix, the reference list, and the Bloom's mapping for 109.2 are
generated rather than prescribed. They are marked as such in `course_profile.json` under
`_scaffold_notes`.

This course carries **no assessment plan** by faculty decision — `assessment_co_po_alignment`
is empty, `attainment_targets` is null, and `rubrics/` and `assessments/` stay empty.

Two findings worth reading before sign-off:

- **CO 109.2** — *"Present creative ideas effectively using storytelling and visual tools"* —
  is not named in any of the three units. It is attained through the presentation component
  of the three prescribed hands-on activities and the final pitch. Worth recording with the
  Board of Studies rather than leaving implicit.
- **PO4** (Ethical, Social and Inclusive Leadership) is mapped 0 by all four COs. Nothing in
  the syllabus addresses it. PO coverage closes at programme level, so this is defensible —
  but confirm before submission.

## Generating content

Open this repo in Codex and follow [`CODEX_BRIEF.md`](CODEX_BRIEF.md) step by step. It
carries the schema rules, the CO id convention (`109.N`), and the studio-course constraints
that keep generated output consistent with the rest of the course portfolio.
