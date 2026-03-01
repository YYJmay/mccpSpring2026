# Slide Plan — Causal Graph Regression (9 Slides, 8 min)

| # | Title | Time | Bullets (≤3, ≤7 words each) | Visual Element | Rubric Tag |
|---|---|---|---|---|---|
| 1 | Title Slide | 10s | Paper title, authors, venue | Clean title layout | — |
| 2 | The Hook: Why This Matters | 50s | Predict exact molecular properties · AI learns shortcuts, not causes · Shortcuts fail on new data | Molecule icon (green causal / red confounding split) | CONTENT · NON-SPECIALIST |
| 3 | Why Regression Breaks Everything | 2 min | Classification: group by label · Regression: continuous → no groups · Prior causal methods need labels | Two-panel: YES/NO bins vs number line | CONTENT · KEY FINDINGS |
| 4 | Insight 1: Confounders Are Predictive | 1 min | Standard GIB ignores confounder signal · Confounders predict, just not causally · Enhanced GIB: separate, don't discard | Boxed diagram: G → C (green) + S (red) → Y | KEY FINDINGS · EVIDENCE |
| 5 | Insight 2: Contrastive Causal Intervention | 1.5 min | Mix causal + random confounder · Positive pair: same cause, different confounder · No labels needed → works for regression | Three-node diagram: real ✓, counterfactual ✓, other ✗ | KEY FINDINGS · EVIDENCE |
| 6 | Full Pipeline | 30s | Encode → split → predict · GIB loss + contrastive loss | Simplified pipeline: Input → Encoder → Split → Predict/Contrast | CONTENT |
| 7 | Results: Ours vs GSAT | 1.5 min | GOOD-ZINC MAE: 26–48% lower · Best OOD in 6/10 ReactionOOD cases · Consistent gains, lower variance | Bar chart: 4 GOOD-ZINC settings, GSAT vs Ours | EVIDENCE · KEY FINDINGS |
| 8 | Significance & Broader Impact | 30s | First to model confounder predictive power · Regression ≠ classification in causal learning · Drug discovery, materials, climate | Three domain icons + bold statement | SIGNIFICANCE |
| 9 | What I Learned + Thank You | 30s | Model confounders explicitly · Test on OOD distribution shifts · Paper teaches claim-backed-by-evidence writing | Two-column: Research Lessons / Key Takeaway | WRITING SKILLS · DELIVERY |

---

## Color Coding
- **Green** (#2ecc71) = causal subgraph / positive
- **Red** (#e74c3c) = confounding subgraph / negative
- **Teal** (#1B4942) = headings, accents

## Key Terms (define once on Slide 2)
1. **Graph** — network of connected nodes (atoms + bonds)
2. **Causal subgraph** — part that truly decides the outcome
3. **Confounding subgraph** — part that only looks related
4. **OOD** — data the model never saw during training

## Speaker Note Style
- Bullet cues only (no scripts)
- 1-line transition cue at bottom of each content slide
