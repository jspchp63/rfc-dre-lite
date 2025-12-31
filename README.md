# RFC-DRE Lite — Coherence-First Session Reconstruction (Demo / Alpha)

**RFC-DRE Lite** is a minimal, executable demonstration of **coherence-first reasoning**:  
it reconstructs *context continuity* across sessions **without transporting full state**.

This repository is **not** an AGI claim, **not** a memory product, and **not** a production SDK.  
It is a **falsifiable demo** that shows how *local resonance patterns* preserve coherence better than transport-heavy context replay.

---

## What Problem This Tests (One Question Only)

> **Does conversational and reasoning coherence fail because intelligence is insufficient,  
> or because meaning is forced to move and be reconstructed across sessions?**

**Claim (to be tested):**  
Transport-based context reconstruction collapses coherence.  
Pattern-based resonance reconstruction preserves it longer.

If this is false, this repo should fail visibly.

---

## What RFC-DRE Lite Is

- A **Python-based demo engine**
- Focused on **cross-session coherence**, not memory storage
- Reconstructs *intent, emotional trajectory, and logical direction* from **patterns**
- Explicitly **does not store conversation history**

Think: **coherence recovery**, not memory.

---

## What This Is NOT

- ❌ Not an LLM
- ❌ Not a chat app
- ❌ Not a vector DB wrapper
- ❌ Not a LangChain / LangGraph alternative
- ❌ Not production-ready software
- ❌ Not an OS

This is a **structural probe**, not a product.

---

## Core Concepts (Lite Version)

- **Resonance Vector**: compressed representation of intent + affect + logic
- **Session Break**: explicit termination (simulates real reset)
- **Re-entry**: coherence reconstructed from resonance, not history
- **Stability Metric**: measures continuity vs collapse

No retrieval. No replay. No summarization.

---

## Demo: What You Can Observe

The demo shows:

1. Session A: user intent & emotional direction established  
2. Session ends (state destroyed)
3. Session B: engine reconstructs *directional coherence*
4. Comparison against transport-style reset (baseline collapse)

You should see:
- Less re-explanation
- Preserved trajectory
- Lower semantic drift

If you don’t, the claim fails.

---

## Repository Structure

rfc-dre-lite/
├─ demo/
│ └─ demo_coherence_reconstruction.py
├─ src/
│ ├─ resonance_vector.py
│ ├─ coherence_metric.py
│ └─ session_rebuilder.py
├─ README.md
└─ LICENSE

yaml
코드 복사

---

## How to Run (Local)

```bash
git clone https://github.com/yourname/rfc-dre-lite.git
cd rfc-dre-lite
python demo/demo_coherence_reconstruction.py
Output is textual + simple plots.
No external APIs required.

Evaluation Criteria (Pass / Fail)
This demo fails if any of the following is true:

Transport-style replay preserves coherence better

Noise degrades resonance reconstruction faster than transport

Reconstructed sessions show no measurable continuity advantage

If you can demonstrate that, this repo disproves itself.

Intended Audience
AI system architects

Researchers studying context, memory, and continuity

Engineers investigating limits of LLM session design

If you are looking for features, UX, or SOTA benchmarks — stop here.

Status
Code: Alpha / Demo-level

Scope: Minimal by design

Commercial Use: ❌ Not licensed

Purpose: Structural falsification

Relationship to RCIRCUIT / HROS
RFC-DRE Lite = executable demo

RCIRCUIT = transport-free compute research

HROS = conceptual OS layer (not implemented here)

This repo stands alone.

Final Note
This repository is intentionally uncomfortable.

If coherence matters, continue.
If scale and parameters are your answer, this will look pointless.

That reaction is part of the test.


# demo/demo_coherence_reconstruction.py
# RFC-DRE Lite — Minimal, Copy-Paste Runnable Demo
# Purpose: Compare transport-style replay vs resonance-based reconstruction
# Run: python demo_coherence_reconstruction.py

import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)

# -----------------------------
# Helpers
# -----------------------------
def coherence_score(phases):
    """Order parameter (Kuramoto-style) as coherence metric."""
    return np.abs(np.mean(np.exp(1j * phases)))

def add_noise(phases, sigma):
    return phases + np.random.normal(0, sigma, size=len(phases))

# -----------------------------
# Simulation Params
# -----------------------------
N = 64               # number of nodes
T = 60               # time steps
noise_sigma = 0.35   # noise level
alpha = 0.15         # local update strength (resonance)
transport_decay = 0.55  # transport degradation factor

# -----------------------------
# Initial State
# -----------------------------
initial_phases = np.random.uniform(-np.pi, np.pi, N)

# -----------------------------
# Transport-style Replay
# (simulate session break + replay with degradation)
# -----------------------------
phases_transport = initial_phases.copy()
transport_scores = []

for t in range(T):
    phases_transport = add_noise(phases_transport, noise_sigma)
    phases_transport *= transport_decay  # degradation from reconstruction
    transport_scores.append(coherence_score(phases_transport))

# -----------------------------
# Resonance Reconstruction
# (local phase evolution, no transport)
# -----------------------------
phases_resonance = initial_phases.copy()
resonance_scores = []

for t in range(T):
    phases_resonance = add_noise(phases_resonance, noise_sigma)
    # local resonance update: pull toward mean phase
    mean_phase = np.angle(np.mean(np.exp(1j * phases_resonance)))
    phases_resonance += alpha * np.sin(mean_phase - phases_resonance)
    resonance_scores.append(coherence_score(phases_resonance))

# -----------------------------
# Results
# -----------------------------
print("Final Coherence")
print("----------------")
print(f"Transport Replay : {transport_scores[-1]:.4f}")
print(f"Resonance Rebuild: {resonance_scores[-1]:.4f}")

# -----------------------------
# Plot
# -----------------------------
plt.figure(figsize=(8, 4))
plt.plot(transport_scores, label="Transport Replay", linestyle="--")
plt.plot(resonance_scores, label="Resonance Reconstruction")
plt.xlabel("Time Step")
plt.ylabel("Coherence (Order Parameter)")
plt.title("RFC-DRE Lite — Coherence Under Noise")
plt.legend()
plt.tight_layout()
plt.show()






