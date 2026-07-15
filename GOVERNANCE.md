# Ontological Space — Governance

This document defines how the Ontological Space organization and its repositories are
governed. It is written to be **honest about the current reality** and **explicit about
the future model**, so that the project's organizational procedure is itself an instance
of its epistemic discipline.

---

## 1. Scope

This governance model applies **by default** to repositories owned by the
`ontologicalspace` organization. A repository may provide a local `GOVERNANCE.md` for
repository-specific rules. Local governance **may specialize** this model but **must not
weaken** organization-level requirements on:

- security,
- evidence integrity, and
- publication integrity.

This mirrors GitHub's default-file override model: a local file always takes precedence
over the org-wide default, but the org default establishes the floor.

---

## 2. Authority Surfaces

OSP separates *where truth lives* from *where it is explained*. Four authority surfaces
govern different kinds of changes:

| Authority surface | Owns | A change here requires… |
|-------------------|------|-------------------------|
| **Protocol** | Invariants, formal model, specs | Paper/spec evidence + conformance proof |
| **Implementation** | Code, CI, tests, tooling | Regression/reproducibility evidence |
| **Paper-Evidence** | Zenodo/arXiv deposits, manuscripts | A new version/corrigendum — never an edit |
| **Release** | Versions, tags, DOIs, receipts | Release evidence + DOI receipt commit |

### The immutability principle

> **Published deposits are never rewritten.** Material changes produce a new version,
> corrigendum, or superseding record. This is the foundation of Paper-Evidence Authority.

### Change → required evidence → publication impact

| Change | Required evidence | Publication impact |
|--------|-------------------|--------------------|
| Internal implementation | Regression test | None |
| Public API | Test + migration note | Docs version bump if needed |
| Normative invariant | Spec source + conformance evidence | Next paper/spec version |
| Metric implementation bug | Fixture + affected corpus rerun | Corrigendum/new version if a claim is affected |
| Metric semantic redefinition | Corpus rerun + compatibility statement | New manuscript/deposit version |
| Published claim correction | Impact analysis | Corrigendum or new DOI version |
| Security boundary | Regression/adversarial evidence | Advisory if coordinated disclosure needed |

---

## 3. Decision Basis — Two Channels, Not "Two Witnesses"

OSP's core features BFT-inspired witnessing with an author/witness separation: a change
author is not an independent witness of their own change. We are careful **not** to
mislabel solo decisions as independent witnessing. Instead, the decision basis has two
channels:

1. **Mechanical verification** — CI, tests, validators, and reproducibility checks where
   applicable. This is the deterministic, re-runnable evidence channel.
2. **Accountable operator decision** — The Project Owner (or a maintainer) records the
   scope, the evidence reviewed, and the risk assessment. This is the human-judgment
   channel.
3. **Independent human review** — An *Eligible Independent Reviewer* (defined below).
   This channel is **not yet enforceable** during the solo phase; it activates when at
   least two eligible maintainers exist.

### Eligible Independent Reviewer

> An **Eligible Independent Reviewer** must:
>
> - not be the author or co-author of the change,
> - have access to the relevant evidence, and
> - demonstrate sufficient competence in the affected authority surface.
>
> The review must be recorded as an explicit approval, rejection, or evidence-qualified
> comment.

### High-risk changes require independent review

The following changes require an Eligible Independent Reviewer **before merge**:

- Normative invariant changes
- Metric semantic redefinition
- Witness/quorum safety
- Evidence integrity
- Security boundary changes

> During the solo phase, high-risk independent review is **policy-enforced rather than
> branch-enforced**. The Project Owner must not merge an affected pull request until the
> qualifying review is recorded. (Branch protection's approval count is `0`; this rule is
> held manually until a second maintainer exists.) If no reviewer can be found, the PR
> remains pending — this is a real rule, not a metaphor.

### Security review privacy

> Security-sensitive reviews may be conducted through a private security advisory or
> another confidential review channel. Public disclosure is **not** required before
> remediation. A change that touches a security boundary may proceed through the private
> reporting path and be merged once remediated and the embargo lifts.

---

## 4. Current Governance Phase

**Phase:** Solo founder / owner.

- The Project Owner holds all roles: author, reviewer-of-record, release authority, and
  emergency bypass holder.
- "Independent human review" (channel 3 above) is **not yet enforceable**; the owner
  records accountable decisions and holds high-risk PRs pending until an external
  reviewer is engaged.
- This phase is documented honestly so that no solo decision is presented as
  two-party witnessing.

### Owner authority limits

Even as sole owner, the Project Owner:

- **must not** rewrite published Zenodo/arXiv deposits,
- **must not** merge a high-risk change (§3 list) without a recorded qualifying review,
- **must not** bypass the branch ruleset except under the emergency conditions below,
  and then only with a follow-up public rationale record.

---

## 5. Future Multi-Maintainer Model

When at least **two eligible maintainers** exist, the following activate:

- Branch-enforced independent review (approval count ≥ 1 for the high-risk list).
- A `CODEOWNERS` file mapping authority surfaces to owners.
- A defined maintainer onboarding/offboarding process (below).
- Shared release authority.

Maintainer roles and their addition/removal are recorded in the repository (e.g., in a
`MAINTAINERS.md` or team membership), never left implicit.

---

## 6. Branch Ruleset (`main`)

A repository **ruleset** (preferred over classic branch protection for its explicit
bypass model) governs `main`:

- **Enforcement:** Active
- **Require pull request:** Yes
- **Required approvals:** `0` during solo phase; ≥ `1` for the high-risk list when a
  second maintainer exists
- **Require conversation resolution:** Yes
- **Block force pushes:** Yes
- **Block deletions:** Yes
- **Owner emergency bypass:** Permitted **only** for security hotfix or repository
  recovery

### Emergency bypass accountability

> Emergency bypass use must be followed by a **public incident or rationale record** once
> disclosure is safe. The record must include the reason, the affected commit(s), the
> checks that were omitted, and the remediation status. A bypass without a follow-up
> record is a governance violation.

---

## 7. Release, Tag, and DOI Authority

- The Project Owner (and, in the future, designated maintainers) hold release authority.
- A release consists of: a semver tag, a changelog entry, a `CITATION.cff` update
  (software DOI + version + date-released), and a receipt commit.
- Paper DOIs and the software DOI are **never conflated**. Paper DOIs reference the
  companion manuscripts; the software DOI references the implementation. Until the first
  real release, the software DOI field in `CITATION.cff` remains empty (epistemic
  accuracy).

---

## 8. Security Embargo Authority

- The Project Owner may declare a temporary embargo on disclosing a vulnerability until
  remediation or a coordinated disclosure window closes.
- Embargoed work proceeds through private security advisories, not public PRs, until the
  embargo lifts.
- Once safe, the emergency-bypass rationale record (§6) is published.

---

## 9. Normative Change Approval

Changes to normative invariants, the formal model, or the spec are the highest-authority
changes. They require:

1. A spec-source update,
2. conformance/proof evidence (type-level or test-level), and
3. a recorded qualifying review (§3).

They contribute to the **next** paper/spec version — never to a silent edit of a
published deposit.

---

## 10. Conflict of Interest

- A maintainer who has a material conflict (employer, funding, commercial stake) on a
  change must disclose it and recuse from the qualifying review.
- During the solo phase, disclosure is recorded in the PR; recusal means engaging an
  external reviewer.

---

## 11. Governance Amendment

- Amendments to **this** document use pull requests.
- The **initial** repository creation is a bootstrap exception: the first commit is
  pushed directly because no protected default branch exists yet. **All** subsequent
  governance changes use pull requests.
- Amendments that weaken §1 (security / evidence-integrity / publication-integrity
  floors) are invalid even if merged.

---

## 12. Project Inactivity and Succession

- If the Project Owner becomes inactive for an extended period, a succession plan
  (documented privately) names a successor or archiver.
- A repository may be archived (read-only) but its published Zenodo/arXiv deposits
  remain immutable.

---

## 13. Repository Transfer, Archive, and End-of-Life

- Repository transfers preserve commit history, issues, PRs, and redirects only when
  done through GitHub's transfer mechanism (not `git push --mirror`).
- An end-of-life decision records: the last supported version, the final archive state,
  and the canonical pointer to any successor.

---

## 14. Appeal and Reconsideration

- A contributor may appeal a rejected PR or a governance decision by opening an issue
  with the label-free evidence (labels are bootstrapped separately) and requesting
  reconsideration.
- Appeals of high-risk decisions require new evidence or a corrected impact analysis;
  they are not re-litigated on preference alone.
