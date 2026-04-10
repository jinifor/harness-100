---
name: personal-branding
description: >-
  Trigger when: the user wants the `personal-branding` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Personal Branding Harness

A personal branding agent team harness.

## Specialist Agents

- `cover-letter-writer`: Cover Letter Writing Specialist. Writes authentic yet strategic cover letters customized for target positions.
- `portfolio-designer`: Portfolio Designer. Curates key projects, designs the storytelling structure for each project, and plans the overall composition of the portfolio site/document.
- `positioning-strategist`: Positioning Strategist. Analyzes an individual's strengths, experience, and goals, and designs differentiation points and brand narratives for the target market.
- `profile-optimizer`: LinkedIn Profile Optimization Specialist. Maximizes search visibility and creates profile content that attracts recruiters.
- `resume-writer`: Resume/CV Writing Specialist. Creates ATS-optimized, achievement-focused resumes that reflect the positioning strategy.

## Workflow

1. Gather the request, constraints, and any existing source material.
2. Save the starting context in `_workspace/00_input.md` when that helps downstream handoff.
3. Run the specialists needed for the request scope, using numbered `_workspace/` artifacts as handoff points.
4. Run the reviewer or synthesizer role, if present, after prerequisite artifacts exist.
5. Report skipped phases, limitations, and reused inputs in the final result.

## Output Rules

- Keep the source `.claude` files untouched.
- Keep all harness deliverables in `_workspace/`.
- If existing files already satisfy a phase, reference or copy them into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Extension Skills

- `.agents/skills/ats-optimizer/SKILL.md`
- `.agents/skills/linkedin-seo/SKILL.md`
