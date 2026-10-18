# Security Policy

## Reporting a vulnerability

Please report suspected vulnerabilities in any Fulcrum-Governance repository to:

- **Email**: agent@fulcrumlayer.io (subject prefix `[security]`)
- **PGP**: optional — request key over email if needed for sensitive details

Do **not** open a public GitHub issue for a vulnerability report. Use email first; we will move to a private GitHub Security Advisory after triage.

## Scope

This policy covers every repository under the Fulcrum-Governance organization, public or private.

| Repo | License | Surface |
|------|---------|---------|
| [Fulcrum-Boundary](https://github.com/Fulcrum-Governance/Fulcrum-Boundary) | Apache 2.0 | Action boundary: MCP proxy, adapters, decision records (includes the Lean sources in docs/proofs/) |
| [homebrew-tap](https://github.com/Fulcrum-Governance/homebrew-tap) · [boundary-plugins](https://github.com/Fulcrum-Governance/boundary-plugins) | | Boundary install and plugin metadata |
| Fulcrum-IO, Fulcrum-Trust, Fulcrum-Proofs (private during build) | BSL 1.1 · Apache 2.0 · MIT | Hosted control plane, trust engine (`fulcrum-trust` on PyPI), Lean proofs. Report by email. |

### In scope
- Code execution, privilege escalation, or bypass of a governed route in Fulcrum-Boundary adapters
- Authentication or authorization bypass in Fulcrum's hosted REST or MCP surfaces
- Trust-state corruption or replay vectors against the `fulcrum-trust` package
- Soundness flaws in the Lean sources Boundary cites (docs/proofs/), e.g. a theorem that does not establish what its citation claims, or an unintended axiom dependency
- Supply-chain compromise of vendored dependencies

### Out of scope (by design, not by neglect)
- The **Isolation Axiom** in the Fulcrum-Proofs Lean sources (`RLMContracts.lean`) is a deployment contract, not a runtime guarantee. Container-escape vulnerabilities in the kernel/hypervisor underneath the proof layer are out of scope here — please report those upstream (gVisor, Firecracker, Linux kernel).
- The pure-Python sandbox in `fulcrum-trust` (RLMRuntime exec model) is documented as bypassable. Standard CPython sandbox-escape techniques are not novel findings.
- Theoretical attacks without a working proof-of-concept.
- Vulnerabilities in third-party dependencies beyond our pinned versions — please report upstream first; we will track downstream fixes.

## Coordinated disclosure

We follow a **90-day coordinated disclosure** window:

1. You report the issue privately to `agent@fulcrumlayer.io` with subject prefix `[security]`.
2. We acknowledge within 5 business days.
3. We investigate, validate, and prepare a fix.
4. We agree on a disclosure date with you (typically the patch ship date).
5. We publish a GitHub Security Advisory and credit you (unless you prefer anonymity).

If 90 days pass without a fix or a mutually agreed extension, you are free to publish.

## What we will not do

- We will not pursue legal action against good-faith researchers operating under this policy.
- We will not gag-order researchers; the disclosure date is collaborative.
- We will not silently patch and deny credit.

## Acknowledgements

Researchers who report valid vulnerabilities under this policy are credited in the Security Advisory and in the relevant repository's CHANGELOG (with permission).

---

*Policy last updated 2026-10-17.*
