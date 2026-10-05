# GitHub Repository Standard (GRS) v1 — Bootstrap Specification

Status: **Draft / bootstrap**
Canonical target: `DaniilSydorenko/.github`

GRS is the policy-as-code contract for repositories in the DaniilSydorenko GitHub portfolio. Repository quality must be explicit, class-aware, versioned, auditable, and enforceable where GitHub capabilities allow.

> This bootstrap copy lives in the profile repository only until the canonical `.github` control repository exists. It must then move there without changing ownership semantics.

## 1. Authority model

GRS defines repository governance. It does not define product architecture or career truth.

- Career Intelligence owns career facts, evidence, provenance, gaps, and priorities.
- Project repositories own their implementation and project-specific architecture.
- GRS owns repository-quality policy, repository classes, machine-readable contracts, validation, and GitHub governance expectations.
- Human-controlled gates remain authoritative for private → public visibility, external credentials, destructive administration, and consequential releases.

## 2. Requirement levels

| Level | Meaning | Validator behavior |
| --- | --- | --- |
| REQUIRED | The repository must satisfy the rule for its class. | FAIL |
| RECOMMENDED | Strong default; omission needs no hard block. | WARN |
| OPTIONAL | Supported but not expected. | PASS / informational |
| N/A | Deliberately not applicable. | Ignored |

A numeric health score may be displayed later, but `PASS / WARN / FAIL / N/A` is authoritative.

## 3. Repository classes

GRS v1 defines seven classes:

- `profile` — special public GitHub profile repository.
- `oss-library` — reusable public library/package intended for external consumers.
- `product` — application/product repository.
- `engineering-labs` — deliberate-practice repository built around engineering missions/scenarios/tasks.
- `knowledge` — handbook/documentation/knowledge-system repository.
- `platform` — data, automation, orchestration, or control-plane repository.
- `historical` — frozen historical evidence; safe and honest, but not forced to imitate a modern active project.

## 4. Governed surfaces

Every class profile must explicitly classify these surfaces as REQUIRED, RECOMMENDED, OPTIONAL, or N/A:

### Repository identity
- README and explicit project/status statement
- description, topics, homepage where applicable
- ownership, maturity, visibility, portfolio role
- license/licensing policy

### Collaboration
- Issue Forms / issue taxonomy
- pull-request template
- CONTRIBUTING policy
- Code of Conduct where appropriate

### Engineering verification
- tests
- lint
- typecheck
- build validation
- project-specific quality checks

### Security and supply chain
- `.gitignore`
- secret scanning
- dependency automation/scanning where dependencies exist
- minimal GitHub Actions permissions
- third-party Actions pinned to immutable full commit SHA where practical
- SECURITY policy for externally consumable/public attack surfaces
- no committed secrets, private data, company-confidential data, credentials, private keys, databases, or backups

### Architecture and decisions
- architecture documentation where complexity warrants it
- ADR/design-decision policy by class
- explicit trade-offs for flagships

### Releases
- release enablement by class
- changelog/release notes
- provenance where packages/artifacts are published
- human-controlled release gates where consequential

### GitHub governance
- default-branch protection/ruleset expectations
- required checks
- direct-push policy
- scheduled governance validation
- public-readiness requirements

## 5. Baseline class intent

| Surface | profile | oss-library | product | engineering-labs | knowledge | platform | historical |
| --- | --- | --- | --- | --- | --- | --- | --- |
| README/status | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED |
| .gitignore | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | RECOMMENDED |
| license policy | N/A | REQUIRED | REQUIRED* | REQUIRED* | REQUIRED before public | REQUIRED* | REQUIRED if historically licensed |
| secret scan | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED |
| PR template | OPTIONAL | REQUIRED | REQUIRED | REQUIRED | RECOMMENDED | REQUIRED | N/A |
| issue taxonomy | N/A | REQUIRED | REQUIRED | REQUIRED | RECOMMENDED | REQUIRED | N/A |
| tests | N/A | REQUIRED | REQUIRED | REQUIRED | validation-specific | REQUIRED | N/A |
| lint/typecheck | N/A | REQUIRED when applicable | REQUIRED when applicable | REQUIRED when applicable | validation-specific | REQUIRED when applicable | N/A |
| SECURITY.md | N/A | REQUIRED | RECOMMENDED | RECOMMENDED | OPTIONAL | RECOMMENDED | OPTIONAL |
| CONTRIBUTING.md | N/A | REQUIRED | RECOMMENDED | RECOMMENDED | RECOMMENDED | RECOMMENDED | N/A |
| ADR/design decisions | N/A | RECOMMENDED | REQUIRED for flagship | REQUIRED | RECOMMENDED | REQUIRED for flagship | N/A |
| releases | N/A | REQUIRED | when releasable | milestone-based | generated-doc releases if used | when releasable | N/A |
| metadata | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED | REQUIRED historical status |
| branch protection | RECOMMENDED | REQUIRED | REQUIRED for public flagship | RECOMMENDED | RECOMMENDED | REQUIRED for flagship | N/A |

`REQUIRED*` means a licensing decision is required; the repository is not automatically required to use an open-source license.

## 6. Per-repository manifest

Managed repositories declare their contract in `.github/repository.yml`.

Minimum shape:

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

Overrides must be explicit, narrow, and justified. A repository may not override critical security requirements merely to make validation green.

## 7. Enforcement architecture

```text
GRS policy + class profile + repository manifest
                    ↓
             repository validator
                    ↓
          PASS / WARN / FAIL / N/A
                    ↓
        reusable GitHub Actions check
                    ↓
 required status check / ruleset where supported
```

Critical deterministic checks should block merge where GitHub plan/capabilities permit. Recommended rules warn rather than creating bureaucracy.

## 8. Versioning

GRS is versioned. Repositories declare the standard version they implement.

A future GRS upgrade must produce migration requirements rather than silently breaking every repository. Example:

```text
GRS v1 → GRS v2 available → migration report → repository PR → GRS v2
```

## 9. Historical/frozen contract

Historical repositories preserve engineering history. They must remain safe, understandable, and non-misleading, but they are not modernized merely to satisfy contemporary cosmetics.

Historical baseline:
- README/status clearly communicates historical/frozen state.
- no live secrets/private data.
- existing licensing remains clear.
- no misleading claim of active maintenance.
- no unnecessary feature development.
- security remediation remains allowed.

## 10. Rollout

1. Freeze GRS v1 specification.
2. Move canonical policy to `DaniilSydorenko/.github`.
3. Add machine-readable schema and class profiles.
4. Implement repository validator.
5. Implement reusable governance workflow.
6. Add community-health defaults/templates.
7. Pilot on profile repository and Haversine.
8. Roll out to active repositories.
9. Apply reduced historical/frozen contract.
10. Add scheduled drift detection and remediation proposals.
11. Integrate verified governance/evidence signals with Career Ecosystem.
12. Evolve toward GitHub Autopilot.

## 11. Bootstrap exit condition

This bootstrap location is complete when:
- `DaniilSydorenko/.github` exists;
- this specification is moved into the canonical control repository;
- schema/class profiles are introduced through a reviewed PR;
- the profile repository consumes GRS rather than owning it.
