# Starting a documentation session

Use this guide when beginning a fresh chat or writing session in this repository.

## Purpose and audience

`subwave-docs` is a user-facing companion to SUB/WAVE. It turns recent feature
work and accumulated operator experience into clear, practical writing for
station operators and interested listeners.

It is **not** the official reference manual, a pull-request archive, or a
development diary. The intended voice is an experienced, candid operator: warm,
specific, and clear about what is observed, configurable, experimental, or not
yet released.

## Document roles

| Place | Purpose | Reader |
| --- | --- | --- |
| `updates/` | One shareable landing page per meaningful update | Someone arriving from social media or a release note |
| `field-guide/` | Evergreen experience-led advice | Station operators looking to improve their setup |
| `faqs/` | Short reusable answers | Readers with one focused question |
| `assets/screenshots/` | Images used by the pages | Page authors |

An update page must stand alone. It should not assume readers know a branch,
an LLM term, or the history of an experiment. Field Guide pages may be more
reflective, but should still separate personal advice from a product guarantee.

## Current first collection

The initial group of pages brings together a month of related work:

1. **Safer, more natural DJ links** — factual boundaries, safe prompt context,
   show-transition wording, and output sanitation.
2. **Sleeve Notes** — optional, bounded track-related material that can make a
   link richer without becoming a factual free-for-all.
3. **Smarter track selection** — controller-built candidate shortlists,
   editorial final choice, controllable breadth, and Musical Leanings.

Treat those as complementary: grounded material supports natural links; a
presenter remains creative within a safe factual boundary; and the DJ retains
editorial judgement after the controller has found eligible music.

## Essential development references

Read the source material before asserting a capability, a safety guarantee, or
the status of a feature. Prefer the maintained branch documents and pull
requests; they supersede older exploratory writing.

### Prompt Safety and Sleeve Notes

- [PR #1633 — Make DJ links safer and more natural](https://github.com/perminder-klair/subwave/pull/1633)
- [Enriched Sleeve Notes design note](https://github.com/Jaz666/subwave/blob/feat/prompt-safety-verified-facts/docs/internals/enriched-sleeve-notes.md)
- [Prompt Safety extraction map](https://github.com/Jaz666/subwave/blob/feat/prompt-safety-verified-facts/docs/prompt-safety-extraction-map.md)

Key user-facing ideas: supplied facts form the factual boundary; subjective
reaction is still welcome; Sleeve Notes are optional editorial material, not a
checklist; and output sanitation is a final safety layer rather than a creative
instruction.

### Native Track Shortlisting and Musical Leanings

- [PR #1634 — Native track shortlisting and Musical Leanings](https://github.com/perminder-klair/subwave/pull/1634)
- [Native track shortlisting design record](https://github.com/Jaz666/subwave/blob/feat/track-cpu-shortlisting/docs/internals/track-shortlisting.md)
- [Comparison-run record](https://github.com/Jaz666/subwave/blob/feat/track-cpu-shortlisting/docs/internals/track-shortlisting-comparisons.md)
- [Current development-path map](https://github.com/Jaz666/subwave/blob/feat/track-cpu-shortlisting/docs/DEVELOPMENT_PATHS.md)

Key user-facing ideas: Context → Continuity → Exploration is the default
three-pass shape; the controller establishes eligibility and provenance; the DJ
makes the final editorial choice; and Musical Leanings are a soft tie-breaker,
never a way around show, safety, or variety rules.

### Historical findings: useful, but not current architecture

- [Significant Findings and Working Knowledge](https://github.com/Jaz666/subwave/blob/archive/producer-routing-20260906/docs/internals/subwave-significant-findings.md)

This is valuable source material for the Field Guide, particularly its findings
on factual grounding, prompt dilution, recent-speech imitation, persona design,
show briefs, strict versus soft filters, library metadata, restraint, and the
distinction between operational discovery and editorial judgement.

Do **not** describe its retired Producer-routing or FunctionGemma proposals as
current SUB/WAVE architecture. Use the current PRs and design records above for
what is actually being proposed or implemented.

### Official documentation

- [Official SUB/WAVE documentation](https://github.com/perminder-klair/subwave/tree/develop/docs)
- [Concepts](https://github.com/perminder-klair/subwave/blob/develop/docs/concepts.md)
- [Custom skills](https://github.com/perminder-klair/subwave/blob/develop/docs/custom-skills.md)

Use official documentation for exact setup instructions. This repository should
link to it rather than duplicate it.

## Writing workflow

1. Check the status of the associated PR or release before writing a headline.
2. Read the relevant source links above and extract only user-meaningful claims.
3. Draft the update page first; it is the social-link destination.
4. Move evergreen, general advice into the Field Guide and reusable answers into
   the FAQ.
5. Add screenshots only when they clarify a setting or an outcome.
6. Finish each page with related links and a clear release-status note when
   needed.

## Style guardrails

- Say what a reader can notice or control before explaining internals.
- Prefer “the DJ” and “the Booth” to retired architectural labels.
- Do not publish private diagnostics, raw prompts, sensitive station data, or
  unverified anecdotes as facts.
- Do not imply that experimental or draft features are already available in a
  released build.
- Keep one page focused on one outcome; link out rather than repeating whole
  explanations.
