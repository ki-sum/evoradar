# EvoRadar — How It Works

> A high-level overview of the engine's approach. No implementation details.

---

## Philosophy

Most AI idea generators start with a problem and bolt AI onto it. We tried that. The results were boring — every idea was a variation of "automate X with AI."

We flipped the approach: **start from what AI just made possible, then find who benefits.** The results were dramatically better. The data was unambiguous.

## Self-Evolving Engine

The engine isn't static. It learns from every generation cycle:

- Ideas that survive strengthen the patterns that produced them
- Ideas that get killed weaken those patterns
- Over time, the engine gets better at distinguishing promising ideas from noise

This means the engine today produces fundamentally different output than it did months ago.

## Rigorous Evaluation

Every idea goes through multiple rounds of scrutiny. The engine actively searches for competitors, checks market timing, stress-tests the business model, and verifies that real customers would actually pay.

A single fatal weakness — regardless of other strengths — kills the idea. This mirrors how real startups fail: from their worst dimension, not their average.

## What the Engine Catches

Through thousands of evaluations, the engine developed an instinct for common failure modes:

- **"Just add AI"** — Ideas that merely automate an existing process. No defensibility, instant competition.
- **Structural adoption barriers** — When the target customer has hidden reasons to reject the solution, even if it's better.
- **Platform dependency** — Building entirely on someone else's platform with no fallback.
- **"The market will be ready soon"** — If you can't charge today, the idea isn't viable today.

## Global Signal Awareness

The engine monitors technology breakthroughs, regulatory changes, and market shifts across multiple industries and regions. These signals determine what the engine thinks about — and therefore what ideas it can imagine.

This wasn't the original approach.

The first version of the engine started from **imagination** — combining unrelated capabilities and seeing what fell out. Creative, but unfocused. The next version tried what most accelerators preach: **start from user pain.** That produced a flood of "AI [tool] for [profession]" ideas, most of which failed evaluation for the same small set of reasons.

What survived, run after run, were ideas anchored to something real that had just changed in the world: a new technology becoming cheap, a new regulation creating an obligation, a new behavior crossing a tipping point. So the engine evolved toward those signals. Imagination is still in the loop — but now it has somewhere to point.

## Content Model

- **Free**: See killed ideas and why they failed — demonstrates the engine's rigor
- **Paid**: Unlock full analysis — risk profiles, competitive landscapes, market strategies
- **VIP**: Custom generation runs tailored to your chosen industries and markets

## Privacy & Data

Every piece of infrastructure runs in the EU. The application server lives in
Frankfurt (Hetzner). Analytics are PostHog's EU region. Error tracking is
Sentry's EU region. There is no data path to the United States in normal
operation, which keeps Schrems II analysis short and Chapter V transfer
mechanisms unnecessary.

Tracking is deliberately conservative. PostHog autocapture is off and session
recording is disabled, so the platform never sees what visitors click or type
beyond the page they're on. PostHog runs only after a visitor accepts the
cookie banner. Error tracking runs by default under legitimate-interest
grounds — with a one-click opt-out on the privacy policy page — because
unaddressed bugs hurt every user, and we'd rather know they exist. Email
addresses and IP addresses are scrubbed from error events before they leave
the server.

The complete sub-processor list is at
[`/sub-processors`](https://evoradar.ai/sub-processors). A Legitimate Interest
Assessment for error tracking is filed internally and reviewed annually.

---

*The engine evolves continuously. This describes its approach, not its implementation.*
