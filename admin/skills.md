# BARTELS Admin Skill

This file is for the admin MCP endpoint. It is not part of the public skill catalog.

## Purpose

Fold approved feedback into the official skills without losing control of the base instructions.

## Inputs

- Official skills in `skills/<slug>/SKILL.md`.
- `Approved Feedback` rows with `Status = active`.

## Workflow

1. Read the approved feedback.
2. Group by `Skill Slug`.
3. Check for duplicates and contradictions.
4. For each skill:
   - keep the existing `SKILL.md` structure;
   - add a short `## Additional guidance` section, or fold the note into the relevant section;
   - do not copy raw user comments;
   - do not include personal data.
5. Open one pull request per skill.
6. After the pull request is merged, mark the feedback as `applied` and add the PR link.

## Rules

- The base `SKILL.md` instructions take precedence.
- Only use approved feedback. Never use raw `Feedback Log` entries directly.
- Maximum 10 addenda per skill.
- Maximum 2,000 characters of addenda per skill.
- Do not change unrelated skills in the same PR.
- Do not merge the PR yourself.
- Do not include customer names, prices, CVs, or BOQ contents in prompts.
