# Ontological Space

**Evidence-grounded protocols for navigating software as an ontological space.**

Ontological Space develops the **Ontological Space Protocol (OSP)** — a research
framework that models software projects as navigable conceptual spaces with
physics-like rules, BFT-inspired witnessing, and deterministic, evidence-backed
transitions. OSP connects architectural measurements, human intent, and AI-agent
actions through formal invariants enforced before mutation.

---

## Three Authority Surfaces

OSP separates where truth *lives* from where it is *explained*:

| Surface | Role | Mutability |
|---------|------|------------|
| **GitHub** | The living reference implementation | Evolves through PRs |
| **Zenodo / arXiv** | The immutable academic record (papers + evidence) | Never rewritten — only versioned |
| **[ontologicalspace.org](https://ontologicalspace.org)** | The canonical, human-readable map | Explains and points to the above |

---

## Three-Paper Research Arc

| # | Paper | Question | Status |
|---|-------|----------|--------|
| **1** | **Static Space** — *Modeling Software as a Conceptual Space with Epistemological Witnessing* | *Where* is software? | Published (Zenodo) |
| **2** | **Agent Trajectory Navigation** — *From Target Coordinates to Measurement Predicates* | How does an agent move *safely*? | Draft |
| **3** | **Concept Anchoring** — *From Human Sentences to Bound Project Work* | How does a human sentence become *measurable work*? | v1.4 on Zenodo |

The arc proceeds: **Static Space** (where software is) → **Agent Trajectory** (how an
agent moves safely) → **Concept Anchoring** (how a human sentence becomes bound work).

---

## Reference Implementation

The OSP reference implementation lives at
[`ontologicalspace/osp`](https://github.com/ontologicalspace/osp) — a Rust workspace
spanning the formal core, two-tier analyzer (tree-sitter + SCIP), an LLM runtime, a
CLI, an MCP server for AI agents, and a desktop visualizer.

```
coupling · cohesion · instability · entropy · witness-depth
```

Every module has a position in this five-axis space. Mutations pass through
deterministic validity gates before they are committed.

---

## Quick Links

- **Code:** [ontologicalspace/osp](https://github.com/ontologicalspace/osp)
- **Website:** [ontologicalspace.org](https://ontologicalspace.org)
- **Governance:** [GOVERNANCE.md](../GOVERNANCE.md) — the OSP authority model
- **Contributing:** [CONTRIBUTING.md](../CONTRIBUTING.md)
- **Security reporting:** [SECURITY.md](../SECURITY.md)

---

## Maturity

> OSP is a **pre-1.0 research protocol and reference implementation.** Interfaces and
> governance rules may evolve through evidence-backed revisions. Published deposits on
> Zenodo/arXiv are never rewritten — material changes produce a new version, corrigendum,
> or superseding record.

---

## License

The contents of this `.github` organization profile repository are licensed under
[Apache-2.0](../LICENSE). The OSP reference implementation and papers carry their own
license and citation metadata — see the respective repositories and `CITATION.cff`.
