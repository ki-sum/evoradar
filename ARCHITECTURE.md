# EvoRadar Architecture Overview

> This document describes the engine's design philosophy and high-level architecture.
> No source code or implementation details are included.

---

## Core Philosophy: Capability-First > Problem-First

Early versions of the engine started from problems ("who has pain?") and worked toward solutions. This produced ideas that were obvious, crowded, and boring — what we call the **"AI fills a form"** pattern. Every idea was some variation of "take a manual workflow, add AI to automate it."

The breakthrough came from inverting the approach: **start from what just became technically possible, then ask who benefits.**

This is not a theoretical preference. We tested both approaches at scale:
- Problem-first ideas had an 8x higher kill rate
- Capability-first ideas produced the highest-scoring survivors
- The data was unambiguous

The engine now runs three flavors (Capability, Painpoint, Crossdomain), but the capability-first lens influences all of them.

## Self-Evolving Gene System

The engine's behavior is controlled by **74 genes** — parameters that shape how it generates, evaluates, and selects ideas. These are not static configuration values. They mutate.

**How evolution works:**
1. After each generation run, the engine examines what survived and what died
2. Genes that contributed to high-scoring survivors get reinforced
3. Genes that consistently produced killed ideas get suppressed or mutated
4. New genes can emerge when the engine identifies a gap in its evaluation capability

**Example genes** (names only, values are proprietary):
- Variable Boldness — controls how aggressively the engine explores unfamiliar territory
- Platform Risk Sensitivity — how heavily the engine penalizes dependence on third-party platforms
- Regulatory Awareness — weighting of regulatory risk across different jurisdictions

The gene system means the engine today is fundamentally different from the engine six months ago. It learned.

## Three-Layer Evaluation

Every idea passes through three evaluation layers. There are no shortcuts.

### Pass 1: Thinking
The engine reasons through the idea from first principles. This is not a checklist — it is genuine analytical reasoning about market dynamics, technical feasibility, competitive landscape, and business model viability. The engine's full thinking trace is recorded and available for replay.

### Pass 2: Deepening + Competitive Verification
The engine actively searches for existing competitors and adjacent solutions. This pass was added after discovering that early versions would enthusiastically score ideas that already had well-funded competitors. The engine now asks: *"Has someone already built this? If not, why not — and is that reason structural or merely timing?"*

### Pass 3: Extraction + Scoring
Final scoring across 7 risk dimensions. The scoring uses geometric mean (not additive) — a single catastrophic weakness kills the idea regardless of other strengths. This is intentional. Real startups die from their worst dimension, not their average.

## Anti-Patterns the Engine Detects

Years of running the engine revealed recurring failure modes. These are now hardcoded as detection rules:

### "AI Fills a Form"
Any idea whose core value proposition is "take a manual process and automate it with AI" gets flagged. These ideas are trivially replicable, have no defensibility, and compete on price from day one. The engine learned to reject these in v2.

### The Pastor Effect
Named after a pattern where the target customer has **structural reasons to reject the solution**, even if the solution is objectively better. Example: a tool that makes a professional's judgment unnecessary — the professional will never buy it, regardless of quality. The engine checks whether the buyer and the displaced party are the same person.

### Platform Risk Blindness
Ideas that depend entirely on a single platform (an API, a marketplace, a social network) without a migration path. The engine learned this the hard way — several early high-scoring ideas were essentially "build on top of X" where X could change its terms overnight.

### Market Timing Delusion
"The market isn't ready yet, but it will be in 2-3 years." The engine treats this as a kill signal, not a reason for patience. If you cannot charge from day one, the idea is not viable today.

## Signal Matrix

The engine maintains a curated signal matrix:

- **248 signals** across **25 industries** and **5 geographic regions**
- Signals include: technology breakthroughs, regulatory changes, market shifts, funding patterns, talent movements
- Each signal has a freshness score — stale signals get deprioritized automatically
- Regional signals cover US, EU, China, and emerging markets with region-specific dynamics

The signal matrix is the engine's view of the world. It determines what the engine thinks about, which in turn determines what ideas it can imagine.

## Content Protection

EvoRadar's output is its product. Multiple protection layers ensure that free-tier users get value (understanding why ideas fail) while paid content remains gated:

1. **Generation-time sanitization** — Internal scoring codes and methodology details are stripped during idea generation
2. **Post-processing sanitization** — A dedicated pipeline scrubs any remaining internal references before publication
3. **Content gating** — Risk scores, detailed analysis, competitive landscapes, and go-to-market strategies are behind the paywall
4. **VIP exclusivity** — Custom generation runs and deep evaluations are VIP-only

The engine's evaluation methodology — how it scores, what weights it uses, how genes interact — is proprietary and not exposed through any tier.

---

*This document describes the architecture as of v8 (March 2026). The engine evolves continuously.*
