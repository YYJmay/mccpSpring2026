# Further Revision Guide (Detailed)

## Purpose
This guide is for revising your **revised draft** into a version that is not only better aligned with the MCCP6020 rubric and the original feedback, but also **factually safer at the literature level**. The main goal is no longer broad restructuring. Instead, it is to fix places where the argument is still too strong, too vague, or not fully supported by the cited papers.

The central revision principle for this round is:

> **Do not merely make the prose sound more critical; make every evaluative sentence match what the cited paper actually claims.**

That means each paragraph now needs three layers of control:
1. rhetorical fit with the move structure;
2. synthesis across papers rather than paper-by-paper summary;
3. factual restraint, so that each comparative claim is genuinely supported.

---

## 1. What has improved, and what still needs work

Your revised draft has already fixed several major structural problems from the first draft:
- Move 2 is much sharper and now states a real gap;
- the literature review is shorter and more synthesis-driven;
- the method families are now grouped in a cleaner way;
- the conclusion is more focused.

However, a second-level problem remains:

> **Some of the new synthesis sentences are rhetorically strong, but the underlying citations do not always fully support them.**

This is very common in revision. When writers move from summary to synthesis, they sometimes overcompress the literature and accidentally make claims that are broader than the papers themselves.

That is exactly what should be fixed now.

---

## 2. The most important factual-citation corrections

This section is the highest-priority part of the guide. These are the places where your current version is either too strong, too loose, or partially inaccurate.

### 2.1 Introduction paragraph on missingness and assay properties

### What is currently risky
In the current revised draft, you write that the published HI table is sparse and that the missingness is "not random," because laboratories perform more measurements for viruses of public health concern. That intuition is reasonable, but the exact wording is currently **stronger than the evidence you explicitly cite**.

### Why this is risky
To say that missingness is "not random" is effectively making a sampling-process claim. That is stronger than simply saying surveillance is uneven or priority-driven. Unless a cited paper explicitly frames the observation process as selective or biased with respect to surveillance priorities, the safest academic move is to soften the wording.

### Better claim
Use one of the following instead:
- "observation is uneven and influenced by surveillance priorities"
- "the measured table reflects targeted surveillance rather than exhaustive testing"
- "coverage is shaped by practical and public-health priorities, so observed data are not a neutral sample of all possible virus-serum pairs"

These versions preserve your argument without overclaiming a formally established MNAR mechanism.

### Better citation logic
For this paragraph, the safest support pattern is:
- **Smith 2004** for HI titers and assay interpretation;
- **Einav & Cleary 2022** for the infeasibility of measuring all antibody-virus interactions and the need to infer missing entries;
- **Adabor et al. 2018** for non-antigenic variability and assay-related confounding;
- **Shah et al. 2024** for practical metadata and assay heterogeneity such as passage, avidity, potency.

### Recommended paragraph-level correction
Instead of saying:
> "Critically, this missingness is not random..."

write something like:

> Because surveillance programs cannot assay all virus-serum pairs, the observed HI table is highly incomplete. Moreover, measurement coverage is shaped by practical and public-health priorities rather than uniform sampling, while dilution limits, passage effects, and laboratory-specific conditions introduce additional heterogeneity into the recorded titers.

This is safer and still strong.

---

### 2.2 Geometry paragraph: claim about inability to position new strains

### What is currently risky
You currently write that a newly emerged virus cannot be positioned in the antigenic map without measured titers or reliable phylogenetic placement, and that geometry-based methods are less suitable than sequence-driven methods for prospective prediction.

### What is true and what needs adjustment
This is **partly true**, but the phrasing should be more careful.

- **Smith et al. 2004** is indeed fundamentally serology-driven: the map is built from observed HI data.
- **Neher et al. 2016** explicitly extends this by using phylogenetic structure to predict antigenic properties for viruses not yet characterized antigenically.

So if you say geometry-based methods "cannot" handle unmeasured viruses, that is too strong once Neher is included in the same paragraph.

### Better interpretive position
What you really want to say is:
- classical cartography is strongly tied to observed serology;
- phylogeny-informed extensions partially relax this limitation;
- but even these models remain less directly inductive than sequence-to-titer models designed for prediction from sequence features alone.

### Better paragraph logic
Use this structure:
1. Smith establishes interpretable geometric representation from HI titers.
2. Neher extends geometry by linking antigenic change to tree structure and thereby enables limited out-of-sample prediction.
3. Therefore, geometry is not purely transductive anymore, but its predictive reach still depends on accurate phylogenetic anchoring and continued serological calibration.
4. This makes it more interpretable, but generally less flexible for fully prospective prediction than dedicated sequence-based models.

### Suggested sentence replacement
Replace this sentence:
> "A newly emerged virus cannot be positioned in the antigenic map without either measured titers or reliable phylogenetic placement."

with:

> In classical antigenic cartography, new viruses require serological data to be located reliably, whereas phylogeny-informed extensions permit limited interpolation for uncharacterized strains by borrowing structure from the evolutionary tree.

Then follow it with:

> Even so, these approaches remain partly anchored to measured serology and are therefore less directly inductive than models trained to predict antigenic outcomes from sequence-derived features alone.

This is more accurate.

---

### 2.3 Matrix paragraph: strongest factual problem in the current draft

This is the paragraph that most needs correction.

### What is currently good
You correctly identify that matrix-based work is useful for reconstruction, denoising, and calibration.

### What is currently too strong or unsupported
Two claims are currently unsafe in their present form:

1. **"they typically assume that missingness is independent of antigenicity"**
2. **"and treat censored values as exact"**

These statements may be defensible as broad methodological concerns in the field, but they are **not clearly established by the specific papers you cite in that paragraph**.

### Why this matters
If you attribute those limitations directly to **Adabor 2018** and **Einav 2022**, a careful reader could object that:
- Adabor is focused on Bayesian decomposition of antigenic and non-antigenic effects, not on formal modeling of surveillance selection;
- Einav & Cleary focuses on low-rank completion and cross-study extrapolation, not on an explicit assumption test about surveillance-driven missingness or censoring-aware likelihoods.

So the problem is not that your concern is intellectually wrong. The problem is that it is **citation-misaligned**.

### Better way to critique matrix methods
Instead of attributing a specific MNAR assumption to these papers, say something like:

> These methods improve reconstruction under sparsity, but they generally operate on the observed table as given rather than explicitly modeling why particular measurements were collected or how censoring enters the likelihood.

This formulation is much safer. It criticizes what the papers do **not** model, without falsely claiming that they formally assume something stronger.

### Better description of Adabor et al. 2018
Also tighten the biological wording. In your current version, you say:
> "serum amplitude, virus-specific avidity, and a latent antigenic compatibility term"

That is directionally fine, but if you keep it, make it clear that the paper is about **decoupling antigenic and non-antigenic contributions** to HI titers, not necessarily reconstructing a generic latent surface in the same way as matrix completion.

Safer version:

> Adabor et al. propose a Bayesian decomposition of HI titers into antigenic and non-antigenic components, allowing assay-related effects such as virus avidity and antibody concentration to be separated from the signal used for antigenic interpretation.

### Better description of Einav & Cleary 2022
Your current summary is mostly sound, but keep the core contribution specific:
- low-rank structure;
- cross-study extrapolation when panels overlap;
- sample-error curves for experimental design.

Avoid overclaiming that the paper specifically solves influenza-surveillance bias.

### Suggested replacement for the critique sentence
Replace:
> "However, they typically assume that missingness is independent of antigenicity and treat censored values as exact..."

with:

> However, these approaches generally reconstruct the observed table rather than explicitly modeling the surveillance process that produced it. As a result, they improve calibration and completion under sparsity, but they do not by themselves resolve selection bias or censoring at the level of data acquisition.

That is much more defensible.

---

### 2.4 Sequence paragraph: mostly good, but two places need tightening

Your sequence-based paragraph is the strongest of the three, but it still has two places where a careful examiner could push back.

#### (a) IAV-CNN
Your current wording is acceptable because you correctly say it is an early, coarse classification model. Keep that. But be explicit that it predicts **antigenic variants / thresholds**, not direct quantitative HI titers.

Safer wording:

> Early sequence-based work established feasibility through classification rather than direct titer regression. IAV-CNN, for example, used embedded HA sequence fragments and a convolutional architecture to predict whether strain pairs crossed an antigenic threshold.

This is more precise than saying it "describes inhibition activity" in the same way later models do.

#### (b) Shah et al. 2024
Your summary is broadly right and, importantly, supported by the paper:
- season-aware evaluation;
- past seasons only;
- metadata including virus avidity, antiserum potency, passage history.

That part can stay.

What should be adjusted is the phrase:
> "producing stable predictions"

That wording is a bit vague and reads like a performance claim without a metric. Better to say:

> "achieving accurate season-by-season prediction under a deployment-like protocol"

This maps more directly onto what the paper actually emphasizes.

#### (c) VaxSeer 2025
This paragraph is strong, but add one note of restraint.

VaxSeer is indeed a major shift from titer prediction to vaccine-ranking support. However, the paper validates the method retrospectively using surrogate coverage/effectiveness relationships. So avoid language that sounds like direct prospective clinical validation.

Safer wording:

> VaxSeer extends this line of work from antigenicity prediction to decision-oriented vaccine ranking by combining an antigenicity predictor with a future-dominance model. In retrospective analyses, its coverage score correlates strongly with vaccine effectiveness and often ranks candidate strains more favorably than historical WHO choices.

The key phrase is **"in retrospective analyses"**.

That protects you from overstating the evidence.

---

### 2.5 Research gap paragraph: conceptually strong, but one line should be softened

### What is currently strong
Your new Move 3 is much better than the first-draft version because it prioritizes one central gap and two supporting gaps.

### What still needs softening
The phrase:
> "geometry-based methods explain antigenic movement clearly but cannot extrapolate beyond observed serology"

is again too strong because of Neher.

### Better version
Use:

> geometry-based methods provide a transparent account of antigenic structure but only limited extrapolation beyond directly measured serology.

That single word change — **limited** instead of **cannot** — makes the whole paragraph more accurate.

---

## 3. Paragraph-by-paragraph revision plan for the current draft

Below, I refer to the paragraphs in your **current revised draft**, not the original first draft.

---

## Introduction

### Paragraph 1: HI importance and public-health motivation

### Keep
- The basic opening works.
- The public-health motivation is clear.
- The added sentence about reducing laboratory burden is good.

### Revise
The opening is slightly citation-heavy. Keep the content, but tighten the progression so it reads less like a chain of references and more like a research problem.

### Recommended internal logic
1. HI assays matter because they operationalize antigenic comparison.
2. These comparisons inform vaccine strain updates.
3. Influenza diversity and speed of evolution make complete laboratory characterization unrealistic.
4. Therefore computational prediction is practically useful.

### Suggested final shape
You do not need to rewrite the whole paragraph, but make sure the last sentence feels like a consequence of the previous three, not just an added policy line.

---

### Paragraph 2: sparse, selective, censored, heterogeneous observations

### Keep
This remains one of the strongest paragraphs in the paper.

### Revise
Replace the strongest sentence on missingness with softer, evidence-aligned wording.

### Replace this part
> "Critically, this missingness is not random..."

with something like:

> Importantly, the observed table reflects targeted surveillance rather than exhaustive measurement, so assay coverage is uneven across viruses and antisera.

### Citation recommendation
In this paragraph, your best support should come mainly from:
- Smith 2004;
- Adabor 2018;
- Einav & Cleary 2022;
- Shah 2024.

I would **reduce dependence on Tricco 2013 / Houser 2015 / Jalan 2025** here unless those are genuinely the sources you want to defend in discussion.

---

### Paragraph 3: Move 2 niche statement

### Keep
This paragraph is much improved relative to the first draft and is already aligned with the original feedback.

### Revise
Very lightly. Its logic is now correct.

### One optional improvement
The final clause
> "yet no existing study systematically compares these trade-offs"

is rhetorically effective, but because this is a course assignment rather than a published review, you can make it slightly less absolute:

> "yet these trade-offs are rarely compared in a structured way across method families."

This avoids the examiner mentally asking whether *literally no* such comparison exists.

---

### Paragraph 4: Move 3 occupying the niche

### Keep
This paragraph is now much better than the first-draft contribution-list version.

### Revise
One small improvement: make the final clause more explicit about **why** this matters for the review.

### Better ending
Instead of
> "identifies the gaps that future work must address"

prefer

> "clarifies which capabilities are already mature and which methodological gaps still limit deployment in surveillance practice."

That sounds a little more analytical and less generic.

---

## Literature Review

### Paragraph 5: thematic overview

### Current issue
The sentence
> "sequence-based methods learn a direct mapping from viral and serum sequences to inhibition activity"

is too broad for the set of papers you actually discuss. Some sequence papers predict thresholded antigenic variation, some predict normalized HI-related outputs, some predict antigenic distance, and VaxSeer predicts a downstream score built from antigenicity plus dominance.

### Better wording
Use:

> sequence-based methods infer antigenic similarity or HI-related outcomes from sequence-derived features.

This is much safer and still captures the category.

### Suggested revised paragraph
A strong version would be:

> Machine learning approaches to HI prediction differ primarily in how they represent virus-serum relationships. Geometry-based methods infer antigenic structure directly from measured serology. Matrix-based methods reconstruct incomplete interaction tables while accounting, to varying degrees, for assay-related distortion. Sequence-based methods infer antigenic similarity or HI-related outcomes from sequence-derived features. In this review, these families are compared in terms of interpretability, robustness to sparse and heterogeneous observations, and generalization to newly emerging strains.

That version is tighter and more faithful.

---

### Paragraph 6: geometry-based methods

### What works
- The Smith → Neher progression is good.
- The paragraph already synthesizes rather than listing.

### What must be corrected
There are three places to adjust.

#### Correction 1: Do not make Smith carry the whole interpretability argument alone
Smith shows punctuated antigenic evolution and monitoring of vaccine/circulating strain differences. That supports interpretability and surveillance use.

#### Correction 2: Soften the "cannot position new virus" claim
As discussed above, Neher partly relaxes this.

#### Correction 3: Do not overstate observation-process critique
"Neither approach explicitly models the selective observation process" is acceptable if you present it as a limitation of scope, not as a demonstrated failure.

### Best paragraph shape
Use this internal sequence:
1. geometry gives a directly interpretable antigenic representation;
2. Smith is the foundational map-based form;
3. Neher adds phylogenetic additivity and limited prediction for unmeasured strains;
4. nevertheless, the family remains dependent on serological structure and does not explicitly model how observations were acquired;
5. therefore its main strength is interpretation, not fully prospective induction.

### Suggested improved paragraph core
> Geometry-based approaches model antigenic relatedness as distance in a latent space inferred from HI measurements. Smith et al. introduced antigenic cartography, showing that HI data could be visualized as an interpretable antigenic map in which major transitions appear as punctuated movements over time. Neher et al. extended this framework by imposing additive antigenic changes along the phylogeny, which enabled limited prediction for strains lacking direct serological characterization. Together, these studies show that geometry offers strong interpretability and remains highly valuable for surveillance communication. At the same time, the family remains closely tied to measured serology and evolutionary anchoring, and it does not explicitly model why particular HI observations are available. Its predictive reach is therefore more constrained than that of sequence-based approaches designed for forward generalization.

This is the version I recommend aiming for.

---

### Paragraph 7: matrix-based methods

### What works
- You correctly frame the family as reconstructive.
- The Adabor + Einav pairing is sensible.

### What must be corrected
This paragraph currently contains the greatest citation-to-claim mismatch.

#### Correction 1: tighten Adabor
Do not imply that Adabor is a generic matrix completion paper. It is better framed as **assay-aware decomposition** of HI into antigenic and non-antigenic components.

#### Correction 2: tighten Einav
Do not imply that the paper is specifically about HI surveillance bias. Its strength is low-rank completion and cross-study extrapolation in antibody-virus datasets.

#### Correction 3: replace the current limitation sentence
Do **not** say these papers assume missingness independent of antigenicity or treat censored values as exact unless you are ready to defend those claims textually from the papers themselves.

### Recommended paragraph core
> Matrix-based approaches shift attention from geometric distance to recovery of an incomplete interaction table. Adabor et al. address this problem through Bayesian decomposition, separating antigenic signal from non-antigenic assay effects such as virus avidity and antibody-related variation. This makes the resulting antigenic estimates better suited for interpretation across heterogeneous experimental settings. Einav and Cleary pursue a different strategy, showing that antibody-virus measurement matrices often have sufficiently low effective rank to support accurate completion of large numbers of unmeasured entries, even across partially overlapping studies. In this family, the main advantage is not prospective extrapolation to wholly novel strains, but improved calibration, denoising, and experimental efficiency within sparse datasets. Its main limitation is that reconstruction usually operates on the observed table as given, rather than explicitly modeling surveillance selection or censoring mechanisms.

This preserves your critique while keeping it honest.

---

### Paragraph 8: sequence-based methods

### What works
This paragraph is already the closest to publication quality.

### What should be revised
#### Correction 1: be precise about the target of IAV-CNN
Say thresholded antigenic variants or antigenic classification, not broad HI prediction.

#### Correction 2: make Shah more explicit and more metric-linked
Your current summary is mostly accurate. Just replace "stable predictions" with something more concrete.

#### Correction 3: insert one restraint phrase for VaxSeer
Add "in retrospective evaluation".

### Recommended paragraph core
> Sequence-based approaches reduce dependence on contemporaneous serology by learning antigenic relationships from sequence-derived features. Early work such as IAV-CNN demonstrated feasibility through classification, predicting whether strain pairs crossed an antigenic threshold rather than directly regressing quantitative titers. Later studies moved toward richer supervision and more realistic deployment settings. Shah et al., for example, trained season by season using only information available from previous seasons and combined HA1 sequence differences with metadata such as avidity, antiserum potency and passage history, thereby aligning evaluation with WHO-style surveillance timelines. VaxSeer pushes this family further toward decision support by combining an antigenicity predictor with a future-dominance model to rank vaccine candidates by coverage score. In retrospective analyses, this score correlates strongly with vaccine effectiveness and often yields stronger candidate rankings than historical selections. The main strength of the family is prospective reach; its main weaknesses are dependence on biased historical training data and weaker interpretability than map-based approaches.

That version is safer and sharper.

---

### Paragraph 9: research gaps

### What works
This paragraph is already much better than the first draft.

### Revise
Only one essential correction: change absolute language about geometry.

### Suggested version
> The comparison across method families shows that no single approach yet satisfies the combined demands of influenza surveillance. The central gap is the absence of methods that can handle sparse and heterogeneous HI data while remaining reliable for prospective prediction of emerging strains. Two supporting tensions sharpen this point. First, geometry-based methods provide transparent antigenic structure but only limited extrapolation beyond directly measured serology, whereas sequence-based methods generalize more naturally to unseen variants but offer weaker geometric interpretability. Second, evaluation protocols remain inconsistent: many studies report predictive accuracy under random or partially retrospective splits, but fewer test robustness under temporal shift and cross-laboratory heterogeneity, which are central to deployment.

This is probably the strongest version for the assignment.

---

### Paragraph 10: literature review conclusion

### What works
The logic is clear and the ending is much improved relative to the first draft.

### Revise
Make the hybrid claim slightly more grounded and slightly less universal.

### Better ending
Instead of
> "Future work should therefore pursue hybrid approaches..."

consider:

> A plausible next step is to combine these strengths more explicitly: sequence models for forward generalization, geometry for communication and interpretation, and assay-aware reconstruction for calibration under sparse heterogeneous measurement.

This sounds less like a generic future-work line and more like a direct implication of your comparison.

---

## 4. What to cut, even now

Even after your successful compression, there are still a few phrases that carry unnecessary risk or weight.

### Cut or replace these kinds of expressions
- "no existing study" → use "rarely compared in a structured way"
- "cannot extrapolate" → use "has limited extrapolative capacity"
- "not random" → use "priority-shaped" / "targeted" / "uneven"
- "treat censored values as exact" → avoid unless directly sourced
- "systematically compares" can stay, but softer wording is safer in coursework

These are small changes, but they sharply improve defensibility.

---

## 5. Best citation strategy for the final version

Do not try to maximize citation count. Instead, make each paragraph rest on **2 to 4 anchor citations** that actually support the claims in that paragraph.

### Recommended anchors by paragraph

#### Introduction paragraph 1
- Smith et al. 2004
- Fonville et al. 2014
- Neher et al. 2016

#### Introduction paragraph 2
- Smith et al. 2004
- Adabor et al. 2018
- Einav & Cleary 2022
- Shah et al. 2024

#### Geometry paragraph
- Smith et al. 2004
- Neher et al. 2016
- optionally Fonville et al. 2014 if you mention downstream interpretive use

#### Matrix paragraph
- Adabor et al. 2018
- Einav & Cleary 2022

#### Sequence paragraph
- Yin et al. / IAV-CNN
- Shah et al. 2024
- Shi et al. 2025
- optionally Li et al. 2024 if you want one intermediate sequence-distance example

This will look cleaner and more deliberate than scattering too many references into single sentences.

---

## 6. The most important viewpoint corrections in one place

If you remember only five corrections from this guide, remember these:

1. **Do not overstate selective missingness as formally established MNAR unless the source clearly says so.**
2. **Do not say geometry-based methods cannot extrapolate; say they extrapolate only in limited, phylogeny-supported ways.**
3. **Do not attribute explicit missingness-independence or censoring-as-exact assumptions to Adabor 2018 / Einav 2022 unless you can quote them.**
4. **Do not describe IAV-CNN as a direct HI-titer regressor; it is better introduced as threshold-based antigenic classification.**
5. **Do not present VaxSeer as direct real-world prospective proof; keep the phrase "retrospective evaluation" or "retrospective analyses."**

---

## 7. Final recommendation on writing style

At this stage, your biggest gain will not come from making the writing more sophisticated. It will come from making it more **disciplined**.

The target style is:
- restrained but confident;
- comparative rather than encyclopedic;
- critical but citation-faithful;
- concise enough for the word limit, but specific enough that each evaluative sentence can be defended.

A good self-check for every paragraph is:

> **If a reviewer asked me, "Which cited paper exactly justifies this sentence?", could I answer immediately?**

If the answer is no, the sentence is too broad and should be softened or split.

---

## 8. One possible near-final paragraph set to aim toward

Below is a compact target formulation for the three core literature-review paragraphs. Do not copy mechanically, but use the logic.

### Geometry
Geometry-based approaches represent antigenic relationships as distances inferred from HI measurements. Smith et al. showed that these data can be embedded into interpretable antigenic maps, revealing punctuated transitions in influenza evolution and providing a practical tool for surveillance. Neher et al. extended this logic by distributing antigenic change along the phylogeny, which enabled limited prediction for strains lacking direct antigenic characterization. The major strength of this family is interpretability: it translates serology into a representation that is useful for communication and evolutionary reasoning. Its limitation is that prediction remains closely tied to measured serology and phylogenetic anchoring, rather than fully learned from sequence-derived predictors.

### Matrix
Matrix-based methods treat the observed HI table as an incomplete measurement of a larger interaction landscape. Adabor et al. improved antigenic interpretation by separating antigenic signal from non-antigenic assay effects, including variation linked to virus avidity and antibody-related factors. Einav and Cleary addressed sparsity from a low-rank perspective, showing that many unmeasured antibody-virus interactions can be recovered accurately and that experimental effort can be guided through sample-error curves. These approaches are especially valuable for denoising, calibration and efficient reconstruction within sparse datasets. Their limitation is that they usually reconstruct the observed table as given, rather than explicitly modeling the surveillance process that determined which measurements were collected.

### Sequence
Sequence-based approaches aim to infer antigenic outcomes from sequence-derived features and therefore offer the clearest route to prospective prediction. Early work such as IAV-CNN demonstrated feasibility through threshold-based antigenic classification from HA sequence embeddings. More recent models moved closer to deployment settings. Shah et al. trained season by season using only information from prior seasons and incorporated metadata such as avidity, potency and passage history, showing that sequence-based prediction can be aligned with WHO-style surveillance workflows. VaxSeer extended the objective further by integrating antigenicity prediction with future dominance forecasting to rank vaccine candidates by predicted coverage. In retrospective evaluation, this ranking correlated strongly with vaccine effectiveness. The family’s main advantage is forward reach; its main weaknesses are dependence on biased historical training data and reduced interpretability relative to geometric mapping.

