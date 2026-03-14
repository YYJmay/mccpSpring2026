# Revision Guide for the HI-Titer Review Draft

## Purpose of this guide
This guide is designed to help revise the current draft of **"Machine Learning Methods for Hemagglutination Inhibition Titer Prediction in Influenza Surveillance"** into a version that better matches the assignment rubric, the teacher's feedback, and the rhetorical move structure required in MCCP6020. It is written as a **paragraph-by-paragraph revision plan**, not as a replacement draft.

The main revision principle is simple:

> **Shift the paper from broad catalog-style coverage to a shorter, more decisive, synthesis-driven research story.**

At present, the draft already shows strong domain knowledge, dense citation support, and a coherent taxonomy. The main issue is that the literature review often reads like a mini survey paper rather than a tightly controlled course assignment. The next version should therefore do less coverage and more argument.

---

## 1. What the rubric is really asking for

Before revising sentences, align the draft with the grading logic.

### 1.1 Task Achievement
To reach the highest band, the paper must do four things clearly and efficiently:
1. explain the background and importance of the problem;
2. define the research focus and objective;
3. **synthesise and critically evaluate** the literature, rather than listing papers one by one;
4. state the research gap and significance sharply.

This means the key risk in the current draft is **not lack of knowledge**, but **insufficient compression and insufficient synthesis**.

### 1.2 Organisation
The marker wants a **coherent research story**. Every paragraph should push the same argument forward:

- HI prediction matters because surveillance data are sparse, biased, and noisy.
- Existing methods differ because they assume different representations of virus-serum interaction.
- Those representational choices create different strengths and weaknesses.
- No single family yet solves interpretability, calibration, and prospective prediction simultaneously.

If a paragraph does not directly advance this logic, cut it or compress it.

### 1.3 Practical consequence for revision
When revising, do **not** ask:
- "Can I add another reference?"

Instead ask:
- "Does this paragraph strengthen the central comparison?"
- "Am I comparing approaches, or just describing them?"
- "Does the reader understand why this method matters for surveillance?"

---

## 2. Your current draft: strengths and real problems

## 2.1 What is already strong
You should preserve these strengths:

- The Introduction already follows Move 1 / Move 2 / Move 3 clearly.
- The practical motivation is strong: selective measurement, finite dilution range, inter-laboratory variation, temporal variation.
- The representational taxonomy is intelligent and defensible.
- The review shows real technical understanding.

These are not small strengths. The next revision should **protect** them while reducing overload.

## 2.2 The real problems
The draft currently has five structural problems.

### Problem A. Move 2 is correct but not sharp enough
The draft says the field has diverse approaches. That is true, but still too descriptive. A stronger niche statement should say that the field lacks a **systematic comparison of assumptions, data requirements, and reliability under surveillance conditions**.

### Problem B. The literature review is too long for the assignment
The assignment asks for **1000-1500 words total**, excluding citations and annotations. The current version behaves like a genuine review article. That gives intellectual depth, but it also makes the paper harder to score well on task fit.

### Problem C. Some sections are still method-by-method summaries
This is the central criticism from the feedback. A literature review should not read like:

- Paper A did X.
- Paper B did Y.
- Paper C did Z.

It should read like:

- Early work assumed X.
- Later work relaxed or challenged X.
- This improved one property but worsened another.
- This matters because surveillance data have property Q.

### Problem D. There are too many research gaps
The draft identifies many good gaps, but in a short assignment, too many gaps weaken focus. You should select **one main gap** and at most **two supporting gaps**.

### Problem E. The paper sometimes sounds like a submission-ready survey article
Phrases such as "To the best of our knowledge" and the formal contribution bullets make sense in a journal paper. In this assignment, they can sound slightly overbuilt. A course paper can be authoritative without sounding like a published review.

---

## 3. Global strategy for the second version

## 3.1 The new controlling question
Reorganize the paper around one controlling question:

> **How should existing HI-titer prediction methods be compared when surveillance data are sparse, selectively measured, and temporally shifting?**

This is stronger than simply saying "there are three categories of methods." The taxonomy should become a tool for answering this question, not the paper's main point.

## 3.2 Recommended scope reduction
Keep only **three core method families**:
- geometry-based methods,
- matrix-based methods,
- sequence-based methods.

Mention other subfamilies only if they directly strengthen a comparison.

## 3.3 New word budget
Use a hard budget so the paper cannot expand again.

- Introduction: **300-350 words**
- Literature Review Move 1: **80-120 words**
- Literature Review Move 2 (three core paragraphs): **550-750 words**
- Literature Review Move 3: **120-160 words**
- Literature Review Move 4: **80-120 words**

Target total: **1150-1400 words**.

---

## 4. Paragraph-by-paragraph revision guide

# INTRODUCTION

## Paragraph 1: HI assay importance and public health context
### Current function
This paragraph establishes territory well.

### Keep
Keep the basic logic:
- HI assays measure antigen recognition,
- HI informs vaccine strain selection,
- influenza diversity makes interpretation more urgent.

### Revise
Compress it slightly. At the moment, it is informative but could arrive at the practical problem faster.

### What to add
Add **one short sentence** linking better prediction to practical surveillance efficiency. For example:

> More reliable computational prediction could reduce the number of laboratory measurements required to characterize emerging strains and support faster vaccine strain recommendation.

### Why
This strengthens significance and makes Move 1 more policy-relevant.

---

## Paragraph 2: sparse, selective, censored, heterogeneous data
### Current function
This is one of the best parts of the draft.

### Keep
Keep all four data problems, because they are the intellectual foundation of the whole review:
- incomplete measurement,
- surveillance-driven selective measurement,
- interval censoring from dilution limits,
- cross-laboratory / temporal variation.

### Revise
Do **not** expand this paragraph further. Instead, tighten it into a more compact "data challenge" paragraph.

### Recommended structure
Use a sequence like this:
1. surveillance cannot test all virus-serum pairs;
2. missingness is selective rather than random;
3. titers are censored by assay range;
4. values vary across laboratories and time;
5. therefore raw titers are an imperfect target and computational modeling is needed.

### Why
This paragraph should become the bridge from public health importance to the need for ML.

---

## Paragraph 3: Move 2 niche statement
### Current problem
This paragraph currently says there are many approaches and they differ in representation. That is true, but still passive.

### What to change
Rewrite the paragraph so the first sentence is a **gap claim**, not a field description.

### Current logic
- Recent advances produced many approaches.
- These methods represent interactions differently.
- They differ in interpretation and extension.

### Better logic
- Despite a growing body of work, the field lacks a systematic comparison of modeling assumptions.
- Existing methods differ not only in architecture but in what they assume antigenic interaction actually is.
- Those assumptions affect interpretability, data dependence, and reliability for future strains.
- Therefore comparison across method families is needed.

### Model sentence pattern
> Despite rapid progress in computational HI prediction, the literature still lacks a clear comparative account of how different modeling assumptions shape performance under realistic surveillance conditions. In particular, geometry-based, matrix-based, and sequence-based methods differ in their dependence on observed titers, their handling of sparsity and assay variation, and their ability to generalize to newly emerging strains.

### Why
This immediately gives Move 2 a stronger argumentative role.

---

## Paragraph 4: Move 3 purpose statement
### Current problem
Move 3 is clear, but too expansive and slightly too publication-like.

### What to delete or reduce
Cut or heavily reduce:
- "To the best of our knowledge..."
- formal contribution bullet list
- long description of unified formulation

### What to keep
Keep three things only:
1. what the review covers,
2. how it is organized,
3. what practical understanding it produces.

### Recommended rewrite focus
State that the review compares three method families by their representational assumptions and their implications for:
- interpretability,
- calibration / robustness to sparse data,
- generalization to future strains.

### Model direction
> This review compares three major families of computational HI prediction methods—geometry-based, matrix-based, and sequence-based approaches—through the assumptions they make about virus-serum interaction. It argues that these assumptions determine whether a method is more useful for antigenic interpretation, reconstruction of sparse data, or prospective prediction for newly emerging strains.

### Why
This is cleaner, more assignment-appropriate, and easier to connect to the literature review.

---

# LITERATURE REVIEW

## Paragraph 5: Move 1 thematic overview
### Current problem
Thematic overview currently repeats too much from the Introduction and repeats the contribution language.

### What to do
Shorten it aggressively.

### Keep
Keep only:
- one sentence defining the scope of the review,
- one sentence naming the three categories,
- one sentence stating the comparison dimensions.

### Recommended content
This paragraph should answer only two questions:
1. What literature is being reviewed?
2. On what basis will it be compared?

### Good comparison dimensions
Use the same three throughout the paper:
- interpretability,
- robustness / calibration under sparse heterogeneous data,
- inductive generalization to unseen strains.

### Why
Once these dimensions are fixed, the rest of the review becomes much easier to control.

---

## Paragraph 6: Geometry-based methods
### Current status
This section is well informed, but it is still a bit too detailed for the assignment. The equations and application discussion push it toward a mini survey.

### What the paragraph should do instead
This should become **one compact synthesis paragraph**, not a mini subsection.

### What to keep from the literature
Keep these core ideas:
- Smith et al. established antigenic cartography by mapping HI relationships into Euclidean antigenic space.
- These maps were useful because they made punctuated antigenic drift visible and interpretable.
- Neher et al. extended the idea by linking antigenic change to phylogenetic structure, allowing partial prediction for unmeasured strains.

### What to cut
Cut or shrink:
- full equations,
- long explanation of antibody landscapes,
- transition paragraph to next category,
- any sentence that only explains the math without serving the comparison.

### What to emphasize critically
This paragraph should explicitly state:
- **strength**: strong interpretability and strong communication value for surveillance;
- **assumption**: antigenic relations can be faithfully represented by distances derived from measured titers;
- **limitation**: dependence on observed serology makes the approach largely transductive;
- **comparison**: sequence methods are more predictive for new strains, but less geometrically interpretable.

### Best synthesis pattern
Try to write it like this:
1. early geometry-based work framed antigenic difference as spatial distance;
2. this was valuable because it made drift interpretable;
3. later phylogeny-informed work improved interpolation;
4. however, both approaches still rely heavily on measured titers and therefore struggle with genuinely unseen variants or biased observation processes.

### Why
This turns the paragraph from description into comparison-driven synthesis.

---

## Paragraph 7: Matrix-based methods
### Current status
This section has the right conceptual center: the matrix is sparse and distorted; methods try to reconstruct latent interaction structure.

### What to keep from the literature
Keep the contrast between two matrix-based lines:
- **Adabor et al.**: assay-aware decomposition that separates antigenic and non-antigenic components;
- **Einav et al.**: matrix completion that infers missing interactions and provides uncertainty / confidence information.

### What to emphasize
This paragraph should show a progression:
- some methods improve calibration by modeling assay effects;
- others improve coverage by exploiting low-rank or shared structure across studies;
- together, they treat HI prediction as a reconstruction problem rather than a mapping problem.

### Critical evaluation to include
Make sure this paragraph explicitly says:
- **strength**: matrix methods are strongest when the goal is denoising, imputing missing values, and harmonizing sparse panels;
- **assumption**: unmeasured values can be inferred from latent structure in the observed matrix;
- **limitation**: these methods usually still depend on overlap patterns and often do not fully model surveillance-driven missingness;
- **comparison**: they are better calibrated than pure sequence-only models for existing datasets, but less naturally prospective for entirely new variants.

### What to cut
Cut most formal optimization notation unless one very short notation line is essential.

### Best synthesis pattern
Write it as a tension:
- geometry methods prioritize interpretability,
- matrix methods prioritize reconstruction and calibration,
- but they still operate close to the observed assay table and therefore do not completely solve forward-looking prediction.

### Why
This paragraph is the bridge between serology-driven and sequence-driven thinking.

---

## Paragraph 8: Sequence-based methods
### Current status
This is conceptually rich, but too wide. It currently contains too many sub-axes and too many examples for the assignment length.

### Scope reduction
Reduce this section to **one dense but readable paragraph** organized around a simple progression:
1. early sequence models treated antigenicity prediction as classification,
2. later models moved toward continuous phenotypes and richer biological features,
3. more recent work evaluates methods in prospective or decision-oriented settings.

### Key literature to keep
You do **not** need all sequence papers. Keep only the most strategically useful ones:
- **IAV-CNN** for early sequence-based classification;
- **Shah et al. 2024** for season-aware prospective prediction from past data only;
- **VaxSeer 2025** for decision-oriented vaccine strain selection.

Optional fourth paper:
- **Li et al. 2024 / MFPAD** if you want one feature-engineered intermediate example between IAV-CNN and Shah.

### What to emphasize critically
This paragraph must make the strongest contrast in the paper:
- **strength**: sequence-based methods uniquely support prediction for newly emerged strains before serological characterization is complete;
- **assumption**: sequence variation contains enough information to infer antigenic behavior;
- **limitation**: these models inherit bias from the observed training assays, often reduce interpretability, and may become unreliable if evaluation ignores temporal leakage or laboratory heterogeneity;
- **comparison**: they are strongest for prospective use, but weaker than geometric approaches for communication and weaker than some matrix approaches for direct calibration of assay artifacts.

### What to cut
Cut the three-axis substructure if word count becomes a problem.

### Best synthesis pattern
A good paragraph structure is:
- early sequence models showed feasibility;
- later models added biologically informed features or richer targets;
- the strongest recent work shifted evaluation toward operational realism;
- however, prospective usefulness depends heavily on avoiding leakage and accounting for assay heterogeneity.

### Why
This is the most important paragraph for showing that you can compare modeling families in terms of research purpose, not just architecture.

---

## Paragraph 9: Move 3 research gaps
### Current problem
The draft currently lists too many gaps and the discussion becomes diffuse.

### What to do
Reduce the gap section to **one short paragraph with 2-3 ranked gaps**.

### Recommended gap set
Use this order:

#### Main gap
**The field still lacks methods that jointly handle sparse, selectively acquired, and heterogeneous HI measurements while remaining useful for prospective surveillance.**

#### Supporting gap 1
There is still a tension between **interpretability** and **inductive generalization**: geometry-based methods explain antigenic movement well, whereas sequence-based methods extrapolate better to new strains.

#### Supporting gap 2
Evaluation protocols are still inconsistent: many studies measure predictive accuracy, but fewer assess robustness under realistic temporal and laboratory shifts.

### Why this ranking works
These three gaps directly unify the entire paper and prepare the conclusion.

### What to avoid
Do not introduce totally new themes here. The gap paragraph should be a logical consequence of the previous comparison.

---

## Paragraph 10: Move 4 conclusion of literature review
### Current problem
The conclusion is strong, but can be shorter.

### What to keep
Keep the idea that the three families are complementary rather than simply competing.

### What to emphasize
The concluding paragraph should do three things only:
1. restate the comparative insight;
2. show why no single family is sufficient;
3. point to the kind of contribution your own research would make.

### Recommended final logic
- geometry gives interpretability,
- matrix methods improve reconstruction and calibration,
- sequence methods enable prospective prediction,
- future work should combine these strengths while accounting for selective measurement and deployment realism.

### Why
This creates a strong landing and directly satisfies Move 4 in the assignment template.

---

## 5. What to delete without regret
These cuts will improve the paper.

### Delete or heavily compress:
- the contribution bullet list in the Introduction;
- most equations in the literature review;
- long technical explanations that do not support comparison;
- the large comparison table, unless your lecturer explicitly values such tables;
- the standalone "Future Directions" section.

### Why these cuts help
They free word count for synthesis and keep the paper aligned with the assignment rather than a journal-style review.

---

## 6. Recommended literature backbone after detailed reading
Use the literature selectively. You do not need every cited paper to carry equal weight. Build the revised version around a small set of representative sources.

## 6.1 Geometry-based backbone
### Smith et al. (2004)
Use this paper for the foundational claim that antigenic evolution can be quantified and visualized from HI measurements, and that antigenic evolution is more punctuated than genetic evolution.

**How to use it in your review:**
- as the origin of antigenic cartography;
- as evidence for interpretability and surveillance usefulness;
- as the baseline for the "serology-first" view.

### Neher et al. (2016)
Use this paper to show that later work tied antigenic change to phylogeny and could predict properties of viruses not yet characterized antigenically.

**How to use it in your review:**
- as a refinement of geometry-based thinking;
- as evidence that sequence can help interpolation without abandoning interpretability;
- as a bridge toward prospective modeling.

## 6.2 Matrix-based backbone
### Adabor et al. (2018)
Use this paper for the claim that HI titers contain both antigenic and non-antigenic components and that Bayesian decomposition can separate them.

**How to use it in your review:**
- as a calibration-oriented response to assay artifacts;
- as evidence that raw titers are not pure antigenic signals;
- as support for your argument that the target variable itself is noisy and composite.

### Einav and Ma (2023)
Use this paper for the claim that matrix completion can infer missing antibody-virus interactions and quantify confidence, especially across heterogeneous studies with partial overlap.

**How to use it in your review:**
- as the strongest example of matrix reconstruction as a prediction problem;
- as support for the idea that sparse tables can be systematically extended;
- as evidence that uncertainty estimation matters when predicting unmeasured interactions.

## 6.3 Sequence-based backbone
### Yin et al. / IAV-CNN (2022)
Use this paper only as an early feasibility example.

**How to use it in your review:**
- to show the initial sequence-to-antigenicity framing often relied on binary classification;
- to mark the starting point of direct sequence learning.

### Shah et al. (2024)
This is a very useful paper for your revised narrative because it explicitly uses **past seasons only** to learn a seasonal mapping from sequence and metadata to normalized HI output.

**How to use it in your review:**
- as a strong example of operationally realistic evaluation;
- as evidence that prospective seasonal prediction is possible when time-aware protocols are used;
- as support for your critique that random splits are insufficient.

### Shi et al. / VaxSeer (2025)
This paper is especially important for your conclusion because it connects antigenicity prediction with **vaccine strain selection**, not just regression accuracy.

**How to use it in your review:**
- to show the field is moving toward decision-oriented evaluation;
- to support the claim that prediction should be aligned with future strain dominance and empirical antigenic match;
- to strengthen the public health significance of the review.

### Optional intermediate sequence paper: Li et al. (2024)
Use only if you need a middle step showing that models progressed from coarse classification to richer feature-driven regression and antigenic trajectory analysis.

---

## 7. How the literature should be synthesized, not listed
Below is the exact difference between the current style and the revised style.

## 7.1 Weak pattern: serial summary
> Smith et al. proposed antigenic cartography. Neher et al. proposed phylogeny-informed prediction. Fonville et al. applied this to antibody landscapes.

This is accurate, but it reads like note-taking.

## 7.2 Stronger pattern: comparative synthesis
> Early geometry-based studies treated antigenic relationships as distances in a latent map inferred from HI measurements, which made punctuated antigenic drift visible and highly interpretable. Later phylogeny-informed extensions preserved much of this interpretability while improving interpolation for unmeasured strains. However, because both approaches remain anchored to observed serology, they are less suitable than sequence-based models for genuinely prospective prediction under sparse surveillance.

This is what you should aim for in every category.

---

## 8. Sentence-level stylistic instructions
Even after structural revision, several language choices will help the paper sound more mature.

## 8.1 Prefer claim-comparison sentences over paper-reporting sentences
Prefer:
- "Geometry-based methods are most useful when interpretability is the primary goal."

Instead of:
- "Smith et al. showed that geometry-based methods can be useful."

## 8.2 Use contrast words strategically
Helpful connectors:
- however,
- by contrast,
- in practice,
- in this sense,
- taken together,
- while,
- although.

These help create synthesis without sounding mechanical.

## 8.3 Reduce publication-style self-promotion
Avoid too many phrases such as:
- "To the best of our knowledge"
- "This study makes three contributions"

For this assignment, the tone should be confident but not over-performative.

## 8.4 Minimize equations
If a mathematical expression is not essential for the reader's conceptual understanding, remove it. In this assignment, conceptual clarity matters more than formal completeness.

---

## 9. Suggested revised outline
Use this as the actual blueprint for rewriting.

# Introduction
### Move 1
HI assays are important for influenza surveillance and vaccine strain selection, but the observed data are sparse, selectively measured, censored, and heterogeneous across laboratories and time. These properties make raw titers difficult to interpret directly and motivate computational prediction.

### Move 2
Although many computational methods have been proposed, the field still lacks a systematic comparison of how different modeling assumptions affect interpretability, calibration, and prospective prediction under realistic surveillance conditions.

### Move 3
This review compares geometry-based, matrix-based, and sequence-based methods as three competing but complementary ways of representing virus-serum interaction.

# Literature Review
### Move 1
Briefly define the scope and comparison dimensions.

### Move 2
Three synthesis paragraphs:
1. geometry-based methods,
2. matrix-based methods,
3. sequence-based methods.

### Move 3
One paragraph with 2-3 prioritized research gaps.

### Move 4
One short concluding paragraph showing complementarity and motivating hybrid or better aligned future methods.

---

## 10. Final checklist before submission
Before you finalize the second version, check every paragraph against this list.

### Structure
- Does each paragraph serve one rhetorical move clearly?
- Does the paper still fit 1000-1500 words?
- Is the literature review built around comparison rather than enumeration?

### Argument
- Is the niche stated as a real gap, not just a description of diversity?
- Are the three method families compared using the same dimensions?
- Is the main research gap sharper than in the first draft?

### Critical evaluation
For every method family, have you stated:
- what it achieves,
- what it assumes,
- what it cannot do well,
- why that matters for surveillance?

### Language
- Have you removed unnecessary equations and contribution bullets?
- Have you reduced overly long sentences?
- Does the paper sound like a coherent academic argument rather than a stitched set of notes?

---

## 11. The single most important revision rule
If you remember only one sentence from this guide, make it this one:

> **Do not revise by adding more material; revise by making every paragraph do more argumentative work with less descriptive volume.**

That is the change most likely to move the paper from "already strong" to "excellent."
