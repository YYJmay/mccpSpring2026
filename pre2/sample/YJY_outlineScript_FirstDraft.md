# YJY Poster Presentation Outline & Script (First Draft)

## 1) 2–3 minute outline

1. Opening and hook (15–20s)
2. Problem and research gap (25–30s)
3. Method (50–60s)
4. Results and significance (30–40s)
5. Closing and Q&A transition (10–15s)

---

## 2) Script (about 2 min 30 s)

### Opening
Hello everyone, I’m Yujia Yin. My poster is titled **“A Recipe for Causal Graph Regression: Confounding Effects Revisited.”**
The key message is: we improve out-of-distribution generalization for graph regression by redesigning how confounding effects are handled.

### Problem and gap
Most causal graph learning methods are designed for **classification**, not **regression**.
But many real tasks—such as molecular property prediction—are regression tasks and more challenging under distribution shifts.
Another issue is that many methods assume confounders are pure noise with no predictive power. In practice, this is often too strong.

### Method
Our framework first separates each graph into a **causal subgraph C** and a **confounding subgraph S** with learnable masks.
Then we optimize an enhanced graph information bottleneck objective:

**L_GIB = -I(C;Y) + αI(C;G) - βI(S;Y)**

This keeps causal information while explicitly modeling the predictive role of confounders.
Next, for causal intervention in regression, we use a **contrastive learning** strategy instead of label-dependent intervention.
The final loss is:

**L = L_GIB + λL_CI**

### Results
On GOOD-ZINC, our method achieves state-of-the-art MAE across scaffold/size and covariate/concept settings.
On ReactionOOD datasets, it gets the best OOD performance in most settings and remains very competitive in the rest.
So the method is not only accurate but also more stable under distribution shifts.

### Closing
In short, we provide a practical recipe for causal graph regression:
model confounders realistically and combine enhanced GIB with contrastive intervention.
Thank you for listening, and I welcome your questions.

---

## 3) Likely Q&A quick responses

- **Q: Why is regression harder than classification here?**  
  Because labels are continuous, so many class-based intervention strategies are not directly applicable.

- **Q: Why keep the confounder term instead of removing confounders completely?**  
  Some confounders are still predictive in real data. Ignoring this can hurt disentanglement and OOD generalization.

- **Q: What is the biggest practical takeaway?**  
  Enhanced GIB plus contrastive intervention offers a robust, transferable strategy for graph regression under shifts.

- **Q: How should non-specialists understand this work?**  
  We teach the model to focus on stable cause-like patterns, so it makes fewer mistakes when data conditions change.
