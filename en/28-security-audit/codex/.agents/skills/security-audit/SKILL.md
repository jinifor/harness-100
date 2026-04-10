---
name: security-audit
description: >-
  Trigger when: the user wants the `security-audit` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Security Audit Harness

An agent team harness for performing security audits covering vulnerability scanning, code analysis, penetration test reporting, and remediation recommendations.

## Specialist Agents

- `audit-reviewer`: audit reviewer(QA). vulnerability-codeanalysis-penetrationtest-improvement betweenof   verificationlower, risketc. lower, final audit report creation.
- `code-analyst`: code security analyst. SAST from the perspective of source codeof security vulnerability -based analysislower, queue  violated matter detectionlower, security pattern/pattern identification.
- `pentest-reporter`: penetration test report. the vulnerability as actual attack  lower, PoC setuplower, business impact analysisto penetration test report .
- `security-consultant`: security . the vulnerabilityin  improvement , security architecture proposal, framework(ISO 27001, NIST) mapping, ·· security asmap count.
- `vulnerability-scanner`: vulnerability . dependency vulnerability(CVE), infrastructure configuration error, notify security vulnerability systematicas and riskalso classificationto report.

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

## Deliverables

- `00_input.md` — Audit scope and organized user input
- `01_vulnerability_scan.md` — Vulnerability scan results
- `02_code_analysis.md` — Code security analysis report
- `03_pentest_report.md` — Penetration test scenario report
- `04_remediation_plan.md` — Remediation recommendations and roadmap
- `05_audit_report.md` — Final audit report

## Extension Skills

- `.agents/skills/cve-analysis/SKILL.md`
- `.agents/skills/owasp-testing-guide/SKILL.md`
- `.agents/skills/threat-modeling/SKILL.md`
