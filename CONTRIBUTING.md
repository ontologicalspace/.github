# Contributing to Ontological Space

Thank you for your interest in contributing to the Ontological Space organization and
the Ontological Space Protocol (OSP). This guide describes how to contribute to
repositories under `ontologicalspace`.

---

## Project model

OSP follows a **phased development model**. Each phase has measurable Go/No-Go gates,
and design decisions are documented in `docs/`. Because OSP is a research protocol
with an immutable academic record, contributions are expected to carry evidence — a
claim should point to a test, a corpus result, or a paper section.

Please read [`GOVERNANCE.md`](GOVERNANCE.md) to understand which changes require what
kind of evidence and review.

---

## Where to contribute

| Repository | Holds |
|------------|-------|
| [`ontologicalspace/osp`](https://github.com/ontologicalspace/osp) | The reference implementation (Rust workspace) |
| [`ontologicalspace/.github`](https://github.com/ontologicalspace/.github) | This org profile + default community files |

Default community health files (`CONTRIBUTING.md`, `SECURITY.md`, etc.) live in this
`.github` repository and are inherited by repositories that do not provide their own.

### Note on issue templates

Issue templates (and `config.yml`) must live under `.github/ISSUE_TEMPLATE/`. If a
repository contains **any** file in its own `.github/ISSUE_TEMPLATE/` directory, the
entire organization-default issue template bundle is disabled for that repository —
GitHub applies an all-or-nothing override.

---

## Before you start

- **Search existing issues and PRs** to avoid duplicates.
- For non-trivial changes, open an issue first to discuss scope.
- Security vulnerabilities are **never** reported through public issues — see
  [`SECURITY.md`](SECURITY.md).

---

## Branch and commit conventions

- Branch from `main` and use a descriptive prefix:
  - `feat/…` — new functionality
  - `fix/…` — bug fixes
  - `docs/…` — documentation
  - `chore/…` — tooling, CI, metadata
- Write clear commit messages. We typically squash-merge, so the PR title becomes the
  canonical commit subject.
- Keep PRs focused; one logical change per PR.

---

## Evidence expectations

| Your change | Attach evidence |
|-------------|-----------------|
| Implementation | Regression/integration test |
| Public API | Test + migration note |
| Metric semantics | Fixture + affected corpus rerun |
| Invariant/formal model | Spec source + conformance proof |
| Documentation | Cross-references to code/paper sections |

See [`GOVERNANCE.md`](GOVERNANCE.md) §2 for the full change→evidence table.

---

## Pull request process

1. Open a PR against `main` and fill in the pull request template.
2. CI (where configured) must pass. For this `.github` repository, the
   `validate` workflow checks YAML syntax, required files, and placeholders.
3. Resolve all review conversations before requesting merge.
4. High-risk changes (invariants, metric semantics, witness/quorum, evidence integrity,
   security boundaries) require an Eligible Independent Reviewer before merge — see
   [`GOVERNANCE.md`](GOVERNANCE.md) §3.

---

## Code of conduct

By participating, you agree to uphold the standards in
[`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).
