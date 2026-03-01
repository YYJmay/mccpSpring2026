# Presentation Outline — A Recipe for Causal Graph Regression

**Paper:** Yin, Y., Qu, T., Wang, Z., & Chen, Y. (2025). A Recipe for Causal Graph Regression: Confounding Effects Revisited. *ICML 2025*, Vancouver. PMLR 267.

**Duration:** 8 minutes &bull; **Slides:** 9

---

## Opening: Hook + Problem (~1 min) — Slides 1-2

### Speaker cues
- "Imagine predicting how soluble a new drug molecule is — not yes/no, but an exact number."
- Most AI today learns shortcuts: molecular weight correlates with solubility but doesn't cause it.
- When the data changes (new molecule types), shortcuts break. This is the OOD problem.
- Our paper asks: **how do we teach AI to find the real causes inside a graph, not the shortcuts — when the answer is a number, not a category?**

### Key terms to define (once, simply)
| Term | Plain-English definition |
|---|---|
| **Graph** | A network of connected nodes — like atoms connected by bonds in a molecule |
| **Causal subgraph** | The part of the graph that truly decides the outcome (green) |
| **Confounding subgraph** | The part that only looks related by coincidence (red) |
| **OOD (out-of-distribution)** | New data the model has never seen during training |

### Presenter notes
- **Delivery:** Open conversationally. Make eye contact. Pause after "an exact number" for effect.
- **Visual:** Title slide → Slide 2 with molecule icon split into green (causal) / red (confounding) parts.
- **Transition:** "So what makes regression so much harder than classification? Let me explain."

---

## Section 1: Why Regression Breaks Prior Methods (~2 min) — Slide 3

### Speaker cues
- Classification: "Is this toxic? YES or NO" → finite categories → you can group graphs by label.
- Regression: "How toxic? 37.2 on a scale..." → continuous → no natural groupings.
- Prior causal graph methods **depend on class labels** to perform causal intervention (e.g., backdoor adjustment mixes graphs within the same class).
- With continuous labels, this label-dependent strategy **simply doesn't work**.
- Another flawed assumption: prior methods treat confounders as **pure noise with zero predictive power**. But in reality, molecular weight is non-causal to toxicity yet strongly predictive. Ignoring confounders loses useful information and hurts disentanglement.

### Presenter notes
- **Delivery:** Use the "YES/NO vs. 37.2" contrast with hand gestures. Slow down on "simply doesn't work."
- **Visual:** Left side: two bins (YES / NO). Right side: continuous number line. Red X over "group by label."
- **Transition:** "We solved both problems. Let me show you how."

---

## Section 2: Our Method — Enhanced GIB + Contrastive Intervention (~3 min) — Slides 4-6

### Slide 4 — Enhanced GIB Objective

**Speaker cues:**
- Standard approach (GIB): force the causal subgraph C to capture ALL predictive info; treat confounder S as noise.
- Our insight: S is predictive too (just not causal). If we ignore S's predictive role, C gets overloaded → poor separation.
- Enhanced GIB adds a term: let S predict Y too (with weight β), so C is freed to capture only the causal signal.
- Conceptually: **"Don't ignore the confounder — understand it, so you can separate it properly."**

**Presenter notes:**
- **Visual:** Boxed diagram: G → split into C (green) and S (red) → both predict Y, but C is direct, S is indirect.
- **Delivery:** One boxed takeaway on slide: "Enhanced GIB = let confounders predict too → cleaner separation." No equations on slide.

### Slide 5 — Contrastive-Learning-Based Causal Intervention

**Speaker cues:**
- Prior methods: mix causal part of graph i with confounder of graph j, then predict Y using the class label → label-dependent, breaks for regression.
- Our approach: instead of predicting labels, use **contrastive learning** (InfoNCE-style).
  - Mix causal part of graph i + random confounder of graph j → create a "counterfactual" mixed graph.
  - Positive pair: original graph representation ↔ its mixed version (same causal core).
  - Negative pairs: representations of all other graphs in the batch.
  - The model learns: "a graph and its counterfactual (same cause, different confounder) should look similar; unrelated graphs should look different."
- This removes the need for discrete labels entirely → **works for regression**.

**Presenter notes:**
- **Visual:** Three nodes in a row: "Real graph ✓" — "Counterfactual (same cause) ✓" — "Other graph ✗". Arrows showing positive/negative pairing.
- **Delivery:** Explain contrastive learning as "learning to spot the real graph among plausible fakes." Pause after the analogy.

### Slide 6 — Putting It Together

**Speaker cues:**
- Total loss: L = L_GIB + λ · L_CI
- Pipeline: GNN encodes graph → attention masks split it into C and S → two readout layers predict Y → enhanced GIB loss + contrastive intervention loss.
- No complex equations on the slide — just the pipeline diagram.

**Presenter notes:**
- **Visual:** Simplified version of Figure 2 from the paper: Input → Encoder → Split → Causal/Confounding → Predict + Contrast.
- **Transition:** "Does it actually work? Let's look at the numbers."

---

## Section 3: Results (~1.5-2 min) — Slide 7

### Speaker cues — GOOD-ZINC (main benchmark, MAE metric)

| Setting | GSAT (prev. best) OOD MAE | Ours OOD MAE | Improvement |
|---|---|---|---|
| Scaffold-Covariate | 0.1419 | **0.1046** | 26.3% lower |
| Scaffold-Concept | 0.0999 | **0.0518** | 48.1% lower |
| Size-Covariate | 0.2112 | **0.1484** | 29.7% lower |
| Size-Concept | 0.1043 | **0.0580** | 44.4% lower |

- Metric: **Mean Absolute Error (MAE)** — lower is better.
- Dataset: **GOOD-ZINC** — predicting molecular solubility under distribution shifts.
- Consistent SOTA across all four OOD settings; also lower variance (more stable).
- On **ReactionOOD** benchmarks (RMSE metric): best OOD in 6/10 cases, runner-up in 2 more.

### Presenter notes
- **Visual:** Simplified bar chart: 4 grouped bars (Scaffold-Cov, Scaffold-Con, Size-Cov, Size-Con), each comparing GSAT vs Ours. Ours clearly shorter (lower error).
- **Delivery:** "In every OOD condition, our method cuts the error by 26 to 48 percent compared to the best prior method." Point at bars.
- **Transition:** "So what does this mean for the bigger picture, and for my own work?"

---

## Section 4: Takeaway + Impact on My Research (~0.5-1 min) — Slides 8-9

### Slide 8 — Significance & Broader Impact

**Speaker cues:**
- First paper to explicitly model confounders' predictive power in graph regression.
- Shows that classification-specific causal methods don't transfer to regression — a different recipe is needed.
- Practical impact: drug discovery, materials science, climate modeling — all need regression on graphs, all face OOD shifts.
- General principle: **don't discard confounders; understand them to separate them.**

**Presenter notes:**
- **Visual:** Three icons (molecule, material, climate) + bold text: "Regression ≠ Classification in causal learning."
- **Delivery:** Brief, confident. 20-30 seconds max.

### Slide 9 — What I Learned + Closing

**Speaker cues (impact on my research design):**
- Model confounders explicitly, don't assume they're noise.
- Use contrastive learning when class labels aren't available.
- Always test on OOD data with distribution shifts.

**Speaker cues (writing technique — 20 sec max):**
- The paper opens with a sharp tension: "prior methods fail on regression" and explains exactly why.
- Every claim is backed by results across multiple datasets and shift types.

**Closing:**
- "To sum up: this paper shows that solving regression in causal graph learning requires rethinking confounders — understanding them rather than ignoring them. Thank you. I'd be happy to take questions."

**Presenter notes:**
- **Visual:** Two-column layout: "Research Lessons" (left) + "Key Takeaway" (right, bold).
- **Delivery:** Slow down for closing. Eye contact. Confident posture. End with a smile.