---
name: mobile-app-builder
description: >-
  Trigger when: the user wants the `mobile-app-builder` harness workflow or its main deliverables end to end. Do not trigger when: a narrower extension skill is sufficient or the request depends on tooling outside this harness. Expected input: user request, constraints, existing files, or source material. Expected output: `_workspace/` deliverables plus the final review or synthesis artifact.
---

# Mobile App Builder Harness

A harness where an agent team collaborates to perform UI/UX design, native code generation, API integration, and store deployment preparation for mobile apps.

## Specialist Agents

- `api-integrator`: API integration specialist. Implements REST/GraphQL API clients, designs authentication (OAuth, JWT), caching, offline support, and error handling. Optimizes the data flow between server and app.
- `app-developer`: Mobile app developer. Generates native/cross-platform code using Swift/SwiftUI, Kotlin/Jetpack Compose, Flutter, or React Native. Applies architecture patterns (MVVM, Clean Architecture) and implements testable structures.
- `qa-engineer`: Mobile QA engineer. Performs UI testing, performance testing, accessibility verification, security checks, and platform compatibility testing. Cross-verifies consistency across all deliverables.
- `store-manager`: App store deployment manager. Prepares metadata, screenshot guides, privacy policies, and review response strategies needed for App Store Connect and Google Play Console.
- `ux-designer`: Mobile UX/UI designer. Designs wireframes, design systems, navigation structures, and interaction patterns. Follows iOS HIG and Material Design guidelines while incorporating accessibility (A11y) considerations.

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

- `00_input.md` — Organized user input
- `01_ux_design.md` — UX/UI design document
- `02_app_code/` — App source code
- `02_app_architecture.md` — App architecture document
- `03_api_integration.md` — API integration specification
- `04_store_listing.md` — Store deployment metadata
- `05_qa_report.md` — QA verification report

## Extension Skills

- `.agents/skills/app-store-optimization/SKILL.md`
- `.agents/skills/mobile-ux-patterns/SKILL.md`
