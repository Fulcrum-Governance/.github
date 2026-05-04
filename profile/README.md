# Fulcrum

**Provably-bounded governance for autonomous AI agents.**

Microsoft's Agent Governance Toolkit ships 13,000 tests. We ship zero-sorry mechanized Lean 4 proofs that bound the same governance invariants. When an audit demands evidence, the difference is admissible.

---

## The four-repo open-core stack

| Repo | Layer | Wedge | License |
|------|-------|-------|---------|
| **[fulcrum-io](https://github.com/Fulcrum-Governance/fulcrum-io)** | Runtime control plane | Policy engine, execution envelope, MCP proxy, governance dashboard | BSL 1.1 → Apache 2.0 (2030-05-04) |
| **[governance-interception-layer](https://github.com/Fulcrum-Governance/governance-interception-layer)** | Enforcement boundary | Protocol-agnostic adapters (MCP / CLI / code-exec), 4-stage pipeline | Apache 2.0 |
| **[fulcrum-trust](https://github.com/Fulcrum-Governance/fulcrum-trust)** | Trust engine | Beta(α,β) circuit breaker, runaway-loop termination, agent-pair trust state | Apache 2.0 |
| **[Fulcrum-Proofs](https://github.com/Fulcrum-Governance/Fulcrum-Proofs)** | Formal core | Lean 4 mechanized proofs, claim ledger, kernel-3 axiom profile, 0 sorrys | MIT |

---

## Why this exists

In April 2026 alone — Microsoft, OpenAI, Cisco, and Palo Alto Networks each shipped or acquired into agent governance. Every one of them picked the orchestration layer. None picked formal verification.

The category has been validated. The proof primitive remains open.

Fulcrum is the deployer-side primitive that the orchestrators explicitly punt to. We're protocol-agnostic (MCP + CLI + code-exec adapters), evidence-grade (machine-checkable Lean 4 theorems with documented axiom profile), and decision-named (every action returns one of: *proved* / *deterministic* / *classified* / *human-approved*).

---

## Three-layer license posture

We're not "closed source." We're not "everything Apache." We're deliberate:

- **Layer 1 — math is foundational knowledge.** Lean 4 proofs are MIT. You can't patent a theorem; pretending otherwise is bad-faith open source.
- **Layer 2 — implementation libraries embed in your stack.** Trust SDK and the enforcement boundary are Apache 2.0. Enterprise legal teams require explicit patent grants when they install a dependency.
- **Layer 3 — runtime control plane is a commercial product.** fulcrum-io ships under BSL 1.1 with an explicit conversion date (May 4, 2030) to Apache 2.0. AWS doesn't get to fork-and-host us during the build phase; the OSS narrative remains intact via the conversion clause.

This posture mirrors AWS Cedar (Apache 2.0 verifier + commercial managed service), MongoDB / Sentry / CockroachDB / Elastic / HashiCorp BSL precedents (commercial runtime + scheduled OSS conversion), and the Lean / Mathlib / Coq cultural norm of always-open formal cores.

---

## Latest

- **D4 preprint** — *Provably-Bounded Governance Invariants for Autonomous AI Agents* — [PDF](https://fulcrumlayer.io/papers/d4.pdf) · arXiv submission pending endorsement · Zenodo DOI to follow on first tagged release.
- **GIL** — protocol-agnostic enforcement boundary, 241 tests, 98.2% coverage, Apache 2.0.
- **Fulcrum-Proofs** — kernel-3 axiom profile, 0 sorrys repo-wide, 18+ theorems mapped to runtime invariants, MIT.
- **fulcrum-trust** — Beta(α,β) trust engine on PyPI, 186 tests, 95.65% coverage.

---

## Use Fulcrum

- **Try it**: [docs.fulcrumlayer.io](https://docs.fulcrumlayer.io)
- **Read the proofs**: [Fulcrum-Proofs](https://github.com/Fulcrum-Governance/Fulcrum-Proofs) → run `bash proofs/reproduce.sh`
- **Web**: [fulcrumlayer.io](https://fulcrumlayer.io)

---

## Get involved

- **Issues + discussion**: open on the relevant repo
- **Security**: see [SECURITY.md](https://github.com/Fulcrum-Governance/.github/blob/main/SECURITY.md) — 90-day coordinated disclosure
- **Code of Conduct**: see [CODE_OF_CONDUCT.md](https://github.com/Fulcrum-Governance/.github/blob/main/CODE_OF_CONDUCT.md) — Contributor Covenant 2.1
- **Support**: see [SUPPORT.md](https://github.com/Fulcrum-Governance/.github/blob/main/SUPPORT.md)

---

*Anthony Diefenbach, founder · Y Combinator S2026 applicant.*
