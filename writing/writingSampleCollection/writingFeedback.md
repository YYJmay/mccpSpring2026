# Writing Feedback — YIN Yujia (殷宇佳)

YIN Yujia (殷宇佳) Student ID: 25482211 Email: 25482211@life.hkbu.edu.hk Programme: PHD COMP | Group: week7 GitHub: https://github.com/YYJmay/mccpSpring2026/tree/main/writing/writingSampleCollection

--- firstDraft.md ---
My First Draft
Source Information
Date written: 14 Feb 2026

Context: Task 3.2 writing sample (first draft; no supervisor/peer revision; for Writing Assignment – a survey for writing practice)

Status: Draft – Introduction complete; Literature Review drafted using a taxonomy of prior ML methods for HI titer prediction


Introduction
Move 1 – Establishing a Territory

Hemagglutination inhibition (HI) assays provide experimental evidence for antigen recognition between influenza viruses and reference vaccine strains \cite{smith2004mapping, koel2013substitutions}. These measurements support the selection of vaccine strains and guide public health decisions about antigenic change in human populations \cite{fonville2014antibody, li2024sequence,bedford2014integrating}. In recent years, the global circulation of influenza viruses has continued to increase in scale and diversity \cite{sawant2023h3n2,petrova2018evolution}. Therefore, rapid and reliable interpretation of hemagglutination inhibition data is important for public health \cite{neher2016prediction}.

Although the number of possible experiments increases with the amount of virus and antiserum, laboratory testing capacity remains limited \cite{shi2023improving,shi2024vaxseer,belongia2016variable}, which means that surveillance programs cannot test all experiments. As a result, the published HI data include only a portion of the complete table of possible interactions \cite{tricco2013comparing}. In addition, laboratories perform more experiments for viruses that raise public health concerns \cite{houser2015influenza,jalan2025optimal}, while other viruses receive little attention. Therefore, the missing entries in the data come from selective measurement rather than random omission \cite{jalan2025optimal}. The assay method also includes a finite range of dilutions. This limitation causes imprecise measurements when inhibition is weaker than the lowest tested dilution or stronger than the highest tested dilution \cite{smith2004mapping}. Variation across laboratories and variation across time further influence the values of the measurements \cite{dhanasekaran2022human, shah2024seasonal,chen2024covid}. Therefore, the direct use of raw titers can lead to incorrect conclusions. These challenges motivate the use of computational models that estimate unmeasured values and adjust for variation in the data \cite{einav2023using}.

Move 2 – Identifying a Niche

Recent advances in machine learning have led to a diverse set of approaches for predicting HI titers and related antigenic properties \cite{thadani2023learning,shi2025influenza}. Despite sharing a common objective, these methods follow different ideas about how to represent virus serum interactions. One idea is to place viruses and antisera in a latent coordinate space \cite{neher2016prediction}. A second idea is to complete the table of measurements by using structural patterns in the partially observed data \cite{einav2023using}. A third idea is to describe inhibition responses directly from amino acid sequences \cite{yin2021iav}. Each idea addresses different challenges in the data. Each idea also influences how researchers interpret results and how researchers extend predictions to viruses that appear in the future.

Move 3 – Occupying the Niche

This survey organizes existing computational approaches according to these representation spaces. We first formulate hemagglutination inhibition prediction as the estimation of missing values in a partially observed matrix with selective measurement and interval censoring. Then, we systematically review existing machine learning methods for this real-world problem. Our taxonomy shows that the three groups of methods provide different but related answers to a single modeling objective. This study also clarifies the assumptions made by each group of methods. A clear organization of these assumptions can support the development of new methods and the evaluation of existing methods in real surveillance settings. To the best of our knowledge, this is the first survey that provides a structured machine learning perspective on influenza HI titer prediction and vaccine strain selection. The main contributions of this work are as follows:

\begin{itemize} \item We formalize the statistical structure of HI learning by framing HI titers as noisy and selectively observed measurements of latent antigenic interaction, capturing sparsity, censoring, surveillance-driven missingness, and temporal variation in a unified formulation. \item We propose a representation-based taxonomy that organizes machine learning approaches into three categories, and provide a detailed analysis of the capabilities of representative work in each group. \item We highlight practical implications for influenza surveillance and vaccine strain selection, identifying strengths that already support operational use and open challenges that motivate new research directions in reliable prospective antigenic prediction. \end{itemize}


Literature Review
Move 1: Thematic Overview This survey organizes existing computational approaches according to these representation spaces. We first formulate hemagglutination inhibition prediction as the estimation of missing values in a partially observed matrix with selective measurement and interval censoring. Then, we systematically review existing machine learning methods for this real-world problem. Our taxonomy shows that the three groups of methods provide different but related answers to a single modeling objective. This study also clarifies the assumptions made by each group of methods. A clear organization of these assumptions can support the development of new methods and the evaluation of existing methods in real surveillance settings. To the best of our knowledge, this is the first survey that provides a structured machine learning perspective on influenza HI titer prediction and vaccine strain selection.

Machine learning approaches to HI titer prediction differ in how they represent virus–serum interactions. Although the supervised target is always the observed titer $Y_{ij}$, models operate in distinct representation spaces. Geometry–based approaches derive antigenic coordinates from pairwise titers. Matrix–based approaches reconstruct a latent antigenic surface from incomplete and biased measurements. Sequence–based approaches learn a direct mapping from viral and serum sequences to inhibition activity. Grouping methods by representational assumptions clarifies their complementary strengths in interpretability, data calibration, and inductive generalization. In this section, we analyze representative methods in each category to highlight how their core ideas determine modeling capability and practical utility.

Move 2: Critical Analysis \subsection{Category I: Geometry Derived from Pairwise Titers}

The defining feature of this category is that antigenic cross reactivity is modeled as a function of geometric distance in a latent space that is inferred entirely from observed HI responses. These methods assume that antigenic evolution can be represented by movement in this space \cite{smith2004mapping}, and they seek to recover geometry that explains measured titers.

Let $\mathbf{z}{v_i}$ and $\mathbf{z}{s_j}$ denote the latent coordinates of virus $v_i$ and antiserum $s_j$ in $\mathbb{R}^{d}$. The predicted log dilution is a monotone transformation of their Euclidean distance [\hat{Y}{ij} = g!\Bigl(\lVert \mathbf{z}{v_i} - \mathbf{z}_{s_j} \rVert\Bigr),] reflecting the empirical observation that nearer antigenic proximity corresponds to stronger inhibition.

\paragraph{Euclidean geometry inferred from titer tables}

Smith et al.\ introduced metric multidimensional scaling to fit a latent Euclidean landscape from the HI map \cite{smith2004mapping}. This antigenic cartography offers computational advantages over the ordinal approach This method assumes a linear relationship between antigen distance and the logarithm of HI titer, and then uses this relationship to establish a parameterized formula. This method is the first to explicitly consider censored HI observations and can be used to detect measurements that are outside the detection sensitivity range. The resulting maps resolve punctuated antigenic transitions that align with vaccine updates and are widely used in routine surveillance \cite{smith2004mapping,han2023co,huang2023immune}.

This approach is fully serology driven. The geometry exists only where measurements exist, and thus the model is transductive. A newly observed sequence cannot be positioned until its titers are measured.

\paragraph{Phylogeny informed geometric interpolation} Neher et al. observed that antigenic differences learned from HI titers follow an additive structure along the phylogenetic tree of hemagglutinin \cite{neher2016prediction}. For a test virus $a$ and an antiserum $\beta$ raised against reference virus $b$, the standardized log titer is modeled as [\widehat{H}{a\beta}=v_a + p{\beta} + \sum_{i \in (a \rightarrow b)} d_i,] where $v_a$ and $p_{\beta}$ are virus and serum specific effects and each branch contribution $d_i \ge 0$ is regularized to encourage sparsity. Because previously unmeasured strains still occupy defined positions on the tree, the model supports interpolation for such strains.

This sequence informed representation maintains geometric interpretability and improves predictive accuracy. Its inductive power remains limited to lineages with reliable phylogenetic placement.

The geometric representation inferred from HI titers has enabled downstream applications beyond antigenic distance estimation. Fonville et al.\ \cite{fonville2014antibody} demonstrated how antigenic coordinates provide a quantitative scaffold for analyzing human immune responses. For a given serum, log titers against a virus panel are projected onto the antigenic map and fitted as a smooth surface, forming an antibody landscape. This visualization captures how prior exposures elevate responses across antigenic space and supports assessment of vaccine update strategies in real populations.

These applications illustrate how geometry based models translate serological measurements into decision relevant insights. Euclidean maps provide a direct and interpretable view of antigenic evolution, while phylogeny informed geometry supports limited inductive interpolation through sequence structure. However, both approaches depend on selectively acquired titers, do not model the observation process, and can be influenced by differences in laboratory protocols. Because new strains cannot be positioned without either measured titers or reliable phylogenetic anchoring, generalization to future circulation remains constrained.

Motivated by these limitations, subsequent methodological advances introduce explicit biological features or directly learn the mapping from sequences to inhibition activity. These developments form the basis of the modeling categories discussed in the following sections.

\subsection{Category II: Matrix-based Reconstruction of Antigenic Surfaces} \label{sec:ml_hi_reconstruction}

These methods argue that antigenic interactions are fundamentally represented as a complete virus–serum matrix, rather than geometric distances between viruses. However, in practice, testing each virus-serum pair is extremely expensive and almost impossible, which results in the empirical measurement matrix $\mathbf{Y}$ being both sparse and systematically distorted by non-antigenic experimental effects. Thus the learning problem becomes to reconstruct a latent antigenic surface $\mathbf{Z}$ that reflects true interaction strengths. Formally, the goal is to estimate $\mathbf{Z}$ from the observed entries: [\widehat{\mathbf{Z}} =\arg\min_{\mathbf{Z}}\sum_{(i,j)\in\mathcal{O}}\ell!\bigl(Y_{ij},g(Z_{ij};\phi_i,\psi_j)\bigr)+\lambda,\Omega(\mathbf{Z}),] where $\mathcal{O}$ is the set of measured entries, $g$ represents non-antigenic effects associated with virus and serum, and $\Omega$ encodes a structural prior for $\mathbf{Z}$. Two types of structure have been used.

\paragraph{Latent effect separation.} One strategy explicitly parameterizes non-antigenic factors so that only the residual signal reflects antigenic affinity. Adabor et al.~\cite{adabor2018bayesian} intrintroduces ierarchical Bayesian model in which each log$_2$ titer is decomposed into a serum amplitude term, a virus-specific component capturing receptor binding avidity, and a latent interaction parameter representing antigenic compatibility. Posterior inference reduces inter-laboratory bias and eliminates spurious temporal shifts, yielding calibrated antigenic interactions that improve downstream evolutionary interpretation.

\paragraph{Low-rank structure.}

A complementary direction exploits the empirical observation that virus–serum interaction matrices have low effective rank. Einav et al.~\cite{einav2022extrapolating} formulate reconstruction as nuclear-norm minimization over transformed titers and demonstrate that, within a study, the resulting completion reaches errors close to experimental noise. When merging studies with partially overlapping panels, this approach accurately recovers entire missing virus columns provided the studies are temporally or procedurally aligned. The reconstructed matrix also supports principled experimental design: sample–error learning curves supply stopping rules for new measurements, and ranking imputed titers efficiently prioritizes assays that identify strong or weak interactions.

The reconstructed antigenic matrix serves a foundational role. It densifies supervision for mapping approaches operating in geometric latent spaces and provides more reliable training signals for sequence-to-interaction models. Future work must better account for surveillance-driven missingness and interval-censored reporting, ensuring that reconstruction remains aligned with the data acquisition process.

\subsection{Category III: Sequence-to-Interaction Prediction} \label{sec:seq_model}

--- reflection.md ---
My Reflection on Writing
Writing Challenges and Difficulties
What aspects of academic writing do you find most challenging? For me, the most demanding aspect of academic writing is maintaining a strong narrative thread while dealing with complex technical material. In this survey draft, I invested significant effort in formalizing the HI prediction problem and organizing methods into representation-based categories. Although this gives the paper a clear analytical structure, I sometimes become overly focused on conceptual precision and modeling details. As a result, the broader story—why this problem is critical for influenza surveillance and vaccine decision-making—may not be emphasized as clearly as it should be.

Another challenge is ensuring that each section advances the central argument rather than functioning as an isolated block of information. Because I structure my writing around conceptual categories, transitions between sections may feel logical to me but not necessarily to a reader encountering the topic for the first time.

What specific difficulties do you face when writing Introduction/Literature Review? In the Introduction, my main difficulty lies in articulating the research gap in a sharp and concise way. In this draft, I described sparsity, censoring, selection bias, and temporal drift in detail, but I am not fully confident that I clearly state what is fundamentally missing in current modeling approaches. I tend to explain the problem structure thoroughly, yet the "so what?"—why this gap has not been adequately addressed—could be more explicitly highlighted.

In the Literature Review, I organized prior work into three representation spaces (geometry-based, matrix-based, and sequence-based). While this taxonomy provides coherence, I sometimes worry that the section becomes systematically descriptive rather than critically comparative. I describe representative methods and their assumptions, but I could engage more deeply with their limitations, especially regarding deployment under selective surveillance conditions. Additionally, because the review follows modeling logic, it may underemphasize the practical consequences of those modeling choices.

What do you struggle with most? I struggle most with making technically dense sections accessible without oversimplifying them. For example, in the statistical formulation and generative modeling sections, I use formal definitions to clarify assumptions. However, I may not always provide enough intuitive explanation to help readers understand why these assumptions matter in practice. Since I am comfortable with mathematical abstraction, I sometimes underestimate how much contextual guidance is needed. Improving reader-oriented explanation is therefore an important goal for me.


My Writing Process
How do you approach writing Introduction and Literature Review? For this survey, I began by clarifying the conceptual backbone of the paper: defining the HI learning problem and identifying differences in representation space as the organizing principle. I usually work from structure outward. I first decide how sections relate logically, and only then do I write detailed paragraphs. This approach helps me avoid disorganized writing, but it may also lead to sections that feel structurally clean yet rhetorically underdeveloped.

What steps do you take? My writing process generally follows these stages:

Systematically collect and categorize relevant literature.

Identify a conceptual framework (in this case, representation space) to organize prior work.

Draft sections focusing on conceptual clarity rather than stylistic refinement.

Revise for logical consistency and remove internal redundancy.

Refine language and improve readability.

In this draft, I revised primarily at the paragraph level. I now realize that I should also revise at the argument level, asking whether each section strengthens the central positioning of the survey.

Do you have a particular method or strategy? My guiding principle is to secure structural coherence before polishing language. I believe that once the conceptual framework is stable, stylistic improvements become more meaningful. However, I am learning that structure alone is not sufficient; the persuasive force of the argument depends on how explicitly the research gap and implications are framed.


How I Use AI for Help
Do you use AI tools (ChatGPT, Claude, etc.) to help with writing? Yes, GPT5.2

How do you use them? for brainstorming, drafting, editing, checking grammar, improving sentences

What prompts do you typically use? [Share examples of prompts you use, if comfortable]

What do you find helpful or not helpful about AI assistance? AI is helpful for surface-level improvements and readability enhancement. It can identify awkward phrasing or suggest more concise wording. However, it does not automatically strengthen conceptual positioning or deepen critical analysis. The responsibility for sharpening the research gap and ensuring argumentative coherence remains mine. I treat AI as an editing assistant rather than a source of intellectual content.


My Goals
What do you hope to improve in your writing? I want to improve my ability to articulate research gaps earlier and more decisively, especially in the Introduction. I also want my writing to reflect a stronger critical stance in the Literature Review rather than a neutral summary of prior methods.

What specific skills do you want to develop? More explicit signaling of argumentative progression.

Deeper comparative evaluation of modeling assumptions.

Clearer translation of formal statistical formulations into intuitive explanations.

Stronger integration between technical discussion and real-world decision contexts.

Greater conciseness without sacrificing analytical rigor.


Additional Notes
[Any other thoughts about your writing, concerns, questions, etc.]



