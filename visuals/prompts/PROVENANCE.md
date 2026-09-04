# Image Provenance — MANB109 visuals

Every raster image in `visuals/` was generated, not sourced. This record exists so any of
them can be regenerated or replaced.

| Field | Value |
|---|---|
| Generator | `codex` CLI codex-cli 0.153.2 built-in `image_gen` tool |
| Session | recorded in the run log; not surfaced by the CLI |
| Date | 2026-09-04 |
| Prompt file | [`course_visual_set.txt`](course_visual_set.txt) — verbatim, one run, all four images |
| Native size | 1536 x 1024 (3:2 landscape), the tool's fixed ~1.57 MP budget |
| Post-processing | None. No resize, no re-encode. |

## Files

| File | Size | SHA-256 (first 16) |
|---|---|---|
| `hero_creative_studio.png` | 3104 KB | `b75cb2bc2b371c27` |
| `unit1_foundations.png` | 2918 KB | `e44d6a9875fc63be` |
| `unit2_mind_mapping.png` | 2728 KB | `0036e4810d0ae332` |
| `unit3_scamper.png` | 2649 KB | `5792c73917cc416e` |

## Constraints worth knowing

- The built-in tool takes no size or quality argument. **~1.57 MP is a hard ceiling** —
  ample for slides and text-width print figures, short for a full-page bleed.
- Style is held by the prompt's STYLE block, which is byte-identical across all four and
  must be reused verbatim for any future image in this set, or the style will drift.
- All four were produced in **one run**, which is what keeps them looking like one hand.
  Generating a fifth in a separate session risks visible drift; attach an existing image as
  a reference (`-i`) if you do.

## Rules for this directory

- Superseded images move to `visuals/rejects/`. **Never delete** — the record should show
  what was tried.
- Diagrams that explain a technique stay **SVG**, not raster: they scale to A3, print in
  greyscale, and can be corrected by editing text.
- No image in this course may be load-bearing. Every session must run with no projector.
