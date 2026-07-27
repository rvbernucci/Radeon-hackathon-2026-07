# SignalForge - AMD AI DevMaster Hackathon Track 2 Submission

| Field | Value |
|---|---|
| Track | Track 2 - Development and Local Deployment of Private AI Agents |
| Team | SignalForge Labs |
| Application | SignalForge |
| Team member | Rafael Bernucci - product architecture, financial domain design, evaluation strategy, and release ownership |
| Championship source | [`032e9c38c4e74a450b38fec8341ed540b6339170`](https://github.com/rvbernucci/signalforge/commit/032e9c38c4e74a450b38fec8341ed540b6339170) |
| Championship release | [`v1.1.0`](https://github.com/rvbernucci/signalforge/releases/tag/v1.1.0) |
| Public image | `ghcr.io/rvbernucci/signalforge:v1.1.0` |
| Image digest | `sha256:1354ccbbbd6138119111e23657ad69c1665f4189d75b9adcdecd53084870a4af` |
| Canonical repository | [github.com/rvbernucci/signalforge](https://github.com/rvbernucci/signalforge) |
| Judge guide | [SignalForge Judge Guide](https://github.com/rvbernucci/signalforge/blob/main/JUDGES.md) |

## Submission Materials

- [Project specification PDF](https://github.com/rvbernucci/signalforge/releases/download/sprint34-artifacts-v1/SignalForge-Project-Specification.pdf)
- [4 minute 12.9 second AMD Radeon demo video](https://github.com/rvbernucci/signalforge/releases/download/sprint34-artifacts-v1/SignalForge-Radeon-Demo.mp4)
- [Six-slide judge deck](https://github.com/rvbernucci/signalforge/releases/download/sprint34-artifacts-v1/SignalForge-Judge-Deck.pptx)
- [Architecture diagram](https://github.com/rvbernucci/signalforge/releases/download/sprint34-artifacts-v1/architecture.svg)
- [Track 2 compliance matrix](https://github.com/rvbernucci/signalforge/blob/main/docs/track2-compliance.md)
- [Exact release attestation](https://github.com/rvbernucci/signalforge/blob/main/evidence/sprint34-release-attestation.json)

The complete immutable `v1.1.0` source snapshot, documentation, deterministic fixtures, tests,
evidence, PDF, deck, and video are included under `source/`.

## Product

SignalForge is a private, local-first financial research desk. It turns public SEC filings,
official investor-relations evidence, macroeconomic series, and market observations into an
inspectable research case rather than an opaque chat answer.

The recorded journey compares Microsoft and NVIDIA as long-term businesses under explicit
higher-rate and slower AI-infrastructure-spending scenarios. The product separates readable
analysis from primary evidence, deterministic calculation receipts, assumptions, limitations,
counterevidence, and thesis-invalidation conditions. It supports research and education; it does
not predict prices, execute trades, or provide personalized investment recommendations.

## Architecture

1. A typed interpreter closes the research intent and scope.
2. A Go-owned orchestrator creates a bounded plan and fans out to at most four specialists at once.
3. A Context Compiler retrieves authorized evidence, preserves conflict, and enforces a budget.
4. Eighty role-authorized deterministic financial operations own values, units, periods, formulas,
   relations, and immutable receipts.
5. Independent Evidence and Risk critics disposition every releasable claim.
6. One final local analyst synthesizes the approved qualitative draft.
7. A Go Answer Compiler joins approved claims to citations, receipts, and numerical references.
8. A React workspace streams a safe expandable execution plan without exposing private reasoning.

All 11 logical roles share one local Gemma runtime with role-specific prompts and strict contracts.
The local path is loopback-only on AMD Radeon through ROCm and `llama.cpp`. The optional hybrid path
routes bounded context specialists through the organizer-provided Radeon API while retaining local
review, synthesis, deterministic authority, and authorized local fallback.

## Track 2 Capabilities

| Capability | SignalForge evidence |
|---|---|
| Local knowledge retrieval | Point-in-time SEC and official investor-relations evidence with resolvable citations and lineage |
| Tool invocation | 80 typed deterministic financial operations with authorization and immutable receipts |
| Multi-step task planning | Interpreter, bounded specialist waves, independent critics, and one final synthesis |
| Local multi-turn memory | Governed follow-ups plus opt-in inspect, export, and delete controls |
| Permission and privacy | Loopback-only local inference, read-only model authority, secret rejection, private traces, and fail-closed release |

SignalForge implements all five capability families listed by Track 2.

## AMD Radeon And ROCm Evidence

- Environment: AMD Radeon Cloud, Radeon `gfx1100`, ROCm 7.2.1.
- Runtime: hash-pinned ROCm `llama.cpp` with Gemma 4 26B A4B Instruct QAT Q4_0 GGUF.
- Baseline: 40/40 deterministic contract checks and 86.46 median decode tokens/s.
- Accepted optimization: four context workers, unified F16 KV, continuous batching, and flash
  attention `auto`.
- Workload result: 44/44 frozen semantic checks in 157.47 seconds, 29.17% faster end to end than
  the passing three-worker control.
- Local Sprint 34 journey: all 12 terminal steps across eight governed phases, 11 local ROCm calls,
  and an accepted release.
- Hybrid Sprint 34 journey: all 12 terminal steps, 17 calls across `radeon-vllm` and `local-rocm`,
  local review/synthesis, and tested API-loss fallback.

These are bounded, hash-backed workload results, not universal accuracy or performance claims.

## Reproduce

The deterministic fixture requires no GPU, API key, model download, database setup, or external
data call:

```bash
git clone --branch v1.1.0 --depth 1 https://github.com/rvbernucci/signalforge.git
cd signalforge
npm --prefix web ci
npm --prefix web run build
go run ./cmd/signalforge-workspace --mode fixture --static-dir web/dist
```

Open `http://127.0.0.1:8080`. The `source/` directory in this PR is the same immutable Git tree.
Its README documents dependencies, environment configuration, the live Radeon path, model revision,
model hash, runtime revision, troubleshooting, container surfaces, and verification.

Pull the exact application image by digest:

```bash
docker pull \
  ghcr.io/rvbernucci/signalforge@sha256:1354ccbbbd6138119111e23657ad69c1665f4189d75b9adcdecd53084870a4af
```

## Release Integrity

The application image is public `linux/amd64`, runs as `10001:10001`, and contains no credentials,
model weights, private corpora, or startup downloads. The container workflow produced SBOM and
provenance, passed a Trivy HIGH/CRITICAL scan, and verified an anonymous digest pull plus clean
fixture execution.

The source snapshot is frozen at `v1.1.0`. The two files beside this README,
`release-checklist-final.json` and `sg05-attestation.json`, bind the exact source, image, workflows,
judge artifacts, human decisions, and release authorization. Artifact hashes are listed in
`SHA256SUMS`.
