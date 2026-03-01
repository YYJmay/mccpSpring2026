# My First Draft

## Source Information

**Date written:** 14 Feb 2026

**Context:** Task 3.2 writing sample (first draft; no supervisor/peer revision; for Writing Assignment – a survey for writing practice) 

**Status:** Draft – Introduction complete; Literature Review drafted using a taxonomy of prior ML methods for HI titer prediction

---

## Introduction

- Move 1 – Establishing a Territory

Hemagglutination inhibition (HI) assays provide experimental evidence for antigen recognition between influenza viruses and reference vaccine strains \cite{smith2004mapping, koel2013substitutions}. These measurements support the selection of vaccine strains and guide public health decisions about antigenic change in human populations \cite{fonville2014antibody, li2024sequence,bedford2014integrating}. In recent years, the global circulation of influenza viruses has continued to increase in scale and diversity \cite{sawant2023h3n2,petrova2018evolution}. Therefore, rapid and reliable interpretation of hemagglutination inhibition data is important for public health \cite{neher2016prediction}.

Although the number of possible experiments increases with the amount of virus and antiserum, laboratory testing capacity remains limited \cite{shi2023improving,shi2024vaxseer,belongia2016variable}, which means that surveillance programs cannot test all experiments.
As a result, the published HI data include only a portion of the complete table of possible interactions \cite{tricco2013comparing}. In addition, laboratories perform more experiments for viruses that raise public health concerns \cite{houser2015influenza,jalan2025optimal}, while other viruses receive little attention. Therefore, the missing entries in the data come from selective measurement rather than random omission \cite{jalan2025optimal}. The assay method also includes a finite range of dilutions. This limitation causes imprecise measurements when inhibition is weaker than the lowest tested dilution or stronger than the highest tested dilution \cite{smith2004mapping}. Variation across laboratories and variation across time further influence the values of the measurements \cite{dhanasekaran2022human, shah2024seasonal,chen2024covid}. Therefore, the direct use of raw titers can lead to incorrect conclusions. These challenges motivate the use of computational models that estimate unmeasured values and adjust for variation in the data \cite{einav2023using}.

- Move 2 – Identifying a Niche

Recent advances in machine learning have led to a diverse set of approaches for predicting HI titers and related antigenic properties \cite{thadani2023learning,shi2025influenza}.
Despite sharing a common objective, these methods follow different ideas about how to represent virus serum interactions. One idea is to place viruses and antisera in a latent coordinate space \cite{neher2016prediction}. A second idea is to complete the table of measurements by using structural patterns in the partially observed data \cite{einav2023using}. A third idea is to describe inhibition responses directly from amino acid sequences \cite{yin2021iav}. Each idea addresses different challenges in the data. Each idea also influences how researchers interpret results and how researchers extend predictions to viruses that appear in the future.

- Move 3 – Occupying the Niche

This survey organizes existing computational approaches according to these representation spaces. We first formulate hemagglutination inhibition prediction as the estimation of missing values in a partially observed matrix with selective measurement and interval censoring. 
Then, we systematically review existing machine learning methods for this real-world problem.
Our taxonomy shows that the three groups of methods provide different but related answers to a single modeling objective. This study also clarifies the assumptions made by each group of methods. A clear organization of these assumptions can support the development of new methods and the evaluation of existing methods in real surveillance settings. To the best of our knowledge, this is the first survey that provides a structured machine learning perspective on influenza HI titer prediction and vaccine strain selection. The main contributions of this work are as follows:

\begin{itemize}
    \item We formalize the statistical structure of HI learning by framing HI titers as noisy and selectively observed measurements of latent antigenic interaction, capturing sparsity, censoring, surveillance-driven missingness, and temporal variation in a unified formulation.
    \item We propose a representation-based taxonomy that organizes machine learning approaches into three categories, and provide a detailed analysis of the capabilities of representative work in each group.
    \item We highlight practical implications for influenza surveillance and vaccine strain selection, identifying strengths that already support operational use and open challenges that motivate new research directions in reliable prospective antigenic prediction.
\end{itemize}




---

## Literature Review


- Move 1: Thematic Overview
  This survey organizes existing computational approaches according to these representation spaces. We first formulate hemagglutination inhibition prediction as the estimation of missing values in a partially observed matrix with selective measurement and interval censoring. Then, we systematically review existing machine learning methods for this real-world problem. Our taxonomy shows that the three groups of methods provide different but related answers to a single modeling objective. This study also clarifies the assumptions made by each group of methods. A clear organization of these assumptions can support the development of new methods and the evaluation of existing methods in real surveillance settings. To the best of our knowledge, this is the first survey that provides a structured machine learning perspective on influenza HI titer prediction and vaccine strain selection. 

  Machine learning approaches to HI titer prediction differ in how they represent virus–serum interactions. Although the supervised target is always the observed titer $Y_{ij}$, models operate in distinct representation spaces. Geometry–based approaches derive antigenic coordinates from pairwise titers. Matrix–based approaches reconstruct a latent antigenic surface from incomplete and biased measurements. Sequence–based approaches learn a direct mapping from viral and serum sequences to inhibition activity. Grouping methods by representational assumptions clarifies their complementary strengths in interpretability, data calibration, and inductive generalization. In this section, we analyze representative methods in each category to highlight how their core ideas determine modeling capability and practical utility.

- Move 2: Critical Analysis
  \subsection{Category I: Geometry Derived from Pairwise Titers}

  The defining feature of this category is that antigenic cross reactivity is modeled as a function of geometric distance in a latent space that is inferred entirely from observed HI responses. These methods assume that antigenic evolution can be represented by movement in this space \cite{smith2004mapping}, and they seek to recover geometry that explains measured titers.

  Let $\mathbf{z}_{v_i}$ and $\mathbf{z}_{s_j}$ denote the latent coordinates of virus $v_i$ and antiserum $s_j$ in $\mathbb{R}^{d}$. The predicted log dilution is a monotone transformation of their Euclidean distance
  \[
  \hat{Y}_{ij} = g\!\Bigl(\lVert \mathbf{z}_{v_i} - \mathbf{z}_{s_j} \rVert\Bigr),
  \]
  reflecting the empirical observation that nearer antigenic proximity corresponds to stronger inhibition.

  \paragraph{Euclidean geometry inferred from titer tables}

  Smith et al.\ introduced metric multidimensional scaling to fit a latent Euclidean landscape from the HI map \cite{smith2004mapping}. This antigenic cartography offers computational advantages over the ordinal approach
  This method assumes a linear relationship between antigen distance and the logarithm of HI titer, and then uses this relationship to establish a parameterized formula. This method is the first to explicitly consider censored HI observations and can be used to detect measurements that are outside the detection sensitivity range.
  The resulting maps resolve punctuated antigenic transitions that align with vaccine updates and are widely used in routine surveillance \cite{smith2004mapping,han2023co,huang2023immune}.

  This approach is fully serology driven. The geometry exists only where measurements exist, and thus the model is transductive. A newly observed sequence cannot be positioned until its titers are measured.

  \paragraph{Phylogeny informed geometric interpolation}
  Neher et al. observed that antigenic differences learned from HI titers follow an additive structure along the phylogenetic tree of hemagglutinin \cite{neher2016prediction}. For a test virus $a$ and an antiserum $\beta$ raised against reference virus $b$, the standardized log titer is modeled as
  \[
  \widehat{H}_{a\beta}
  =
  v_a + p_{\beta} + \sum_{i \in (a \rightarrow b)} d_i,
  \]
  where $v_a$ and $p_{\beta}$ are virus and serum specific effects and each branch contribution $d_i \ge 0$ is regularized to encourage sparsity. Because previously unmeasured strains still occupy defined positions on the tree, the model supports interpolation for such strains.
 
  This sequence informed representation maintains geometric interpretability and improves predictive accuracy. Its inductive power remains limited to lineages with reliable phylogenetic placement.

  The geometric representation inferred from HI titers has enabled downstream applications beyond antigenic distance estimation. Fonville et al.\ \cite{fonville2014antibody} demonstrated how antigenic coordinates provide a quantitative scaffold for analyzing human immune responses. For a given serum, log titers against a virus panel are projected onto the antigenic map and fitted as a smooth surface, forming an antibody landscape. This visualization captures how prior exposures elevate responses across antigenic space and supports assessment of vaccine update strategies in real populations.

  These applications illustrate how geometry based models translate serological measurements into decision relevant insights. Euclidean maps provide a direct and interpretable view of antigenic evolution, while phylogeny informed geometry supports limited inductive interpolation through sequence structure. However, both approaches depend on selectively acquired titers, do not model the observation process, and can be influenced by differences in laboratory protocols. Because new strains cannot be positioned without either measured titers or reliable phylogenetic anchoring, generalization to future circulation remains constrained.

  Motivated by these limitations, subsequent methodological advances introduce explicit biological features or directly learn the mapping from sequences to inhibition activity. These developments form the basis of the modeling categories discussed in the following sections.

  \subsection{Category II: Matrix-based Reconstruction of Antigenic Surfaces}
  \label{sec:ml_hi_reconstruction}

  These methods argue that antigenic interactions are fundamentally represented as a complete virus–serum matrix, rather than geometric distances between viruses. 
  However, in practice, testing each virus-serum pair is extremely expensive and almost impossible, which results in the empirical measurement matrix $\mathbf{Y}$ being both sparse and systematically distorted by non-antigenic experimental effects.
  Thus the learning problem becomes to reconstruct a latent antigenic surface $\mathbf{Z}$ that reflects true interaction strengths.
  Formally, the goal is to estimate $\mathbf{Z}$ from the observed entries:
  \[
  \widehat{\mathbf{Z}} = 
  \arg\min_{\mathbf{Z}} 
  \sum_{(i,j)\in\mathcal{O}}
  \ell\!\bigl(Y_{ij},g(Z_{ij};\phi_i,\psi_j)\bigr)
  +\lambda\,\Omega(\mathbf{Z}),
  \]
  where $\mathcal{O}$ is the set of measured entries, $g$ represents
  non-antigenic effects associated with virus and serum, and $\Omega$ encodes a
  structural prior for $\mathbf{Z}$. Two types of structure have been used.

  \paragraph{Latent effect separation.}
  One strategy explicitly parameterizes non-antigenic factors so that only the
  residual signal reflects antigenic affinity. Adabor et al.~\cite{adabor2018bayesian} intrintroduces ierarchical Bayesian model in which each
  log$_2$ titer is decomposed into a serum amplitude term, a virus-specific
  component capturing receptor binding avidity, and a latent interaction
  parameter representing antigenic compatibility. Posterior inference reduces
  inter-laboratory bias and eliminates spurious temporal shifts, yielding
  calibrated antigenic interactions that improve downstream evolutionary
  interpretation.

  \paragraph{Low-rank structure.}

  A complementary direction exploits the empirical observation that virus–serum interaction matrices have low effective rank. Einav et al.~\cite{einav2022extrapolating} formulate reconstruction as nuclear-norm minimization over transformed titers and demonstrate that, within a study, the resulting completion reaches errors close to experimental noise. When merging studies with partially overlapping panels, this approach accurately recovers
  entire missing virus columns provided the studies are temporally or procedurally aligned. The reconstructed matrix also supports principled experimental design: sample–error learning curves supply stopping rules for new
  measurements, and ranking imputed titers efficiently prioritizes assays that identify strong or weak interactions.

  The reconstructed antigenic matrix serves a foundational role. It densifies supervision for mapping approaches operating in geometric latent spaces and provides more reliable training signals for sequence-to-interaction models. Future work must better account for surveillance-driven missingness and interval-censored reporting, ensuring that reconstruction remains aligned with
  the data acquisition process.

  \subsection{Category III: Sequence-to-Interaction Prediction}
  \label{sec:seq_models}

  Category~III replaces latent antigenic geometry with direct learning of the interaction between a circulating virus $v_i$ and a reference serum $s_j$ from their hemagglutinin sequences,
  \[
  f:\bigl(\mathrm{seq}(v_i),\,\mathrm{seq}(s_j)\bigr) \rightarrow \hat{Y}_{ij}.
  \]
  This inductive formulation uniquely enables predictions for newly emerged viruses lacking serological assays, directly supporting prospective decision making.

  Representative developments can be understood along three methodological axes: the supervision signal, the treatment of residue-level causality, and the handling of temporal and laboratory heterogeneity.

  \paragraph{Supervision signal: from binary variant calls to continuous antigenic phenotypes.}
  Initial studies established feasibility using coarse binary targets. IAV--CNN~\cite{yin2021iav} embeds HA sequences via ProtVec 3-grams and applies convolutional classification to determine whether two strains exceed an Archetti--Horsfall antigenic threshold. This demonstrated that sequence differences alone encode actionable antigenic cues. To recover graded drift magnitudes, MFPAD~\cite{li2024sequence} instead regresses continuous antigenic distances obtained from low-rank HI matrix completion. The richer supervision improves interpretability through drift trajectories, though distance estimates propagate biases from observed assays. A complementary route regresses sequence embeddings directly to antigenic map (AM) coordinates. Durazzi et al. \cite{durazzi2025language} compares Hamming-, physicochemical-, BiLSTM-, and ProtBERT-based embeddings with a common ridge regressor, finding that language-model embeddings match coarse AM structure and markedly improve fine-grained tasks.

  \paragraph{Residue representation: from descriptive features to mechanistic attribution.}
  Feature engineering has increasingly incorporated biological insight. MFPAD encodes glycosylation motif changes, canonical epitope mutations, and physicochemical shifts to enhance predictive stability. Harvey et al.~\cite{harvey2023bayesian} go further by modeling latent log$_2$ titers with hierarchical site--substitution parameters and Bayesian stochastic search. Structure-aware priors based on receptor-binding-site proximity and epitope accessibility raise posterior certainty for truly causal positions, improving mechanistic interpretability albeit with higher computational cost.

  \paragraph{Deployment robustness: from random splits to operational workflows.}
  Realistic deployment must avoid temporal leakage \cite{dhanasekaran2022human} and correct for laboratory variation. Shah et al.~\cite{shah2024seasonal} enforce a season-aware protocol aligned with WHO timelines and augment sequence-difference features with metadata on virus avidity, serum potency, and passage history, producing stable genotype-to-antigenicity prediction. VaxSeer further elevates this direction by integrating a sequence-based antigenicity model with a forward dominance predictor parameterized by protein language models, yielding a coverage score that jointly reflects antigenic similarity and expected circulation.\cite{shi2025influenza} Retrospective analyses show strong correlation with vaccine effectiveness and improved candidate rankings relative to WHO decisions, illustrating how sequence models can transition from HI prediction to actionable vaccine selection.

  Across these axes, sequence-to-interaction models capitalize on advances in protein representation learning and offer the only path to truly prospective antigenic evaluation. Persistent challenges include non-random assay acquisition, cross-laboratory variability, and the absence of an explicit antigenic geometry for communication and uncertainty quantification. These limitations motivate hybrid approaches that combine the inductive strengths of sequence encoders with geometric constraints and explicit models of the surveillance process.


- Move 3: Research Gaps
  \subsection{Comparison Across Modeling Categories}

  The three categories reflect distinct representational assumptions about antigen--serum interactions. Geometry-based models interpret antigenic relationships as distances in a Euclidean or phylogeny-informed space learned directly from titers \cite{smith2004mapping,neher2016prediction}. Matrix-based models assume that the full interaction landscape is a latent surface that can be estimated from sparse and heterogeneous measurements \cite{adabor2018bayesian,einav2022extrapolating}. Sequence models treat the response as a function of viral and serum amino acid sequences, enabling inductive prediction for previously unassayed strains \cite{yin2021iav,li2024sequence,harvey2023bayesian,shah2024seasonal,shi2025influenza}.

  These representational choices determine how each category addresses the key data challenges summarized in Section~\ref{sec:data_problem}. Geometry recovers interpretable evolutionary structure and enables antibody landscape visualization \cite{fonville2014antibody}, but prediction for unseen variants is limited without supporting phylogeny or assays. Matrix reconstruction reduces sparsity and mitigates systematic non-antigenic effects \cite{adabor2018bayesian}, and can align multi-study data for improved calibration \cite{einav2022extrapolating}, yet most approaches still assume missingness that is independent of antigenicity and treat interval-censored values as exact. Sequence-based models support real-time evaluation of emerging strains and can incorporate censoring via a likelihood formulation \cite{harvey2023bayesian}, but remain sensitive to biases in the observed table and provide minimal geometric structure for communicating evolutionary transitions.

  The categories are therefore complementary rather than competing. Geometry offers interpretability grounded in serological evidence. Matrix reconstruction supplies debiased and dense supervision. Sequence models extend predictions into the future and broaden decision coverage. Recent studies already couple these capabilities: continuous antigenic distances from matrix completion are used as regression targets for sequence models \cite{li2024sequence}, while phylodynamic geometry informs interpolation for strains lacking assays \cite{neher2016prediction}. Hybrid pipelines that exploit these synergies are essential for operational vaccine strain selection, where interpretability, calibration under biased sampling, and prospective generalization must be satisfied simultaneously. Table~\ref{tab:model_comparison} summarizes the contrasts along these dimensions.

  \begin{table*}[t]
  \centering
  \caption{
  Representative computational approaches for antigenic characterization,
  organized by the representation space in which virus–serum interactions
  are modeled. 
  }
  \label{tab:model_comparison}
  \resizebox{\textwidth}{!}{
  \begin{tabular}{@{}lcccccccc@{}}
  \toprule
  \textbf{Method} & \textbf{Year} & \textbf{Venue}  & \textbf{Space} & \textbf{Target} & \textbf{Sparse} & \textbf{Censor.} & \textbf{MNAR} & \textbf{Key Idea} \\
  \midrule
  Antigenic Cartography~\cite{smith2004mapping} & 2004 & Science & Geo & Map & N & Y & N & MDS \\
  Tree~\cite{neher2016prediction}  & 2016 & PNAS & Geo & Map/HI& N & N & N & Phylo-add \\
  \midrule
  Bayesian Decomposition~\cite{adabor2018bayesian}& 2018 & RSOS & Matrix-Z & HI & Partial& N & Partial & Bayes-decomp \\
  Matrix Completion~\cite{einav2022extrapolating} & 2022 & Cell Syst.  & Matrix-Z & HI & Y& N & Partial & NucNorm \\
  \midrule
  IAV-CNN~\cite{yin2021iav} & 2021 & IEEE/ACM T-CBB  & Seq & similar/distinct & Y& N & Y  & CNN \\
  MFPAD~\cite{li2024sequence} & 2024 & Front. Microbiol.  & Seq & Dist & Y& N & Y & Feat-epi/glyco \\
  BSSVS~\cite{harvey2023bayesian}  & 2023 & PLoS CB & Seq & HI & Y& N & Y & Structure+BSSVS \\
  AdaBoost~\cite{shah2024seasonal}  & 2024 & Nat Commun.  & Seq & HI/NHT & Y& Partial & Y & Season-split \\
  VaxSeer~\cite{shi2025influenza}  & 2025 & Nat Med. & Seq & Coverage & Y& Partial & Y & Dominance+LM \\
  LM2AM~\cite{durazzi2025language}  & 2025 & Sci Rep.& Seq & MAP & Y& Partial & Y &  LM-embed \\
  \bottomrule
  \end{tabular}
  }
  \par\medskip
  \footnotesize
  \textbf{Abbreviations:} MDS: multidimensional scaling; Phylo-add: tree-additive model; Bayes-decomp: assay-aware Bayesian decomposition; NucNorm: nuclear-norm completion; 
  Feat-epi/glyco: epitope/glycan features; 
  Structure+BSSVS: structure-informed site/substitution selection; Season-split: season-aware train/test protocol; Dominance+LM: sequence-driven dominance + antigenicity for coverage; LM-embed: protein language model embeddings.
  \end{table*}


  \section{Future Directions}
  The studies reviewed in this work indicate that reliable prediction of HI titers requires more than accurate estimation of observed values. Therefore, surveillance settings demand methods that remain valid when observations are incomplete, when observations follow selection rules, and when observations come from changing laboratory practice. We outline three directions in which future research can provide progress.

  \paragraph{Learning under selective surveillance.}
  HI measurements come from requests for viruses that show concerning signals in public health surveillance \cite{adabor2018bayesian}. Therefore, selection rules for measurement depend on the unknown antigen relationships. However, several current methods assume that missing values do not depend on antigen relationships and do not express uncertainty about the selection process. Future research needs models that include explicit sampling rules \cite{jalan2025optimal} and that produce calibrated uncertainty when surveillance priorities change across time. These advances can reduce bias in estimates of antigen change and can improve robustness when measurements become scarce in parts of the antigen space.

  \paragraph{Immunologically grounded representations.}
  Current methods that use geometry, current methods that use matrix structure, and current methods that use sequence representation capture different aspects of antigen change \cite{shi2024vaxseer}. Therefore, future models can improve generalization when models include information about receptor binding sites, accessible regions of the antigen, and the smooth nature of antigen evolution. Representations that follow biological rules of antibody recognition can reduce sensitivity to changes in circulating viruses and can help identify key drivers of antigen change \cite{li2024sequence}.

  \paragraph{Decision alignment and evaluation under deployment conditions.}
  Most current models learn from past titers by using regression losses \cite{wang2018predicting,zeller2021machine}, although the real goal of surveillance is to support selection of vaccine components. Therefore, evaluation should reward correct ordering of viruses that appear in future seasons \cite{dhanasekaran2022human,einav2022using}, stable prediction when the distribution changes, and the expression of uncertainty around levels of protection. Protocols such as evaluation by time and evaluation across laboratories are needed in order to measure these properties in practical surveillance.

- Move 4: Conclusion

  This survey formalizes HI titer prediction as inference on a sparse and selectively measured interaction matrix that includes interval censoring and temporal shift. It organizes existing methods by the representation they use: geometry learned directly from titers, matrix based reconstruction of latent antigenic surfaces, and sequence based prediction. The review shows that these representations address different parts of the problem: geometry provides interpretable structure, matrix approaches supply denser and more calibrated supervision, and sequence models enable prospective evaluation for new strains. Together, these perspectives motivate hybrid pipelines that couple missingness aware reconstruction, sequence encoders, and decision oriented objectives. In the future, closing gaps related to selection bias, censoring aware likelihoods, and uncertainty that directly supports vaccine ranking will be essential for practical deployment in surveillance.



---

## Notes


