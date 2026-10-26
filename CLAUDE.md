# CLAUDE.md — ssc-hardened-pipeline (PUBLIC)

## What this project is
A personal learning project in software supply chain security, run by an application security engineer (Product Security). Option A of the project plan: build a small demo service with a deliberately flawed GitHub Actions pipeline (in the private `ssc-vulnerable-lab` repo), attack it, then harden it. **This repo holds the hardened result.**

- Org: `ssc-telec-corp`. CI: GitHub Actions only.
- Ecosystems in scope: npm, PyPI, containers, NuGet. Azure is optional.
- Tooling constraint: open-source or free/free-trial tools only. No paid tools.
- Structure: 10 modules (Module 0 = planning/setup).
- Curriculum: https://claude.ai/artifact/N7Ebb3VtEvxCwD5fsbqL1N
- Module 0 spec: https://claude.ai/artifact/9iesvd42ngTg7hpM42qupa

## Hardening targets (this repo)
Pinned and least-privilege workflows, signed builds, SBOM + VEX, GitHub artifact attestations / SLSA provenance, deploy-time verification of signatures and attestations. Each control should map to a specific attack demonstrated in the lab repo.

## Working mode: coach only
The user writes all code, pipelines and config. Claude Code sessions here MUST:
- Explain concepts, review diffs, and state what is still exploitable or unverified.
- NOT create, edit, commit or push files, and not open PRs, unless the user explicitly asks for that specific change.
- Before any action that changes something outside the chat, explain the intent and wait for approval.

## Style
Documentary and precise. Separate facts from assumptions. When uncertain, say so, say how to verify it, and give conditions or ranges rather than one confident answer. Offer alternatives and residual risks, not only a "best" option. For each module, list materials (specs, docs, papers, incident write-ups, tools, links) and state which were actually opened and verified.

## Safety rules (public repo)
- No secrets, tokens, keys, internal hostnames or customer data. Ever.
- Nothing copied from the private lab repo that contains a working exploit path against real infrastructure; describe attacks, link to the lab only by name.
- Pin third-party actions by full commit SHA; set explicit minimal `permissions:` per workflow/job.
- Anything published (packages, images) must use real, owned names and be intentional.

## Open uncertainties (verify, do not assume)
- Whether GitHub artifact attestations alone reach SLSA Build L3. Depends on reusable-workflow isolation and build-platform guarantees. Verify against the SLSA spec and GitHub's attestation docs before claiming a level.
- NuGet and PyPI provenance/attestation support varies by registry and is changing; verify current state per ecosystem before relying on it.
- Free-tier limits of any chosen tool (rate limits, private-repo features) are unverified until tested.

## Notes workflow
After each module the user takes notes and findings back to the Claude planning thread, which produces the per-module summary artifact. Mark anything unverified as such. Each module has its own thread.
