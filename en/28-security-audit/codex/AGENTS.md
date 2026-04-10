# Security Audit Harness

This folder is the Codex version of the Security Audit Harness. Start with the local `security-audit` skill for the full workflow.

## Structure

- Orchestrator skill: `.agents/skills/security-audit/SKILL.md`
- Specialist agents: `.codex/agents/audit-reviewer.toml`, `.codex/agents/code-analyst.toml`, `.codex/agents/pentest-reporter.toml`, `.codex/agents/security-consultant.toml`, `.codex/agents/vulnerability-scanner.toml`
- Extension skills: `.agents/skills/cve-analysis/SKILL.md`, `.agents/skills/owasp-testing-guide/SKILL.md`, `.agents/skills/threat-modeling/SKILL.md`

## Workflow

- Start full-pipeline work with `security-audit`.
- Use custom agents only for explicit specialist delegation or parallel work.
- Keep all deliverables in `_workspace/`.
- If a reviewer or synthesizer role exists, run it after prerequisite artifacts are available and report findings first.
- Keep the source `.claude` files untouched.

## Rules

- Do not invent undocumented Codex keys, manifests, or extra scripts/assets.
- If existing source material already satisfies a phase, reference or copy it into `_workspace/` and skip redundant work when appropriate.
- If external lookup or generation fails, continue with the best available context and note the limitation.

## Summary

- An agent team harness for performing security audits covering vulnerability scanning, code analysis, penetration test reporting, and remediation recommendations.

## Deliverables

- `00_input.md` — Audit scope and organized user input
- `01_vulnerability_scan.md` — Vulnerability scan results
- `02_code_analysis.md` — Code security analysis report
- `03_pentest_report.md` — Penetration test scenario report
- `04_remediation_plan.md` — Remediation recommendations and roadmap
- `05_audit_report.md` — Final audit report
