# Repository Engineering Standard

Task: `PORT-002`

This standard governs repositories presented as part of the Nikolaos Anestakis engineering portfolio. Its purpose is to make projects easy to evaluate, maintain, reproduce, and trace back to engineering work.

## 1. Repository classification

Every repository must have an explicit portfolio role before it is promoted:

- **Flagship** — strongest independent engineering work.
- **Supporting** — useful project that strengthens the portfolio but is not a primary showcase.
- **Reusable Engineering** — libraries, frameworks, templates, shared components, or governance tooling.
- **Academic — Individual** — coursework completed primarily by Nikolaos.
- **Academic — Team** — collaborative university work with Nikolaos's contribution clearly identified.
- **Collaborative / Contributor** — project owned by another person or team; never presented as independently authored.
- **Learning / Experimental** — exploratory work, prototypes, labs, or exercises.
- **Legacy / Archive** — historically useful work retained for progression evidence.

Ownership and authorship are separate. Repository ownership must never be used to imply sole authorship when the history is collaborative.

## 2. README minimum standard

A portfolio-facing repository should explain, near the top:

1. What the project is.
2. Why it exists / the problem it addresses.
3. Project status and provenance.
4. Nikolaos's contribution when work is collaborative.
5. Core architecture or major components.
6. Technologies used and why they were chosen.
7. How to run or inspect the project.
8. How the project is tested or verified.
9. Known limitations and important trade-offs.
10. Future improvements or retrospective lessons where useful.

Academic repositories must include institution/course context when known and must distinguish original coursework from later independent improvements.

## 3. Documentation structure

Use only documentation that adds engineering value. Do not add files simply to make a repository look enterprise-like.

Recommended when justified:

```text
docs/
  architecture.md
  setup.md
  testing.md
  decisions/
  screenshots/
```

Architecture Decision Records (ADRs) are appropriate when an important technical choice has meaningful alternatives or consequences.

Example:

```text
docs/decisions/0001-use-fastapi.md
```

An ADR should state **Status, Context, Decision, Alternatives, and Consequences**.

## 4. Git and ClickUp traceability

Meaningful portfolio work must map to a ClickUp task using the `PORT-###` convention.

### Branch names

Use a purpose prefix plus task ID:

```text
feature/PORT-021-api-health
fix/PORT-034-auth-timeout
docs/PORT-004-delivery-architecture
audit/PORT-003-delivery-predictor
refactor/PORT-012-validation
portfolio/PORT-002-repository-standard
```

### Commit messages

Every meaningful commit must begin with its task ID and describe one coherent change.

```text
PORT-021 feat: add health endpoint
PORT-021 test: add health endpoint coverage
PORT-004 docs: document service architecture
PORT-034 fix: handle expired authentication sessions
```

Avoid messages such as `update`, `changes`, `fix`, `final`, `test2`, or `misc`.

### Pull requests

PR titles should begin with the same task ID:

```text
PORT-021 Add API health endpoint
```

PR descriptions should contain purpose, changes, validation/testing, risks or limitations when relevant, and the associated ClickUp task.

## 5. Change workflow

Default engineering flow:

```text
ClickUp task
  -> BACKLOG
  -> READY
  -> IN PROGRESS
  -> feature/fix/docs/audit branch
  -> atomic commits
  -> pull request
  -> CODE REVIEW
  -> merge
  -> DONE
```

Do not perform routine portfolio work directly on the default branch.

## 6. Repository structure

Repository structure must follow the technology and problem domain rather than one universal template.

Typical application example:

```text
README.md
src/
tests/
docs/
scripts/
.github/workflows/
```

Typical networking-lab repository may instead use:

```text
README.md
labs/
topologies/
configs/
verification/
docs/
scripts/
```

Consistency should exist in navigation, naming, documentation, and engineering practice — not through artificial folder uniformity.

## 7. Testing and verification

A repository should define an appropriate verification strategy.

Depending on project type this may include:

- unit tests,
- integration tests,
- API tests,
- linting and static analysis,
- reproducible ML evaluation,
- network show-command verification,
- configuration validation,
- manual acceptance checks where automation is not practical.

Claims in a README should be supported by reproducible evidence where reasonable.

## 8. CI/CD

Flagship repositories should normally have CI when automated checks provide real value. CI may run tests, linting, type checking, build validation, security checks, or release gates.

Do not add CI purely for appearance. A simple project with no meaningful automated validation does not require a ceremonial workflow.

## 9. Security and secrets

Never commit:

- passwords,
- API keys,
- private keys,
- production credentials,
- access tokens,
- real secrets in `.env` files,
- sensitive personal or client data.

Use `.env.example` or equivalent when configuration variables must be documented. Review Git history when there is reason to suspect secrets were previously committed.

Security-sensitive projects should document threat assumptions and limitations where relevant.

## 10. Dependencies and reproducibility

Dependencies should be explicitly declared using the ecosystem's standard mechanism, for example `requirements.txt`, `pyproject.toml`, `package.json`, or equivalent.

Setup instructions should be sufficient for another engineer to understand the expected environment. Pin versions when reproducibility materially depends on them.

Generated dependencies, virtual environments, IDE metadata, caches, large local datasets, and build artifacts should normally be excluded from Git unless there is a deliberate reason to version them.

## 11. CHANGELOG, CONTRIBUTING, LICENSE

These files are conditional, not mandatory decorations.

- **CHANGELOG.md** — use for versioned software or projects with meaningful release history.
- **CONTRIBUTING.md** — use when external or multi-person contribution is plausible or contribution rules matter.
- **LICENSE** — add only after the intended reuse/open-source terms are decided. Private or academic repositories do not automatically require one.

## 12. Academic and collaborative work

Academic/team projects must clearly state:

- academic context,
- team vs individual status,
- Nikolaos's specific responsibility,
- original constraints,
- which work was performed during the academic project,
- which improvements were made later, if any.

Never rewrite project history to make coursework appear commercial or solely authored.

When useful, preserve an identifiable academic baseline and document later modernization separately.

## 13. Legacy projects

Legacy work should be preserved when it demonstrates progression or contains unique knowledge. Do not delete unique work until a verified backup exists.

A legacy README may include a retrospective such as **What I Would Change Today** rather than silently modernizing history.

## 14. Experimental repositories

Experimental work may remain private or unfeatured until it communicates a clear engineering lesson. Empty placeholders and abandoned experiments should not compete with flagship work.

## 15. Flagship promotion gate

A repository should not be promoted as flagship until an audit confirms that it has:

- clear ownership/provenance,
- clear purpose,
- understandable architecture,
- credible documentation,
- appropriate verification/testing,
- safe secrets/data handling,
- coherent Git history going forward,
- enough technical depth to justify reviewer attention.

Flagship status is earned by evidence, not by repository size or technology count.

## 16. Portfolio principle

The portfolio should optimize for reviewer comprehension and engineering credibility. A reviewer should quickly understand what the system does, what Nikolaos contributed, why key decisions were made, how correctness was verified, and what limitations remain.
