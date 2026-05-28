---
name: vault-to-artifact-tailor
description: >
  Tailor a personal outbound artifact (resume / cover letter / outreach email /
  proposal / pitch one-pager) against an external audience constraint
  (job description / RFP / pitch context), using a personal memory vault as the
  source of truth. Use when the user provides (1) a vault path or repo URL with
  their canonical self-data, and (2) an audience constraint document or link.
metadata:
  layer: cognitive-meta
  category: outbound-artifact-generation
compatibility: Designed for Claude Code (and other agentic CLIs) operating against a personal memory vault that follows the personal-memory-vault-starter schema. Not for one-shot generation without vault grounding.
license: MIT
---

# Vault-to-Artifact Tailor Skill

Version: 0.1

## Purpose

Convert a person's canonical vault content into a tailored outbound artifact
(resume, cover letter, outreach, proposal) that matches an external audience
constraint — **without** fabricating evidence, **without** smoothing away the
person's authentic voice, and **without** leaking private vault fields beyond
what the artifact's destination warrants.

The skill is a translator, not a writer. Every claim in the output must be
traceable to a vault node. If a section of the artifact cannot be backed by
vault evidence, the skill surfaces it as a `[TBD]` placeholder rather than
inventing content.

## When to use

- Job application (resume tailored to a specific JD)
- Cover letter tailored to a specific role / company
- Outreach email to investor / customer / collaborator with audience-fit framing
- Proposal / pitch one-pager tailored to a specific audience constraint
- Any case where: **canonical self-data + audience constraint → tailored sendable artifact**

## Do not use

- One-shot generation with no vault (the skill's whole point is vault grounding)
- Pure copywriting tasks where audience truth-fidelity is not required
- When user wants generic polished prose with no structural fidelity
- When vault evidence is too thin — surface the gap, don't fabricate

## Input expectations

Required:
- **Vault locator**: GitHub repo URL (private acceptable, will use `gh` CLI) or local filesystem path. Must follow `personal-memory-vault-starter` schema or equivalent (`people/`, `projects/`, `playbooks/`, `tracelets/`, etc.)
- **Audience constraint**: one of (a) URL to JD/RFP/pitch context, (b) raw text of the constraint, (c) bullet-point summary of audience requirements

Optional (improves output):
- **Artifact type**: `resume | cover_letter | outreach_email | proposal_one_pager` (default: `resume`)
- **Direction hint**: short phrase from user describing the angle they want (e.g. "enterprise customer-facing" vs "developer relations" vs "ops-born product")
- **Length budget**: page count or word count (default: resume 2-3 pages, cover letter ≤1 page)
- **Output language**: e.g. `en`, `zh`, `ja` (default: match audience constraint language)
- **Render format**: `markdown | html | pdf | all` (default: `pdf` + `markdown`)

## Vault contract

The skill expects vault to roughly follow this layout:

```
<vault-root>/
├── INDEX.md              network entry / navigation
├── people/<self>.md      canonical self-description (name, contact, locations, languages, current role anchors)
├── projects/*.md         project history with evidence
├── playbooks/*.md        operating rules / preferences
├── tracelets/*.md        single-decision calibration moments
└── concepts/*.md         (optional) framework / vocabulary anchors
```

The skill reads these nodes by topic relevance to the audience constraint.
It does NOT modify vault content. It only **reads** vault and **writes** artifacts
back to a designated outputs location (default: `vault/projects/<career-or-equiv>/outputs/`).

## Output contract

Return:

```json
{
  "audience_parse": {
    "organization": "...",
    "role_title": "...",
    "role_family": "solutions_architect | developer_relations | product_manager | engineer | program_manager | other",
    "level": "ic | senior | staff | manager | director",
    "location": "...",
    "key_keywords": ["..."],
    "explicit_requirements": ["..."],
    "preferred_requirements": ["..."]
  },
  "vault_query": {
    "nodes_read": ["people/quinn.md", "projects/career.md", "playbooks/...", "..."],
    "evidence_for_each_claim": { "claim_id": "vault_node_path" }
  },
  "tailored_sections": {
    "headline": "...",
    "profile": "...",
    "target_roles": ["..."],
    "core_positioning": ["..."],
    "selected_projects": [{"title": "...", "vault_node": "...", "tailored_summary": "..."}],
    "skills": [...],
    "match_summary": [...]
  },
  "redaction_log": {
    "items_filtered": ["..."],
    "reason": "..."
  },
  "rendered_artifact": {
    "markdown_path": "...",
    "pdf_path": "...",
    "char_count": 0,
    "estimated_pages": 0
  },
  "tbd_placeholders": ["fields the user must fill before sending"]
}
```

## Method

1. **Parse audience constraint** → extract organization, role_title, role_family, level, location, key keywords, explicit/preferred requirements.
2. **Query vault** by topic relevance:
   - `people/<self>.md` → identity, contact (subject to redaction), languages
   - `projects/career.md` or equivalent → master resume content, applications log, prior tailored variants
   - other `projects/*.md` → project evidence that matches role_family
   - `playbooks/*.md` → tone, voice, addressing convention, no-go phrases
3. **Apply tailoring rules**:
   - mirror audience keywords into Profile + Core Positioning (only if vault has matching evidence)
   - rank/select top 2-3 projects most relevant to role_family
   - tilt core positioning emphasis to match role_family invariants (e.g. SA = customer-discovery + cross-functional; DR = translation + community; PM = ops-to-product + metrics)
   - generate role-specific match summary mapping audience requirements to vault evidence
4. **Render**:
   - tailored markdown → HTML template → PDF (via Chrome headless or equivalent)
   - save to `vault/projects/<career>/outputs/<YYYY-MM-DD>_<org>_<role>/`
5. **Emit redaction log + TBD list**:
   - never leak vault fields that the audience destination doesn't warrant (e.g. private employer compensation in a public-facing pitch)
   - surface any claim that couldn't be backed by vault as `[TBD]` for user to fill

## Privacy / sovereignty

- **Vault read access**: skill uses user-authorized `gh` CLI or local filesystem; does not transmit vault content to external services without explicit user invocation
- **Output destination control**: tailored artifacts default to `vault/.../outputs/` (still inside the private vault); user explicit action moves them to public surface (LinkedIn upload, Workday application, etc.)
- **Redaction by default**: if audience constraint indicates a public surface, the skill removes vault-private fields (real compensation numbers, employer-private project metrics, etc.) and notes them in `redaction_log`
- **No fabrication**: every claim traceable to vault node; missing evidence → `[TBD]`, never hallucinated
- **Respect vault's own privacy rules**: if vault has a `playbooks/external-writing-anonymize.md` or similar, the skill follows it

## Anti-patterns to avoid

- Generating content not grounded in vault (hallucination)
- Smoothing user's authentic voice into corporate prose (this is what `founder-thought-translator` covers; vault-to-artifact-tailor should call it for the actual prose translation step, not redo it)
- Adding metrics not in vault (use only vault-stored real numbers)
- Filling `[TBD]` placeholders with assumed data
- Pushing tailored output to public repo without explicit per-output user confirmation
- Mixing multiple audience constraints into one artifact (one constraint → one artifact)

## Defaults

| Field | Default |
|---|---|
| Output format | PDF + markdown both |
| Resume length | 2-3 pages |
| Cover letter length | ≤1 page |
| Outreach email length | ≤300 words |
| Output directory | `<vault>/projects/<career_node>/outputs/<YYYY-MM-DD>_<org>_<role>/` |
| Redaction | filter compensation + employer-private metrics if destination is public |
| Language | match audience constraint language |
| Naming convention | `<YYYY-MM-DD>_<org_slug>_<role_slug>.<ext>` |

## Composition with other skills

This skill composes with existing claude-cognition-skills:

- **`founder-thought-translator`** — call when a section needs raw vault thought translated into sendable prose without losing voice
- **`decision-snapshot-builder`** — call when audience constraint is fuzzy and needs structuring before tailoring begins
- **`trap-detector`** — call to catch when tailoring drifts into fabrication or audience-pleasing distortion
- **`helpful-now-deriver`** — call when user is mid-application and needs the smallest useful next move, not a full polished artifact

## Reference implementation reuse

The PDF render pipeline is reused from prior work (Chrome headless + HTML+CSS template). Recommended directory layout in vault career node:

```
vault/projects/career/
├── README.md                          career node entry
├── master-resume-source.md            canonical master
├── applications-log.md                application history tracker
├── templates/                         (optional) HTML/CSS templates per artifact type
└── outputs/
    └── YYYY-MM-DD_<org>_<role>/
        ├── tailored.md
        ├── tailored.html
        └── tailored.pdf
```
