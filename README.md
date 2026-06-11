# Bin-Stack

A local collection of Codex skills and skill drafts — reusable AI-assisted engineering workflows kept in one repository.

## Repository Layout

| Path | Status | Purpose |
| --- | --- | --- |
| `project-code-onboarding/` | Active skill | Generates a concise Markdown onboarding guide for a codebase (architecture, entry points, interfaces, runtime flows, Mermaid diagrams). |
| `html-tech-diagram/` | Active skill | Generates self-contained HTML technical diagrams for flows, state machines, and architecture. |
| `taleb-antifragile-analysis/` | Active skill | Analyzes decisions, careers, companies, and strategies through fragility, tail risk, convexity, optionality, and antifragility. |
| `elon-musk-first-principles/` | Active skill | Stress-tests ambitious engineering, manufacturing, product, and execution plans with first-principles reasoning, the Idiot Index, and Musk's five-step algorithm. |
| `skills-draft/` | Local drafts | Staging area for candidate skills before promotion. Ignored by git. |

Each skill's own `SKILL.md` is the source of truth for what it does and when it triggers — this README does not duplicate that.

## Using a Skill

Expose the skill directory through your Codex skills path, then reference it in a prompt with `$skill-name`:

```text
Use $project-code-onboarding to analyze this repo and write docs/project-onboarding.md.
```

## Developing a Skill

### 1. Directory structure

A skill is a directory whose name matches its `name:` frontmatter. Keep `SKILL.md` lean and push bulky content into supporting files (progressive disclosure — supporting files are loaded only when the skill references them):

```text
skill-name/
  SKILL.md                 # required: frontmatter + workflow. Keep it short.
  agents/
    openai.yaml            # optional: UI metadata (display_name, short_description, default_prompt)
  templates/               # optional: output scaffolds the skill fills in
    *.md
  reference/               # optional: detailed rules/specs read on demand
    *.md
  scripts/                 # optional: helper scripts the skill runs
```

`project-code-onboarding` is the reference example: its `SKILL.md` holds the workflow and points to `templates/onboarding-template.md` and `reference/mermaid.md` instead of inlining them.

### 2. Frontmatter

```yaml
---
name: skill-name
description: What the skill produces, the trigger phrases that should activate it, and what it must NOT be used for.
---
```

A good `description` is the trigger contract. Make it specific enough that Codex knows exactly when to fire, list real trigger phrases (including localized ones), and state explicit non-goals so it does not compete with unrelated workflows.

### 3. Write the workflow

- Give numbered, ordered steps from scope assessment to a verifiable output.
- Prefer concrete, checkable instructions ("render each Mermaid block with the CLI") over vague guidance ("make sure diagrams look right").
- Include a final verification step the model can actually execute, so it can confirm output before reporting success.
- Move long templates, syntax rules, and example libraries into `templates/` or `reference/` and link them by relative path.

### 4. Test and promote

1. Draft in `skills-draft/` (git-ignored) while iterating.
2. Test with a real prompt in a small target repo and check the trigger fires and the output verifies.
3. Promote to a top-level directory only when it is ready to be versioned.

## Maintenance Notes

- One reusable workflow per skill.
- Keep `SKILL.md` frontmatter `description` in sync with `agents/openai.yaml`.
- Keep `SKILL.md` short; bulky reference material belongs in `reference/` or `templates/`.
- Do not commit generated outputs, local caches, or scratch files.
