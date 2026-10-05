# GitHub Repository Standard (GRS)

> Bootstrap specification. The canonical home for GRS is `DaniilSydorenko/.github` once that control repository exists.

GRS is the policy-as-code contract for repositories in the DaniilSydorenko GitHub portfolio. Its purpose is to make repository quality explicit, class-aware, versioned, auditable, and enforceable without forcing every repository into the same shape.

## Core model

```text
GRS policy
  → repository class
    → per-repository manifest
      → validator
        → reusable GitHub workflows
          → PASS / WARN / FAIL / N/A
            → required checks / rulesets where supported
```

## Requirement levels

- **REQUIRED** — absence or violation fails governance validation.
- **RECOMMENDED** — absence or violation emits a warning.
- **OPTIONAL** — supported but not expected.
- **N/A** — deliberately not applicable.

A numeric health score may be derived for presentation, but it must never hide a failed REQUIRED control.

## Repository classes

GRS v1 defines these classes:

- `profile` — GitHub identity/presentation repository.
- `oss-library` — reusable public package/library.
- `product` — deployable product/application.
- `engineering-labs` — deliberate engineering practice using Mission → Stage → Scenario → Task.
- `knowledge` — structured documentation/theory/handbook.
- `platform` — data, automation, integration, or control-plane system.
- `historical` — frozen historical evidence; safe and honestly framed, not cosmetically modernized.

## Governed surfaces

Class profiles must explicitly decide the applicability and level of:

1. README, purpose, status, ownership and maturity.
2. License/licensing policy.
3. `.gitignore` and generated-artifact hygiene.
4. `SECURITY.md` and vulnerability reporting.
5. `CONTRIBUTING.md` and Code of Conduct where appropriate.
6. Issue Forms, issue taxonomy and PR template.
7. Tests, lint, typecheck and other class-specific validation.
8. Secret scanning and credential hygiene.
9. Dependency and supply-chain hygiene.
10. GitHub Actions permissions, action pinning and workflow safety.
11. Default-branch protection/ruleset expectations.
12. Release, changelog and provenance requirements.
13. Architecture and ADR expectations.
14. Repository description, topics and homepage.
15. Public-readiness requirements.
16. Historical/frozen behavior.

## Per-repository manifest

Managed repositories should eventually contain a small manifest:

```yaml
schema: 1

standard:
  version: 1

repository:
  class: oss-library
  maturity: maintained
  visibility: public

portfolio:
  flagship: true
  pin_candidate: true
```

Repository-specific overrides must be explicit, schema-valid and limited to controls that GRS marks overridable. An override must never silently weaken a non-overridable security control.

## Enforcement

The validator is authoritative for policy evaluation:

- REQUIRED violation → `FAIL`
- RECOMMENDED violation → `WARN`
- satisfied control → `PASS`
- non-applicable control → `N/A`

For flagship repositories, critical governance checks should become required status checks and branch/ruleset gates where GitHub plan and repository visibility support them.

Human-controlled gates remain mandatory for consequential operations including private → public visibility changes, credential revocation/rotation and sensitive releases.

## Versioning

GRS is versioned. A new standard version must not silently break every managed repository. Upgrades should produce a migration report and move repositories deliberately to the new version.

## Historical repositories

The `historical` class uses a reduced contract. Historical repositories must remain safe, understandable and truthful about their age/status. GRS must not manufacture modern-looking activity or require irrelevant 2026 engineering machinery merely to improve a score.

## Rollout

1. Bootstrap GRS v1 specification.
2. Define machine-readable schema and class profiles.
3. Implement repository validator.
4. Add reusable GitHub Actions.
5. Add templates/default community-health files.
6. Pilot on the profile repository and Haversine.
7. Roll out to Engineering Labs, Ladvero, Engineering Handbook, Career Intelligence and other active repositories.
8. Apply the reduced historical/frozen contract.
9. Add scheduled drift detection and remediation proposals.
10. Feed verified governance/evidence signals into Career Ecosystem and GitHub Autopilot.

## Canonical-home transition

This file is intentionally a bootstrap artifact. Once `DaniilSydorenko/.github` exists, GRS source-of-truth policy belongs there. This repository should then retain only the profile-specific manifest/caller and links to the canonical standard.
