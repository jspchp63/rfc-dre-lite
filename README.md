# RFC-DRE Lite — Minimal Coherence Recovery Demo

> **Purpose**
>  
> Show, with executable code, that **context / coherence can be partially restored
> without transport-based memory**, using resonance-style reconstruction.
>  
> This is **not** HROS-6, **not** a full OS, and **not** a product claim.  
> It is a **minimal, falsifiable demo**.

---

## What this repository is

RFC-DRE Lite is a **research-grade demo** that implements:

- Local signal / state encoding
- Resonance-based similarity reconstruction
- Cross-session coherence recovery (pattern-based, not memory replay)
- Observable difference vs naïve stateless restart

This repo exists to answer **one practical question**:

> Can coherence be partially recovered **without transporting full state**?

---

## What this repository is NOT

- ❌ Not a full RFC-DRE engine  
- ❌ Not HROS-6  
- ❌ Not a commercial SDK  
- ❌ Not long-term memory  
- ❌ Not an LLM replacement  

If you are looking for a finished product, stop here.

---

## Demo Overview (What you can actually see)

The demo shows **three phases**:

1. **Session A**
   - Input sequence produces an internal resonance profile
2. **Session Break**
   - No stored conversation, no replay
3. **Session B**
   - New input reconstructs prior coherence pattern
   - Output differs from stateless baseline

Key point:  
**Reconstruction ≠ memory storage**

---

## How to Run (Local)

```bash
git clone https://github.com/yourname/rfc-dre-lite.git
cd rfc-dre-lite
python demo/demo_rfc_dre_lite.py
Expected output:

Coherence score

Baseline vs reconstructed divergence

Simple plot or printed metric

Metrics (Visible, Not Claimed)

Coherence Index (CI)

Pattern Overlap Ratio (POR)

Drift vs Recovery delta

These are illustrative, not benchmarks.

Relation to RCIRCUIT

RCIRCUIT: transport-free phase compute (theory + simulation)

RFC-DRE Lite: coherence reconstruction demo (software-level)

RFC-DRE Lite does not prove RCIRCUIT.
It demonstrates a compatible failure-recovery principle.

Why this matters

Modern AI systems fail coherence because:

Context is moved

State is serialized

Meaning is reconstructed via transport

This demo shows a different direction:
coherence via local pattern resonance, not recall.

Status

Research demo

Alpha quality

Single-file runnable

No guarantees

No commercial license

License

Research / evaluation only.
No commercial use without permission.

Author

Chulhee Park
Concept: Transport-free coherence & resonance reconstruction# rfc-dre-lite
