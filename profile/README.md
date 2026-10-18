# Fulcrum

**Pre-execution governance for routed AI agent tool calls, with receipts you can check.**

An agent proposes an action. [Fulcrum Boundary](https://github.com/Fulcrum-Governance/Fulcrum-Boundary) decides — allow, deny, warn, escalate, or require approval — *before* the tool runs, records a hash-verifiable decision, and only then lets execution proceed. Routed-only by design: Boundary governs the routes forced through it, and its docs say exactly what that does and does not cover.

---

## Start here: Fulcrum Boundary

```bash
brew install fulcrum-governance/tap/boundary
boundary demo github-lethal-trifecta   # watch a write-after-taint action denied before upstream
boundary demo tamper-evidence          # forge the receipt; watch verification refuse it
```

Also ships as [release binaries](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/releases/latest) with checksums, `docker pull ghcr.io/fulcrum-governance/boundary`, and `go install`. Demos are fixture-only: no credentials, no live calls, no real mutations.

- **Deterministic verdict path.** No model decides allow/deny locally; semantic rules escalate to a human or upstream system instead of guessing.
- **Records verifiable outside Boundary.** Decision records hash canonical bytes per RFC 8785 (JCS), scoped to the record — a stock RFC 8785 implementation recomputes the same `decision_hash`. That is a record-level statement, not a claim that Boundary as a whole is standards-conformant, and the hashes are integrity, not authenticity.
- **Honesty enforced by the build.** A machine-readable claims ledger and a public-language lint fail the build on overclaim. Clone it and run `go test ./claims/... -count=1` yourself.

## The Fulcrum stack

| Repo | Layer | License |
|------|-------|---------|
| **[Fulcrum-Boundary](https://github.com/Fulcrum-Governance/Fulcrum-Boundary)** | The action boundary: pre-execution decisions for routed agent tool calls, decision records, policy-as-code testing | Apache 2.0 |
| Fulcrum-Trust · Fulcrum-Proofs | Trust-modeling and Lean proof work, private during build. The Lean sources Boundary cites are in [docs/proofs/](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/tree/main/docs/proofs) | Apache 2.0 · MIT |
| **Fulcrum-IO** | Runtime control plane (commercial kernel: policy, budget, trust, escalation, audit) — private during build | BSL 1.1 |

The license posture is deliberate: the math is MIT (you cannot patent a theorem), the embeddable libraries are Apache 2.0 (enterprises need explicit patent grants in dependencies), and the hosted control plane is commercial. Boundary runs standalone with zero external dependencies; the kernel integration is opt-in.

## Where the proofs stop

Boundary's budget, trust and privilege behavior corresponds by design to machine-checked Lean 4 theorems. The sources it cites are in [docs/proofs/](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/tree/main/docs/proofs). That correspondence is a design constraint, not a runtime certificate: Boundary never emits a `proved` decision, and a passing record check does not prove an action was executed or prevented. The boundary between what is proved and what is asserted is documented, tested, and linted: [PROOF_BOUNDARY](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/blob/main/docs/PROOF_BOUNDARY.md) · [What It Does Not Prove](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/blob/main/LIMITATIONS.md) · [How we keep ourselves honest](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/blob/main/docs/HOW_WE_KEEP_OURSELVES_HONEST.md).

## Get involved

- **Discussions**: [Fulcrum-Boundary Discussions](https://github.com/Fulcrum-Governance/Fulcrum-Boundary/discussions) · issues on the relevant repo
- **Security**: [SECURITY.md](https://github.com/Fulcrum-Governance/.github/blob/main/SECURITY.md) — coordinated disclosure
- **Conduct**: [CODE_OF_CONDUCT.md](https://github.com/Fulcrum-Governance/.github/blob/main/CODE_OF_CONDUCT.md) · **Support**: [SUPPORT.md](https://github.com/Fulcrum-Governance/.github/blob/main/SUPPORT.md)
- **Web**: [fulcrumlayer.io](https://fulcrumlayer.io) · [docs.fulcrumlayer.io](https://docs.fulcrumlayer.io)

---

*Anthony Diefenbach, founder.*
