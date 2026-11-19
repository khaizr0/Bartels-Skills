# BARTELS Skills

Source of truth for BARTELS AI agent skills. The catalog platform reads this repository directly.

## Layout

```
skills/<slug>/
  SKILL.md        # required: name + description in frontmatter
  catalog.yaml    # required metadata: title, collection, owner, authors, version, risk_tier, tags, status
  references/     # optional supporting files
```

## Editing

Use the catalog platform:

- `/contribute` to propose a new skill.
- Edit on an existing skill to propose a change.
- A reviewer approves the proposal.
- The approved change is written into this repository.

Commit and push after approving:

```bash
git add .
git commit -m "Add or update <slug>"
git push
```

Do not store proposals, feedback, or generated bundles here. Those live with the platform.

## Rules

- One folder per skill, slug in lowercase with hyphens.
- `SKILL.md` must stay readable by any AI client.
- `catalog.yaml` is the source of catalog metadata.
- Never edit a published skill directly in production; use the proposal flow.
