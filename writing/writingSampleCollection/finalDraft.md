# My Final Draft

## Source Information


Writing Date: 14 March
Context: MCCP 2026 Spring Writing Course Homework. 
Status: Complete the draft.

---

## Introduction

### Move 1 Establishing a Territory

Hemagglutination inhibition (HI) determination provides experimental evidence for antigen identification between influenza virus and reference vaccine strains \cite{smith2004mapping, koel2013substitutions}. These measurements support the selection of vaccine strains and guide public health decision-making on antigen changes in circulating populations \cite{fonville2014antibody, li2024sequence, bedford2014integrating}. As  the global transmission scale and diversity of the influenza virus continue to increase\cite{sawant2023h3n2, petrova2018evolution}, the fast and reliable interpretation of HI data is crucial to public health\cite{neher2016prediction}. More reliable computational predictions can reduce the number of laboratory measurements required to characterize emerging strains and support faster vaccine strain recommendations. However, this actual value depends on the data coverage that the monitoring system cannot fully provide in daily operation.

Because the monitoring program cannot detect all virus serum pairs, the observed HI table is very incomplete\cite{einav2022extrapolating}. Measurement coverage is formed by practical and public health priorities rather than unified sampling, so the available data is not all neutral samples that may interact\cite{smith2004mapping, adabor2018bayesian}. The assay itself introduces interval censoring, because values are imprecise when inhibition falls outside the tested dilution range \cite{smith2004mapping}. Passage effects, variation across laboratories, and changes over time further influence recorded values \cite{adabor2018bayesian, shah2024seasonal}. These constraints make computational modeling necessary, but they also make model choice important because different methods respond to sparsity, heterogeneity, and forward prediction needs in different ways.

### Move 2 Identifying a Niche

In response to these data constraints, computational HI prediction has progressed rapidly. However, the literature still lacks a clear comparative account of how different modeling assumptions shape performance under realistic surveillance conditions. In particular, geometry based, matrix based, and sequence based methods differ in their dependence on observed titers, their handling of sparsity and assay variation, and their ability to generalize to newly emerging strains. These trade offs are therefore rarely compared in a structured way across method families, especially in terms of interpretability, calibration under sparse heterogeneous observations, and prospective utility.

### Move 3 Occupying the Niche

In order to solve this comparative gap, this review studies three main families of computational HI prediction methods, namely geometry-based, matrix-based and sequence-based methods, through the assumption of viral serum interaction. It believes that these assumptions determine whether a method is most useful for antigen interpretation, sparse data reconstruction or prospective prediction of emerging strains. By organizing literature around these representative commitments, it is reviewed and clarified which capabilities have matured and which method gaps still limit the deployment in monitoring practice.

---

## Literature Review

### Move 1 Thematic Overview

Machine learning approaches to HI prediction differ mainly in how they represent virus serum relationships. Geometry based methods infer antigenic structure directly from measured serology. Matrix based methods reconstruct incomplete interaction tables while accounting, to some degree, for assay related distortion. Sequence based methods infer antigenic similarity or HI related outcomes from sequence derived features. In this review, these families are compared in terms of interpretability, robustness to sparse and mixed observations, and generalization to newly emerging strains.

### Move 2 Critical Analysis

#### Geometry based methods

Geometry-based approaches simulates the antigen correlation as the distance in the hidden space inferred from the HI measurement. Smith et al. \cite{smith2004mapping} introduced antigenic cartography and showed that HI data could be placed on an antigenic map. This map made major shifts over time easier to see and gave surveillance work a clear way to describe antigenic change. Neher et al. \cite{neher2016prediction} extended this idea by linking antigenic change to the phylogeny, which allowed limited prediction for strains without direct serological data. Taken together, these studies show that geometry is the most useful when the main goal is a clear explanation. At the same time, this family is still closely related to measured serology and corrected evolutionary positioning. It also does not directly simulate why some HI observations are available while others are not. For this reason, its range in positive prediction is more limited than that of sequence-based methods.

#### Matrix based methods

The matrix-based method shifts attention from the geometric distance to the incomplete interaction table. Adabor et al. \cite{adabor2018bayesian} address this problem through Bayesian decomposition, separating antigenic signal from non antigenic assay effects such as virus avidity and antibody related variation. This makes the resulting antigenic estimates more useful for interpretation across different experimental settings. Einav and Cleary \cite{einav2022extrapolating} use a different strategy and show that antibody virus measurement matrices often have low enough effective rank to support accurate completion of many unmeasured entries, even across studies with partial overlap. Their work also supports more efficient experiment planning through sample error curves that help guide measurement priorities. In this family, the main strength is not prediction for fully new strains. Instead, it is better calibration, denoising, and more efficient use of sparse data. Its main limit is that reconstruction usually works on the observed table as it is, rather than modeling surveillance selection or censoring directly.

#### Sequence based methods

The sequence-based method reduces the dependence on current serology by learning the antigen relationship from the sequence-derived characteristics. This provides them with the clearest forward-looking prediction path. Early studies such as IAV CNN \cite{yin2021iav} show that this method can be classified to predict whether the strain pair has crossed the antigen threshold, rather than directly returning to the quantitative titre. Later research is closer to the actual use of settings. Shah et al. \cite{shah2024seasonal}, for example, use only early season information to train the season-by-season model, and combine HA1 sequence differences with metadata such as fanaticism, antiserum efficacy and channel history. This design brings the assessment closer to the WHO-style monitoring schedule. VaxSeer \cite{shi2025influenza} goes further, combining the antigenic predictor with the future dominant model to rank the candidate vaccines according to the coverage score. In retrospective analysis, this score is closely related to the effectiveness of the vaccine, which usually gives a better candidate ranking than past choices. The main advantage of this family is to develop forward. Its main limitation is its reliance on biased past training data, and its interpretability is weaker than map-based methods.

### Move 3 Research Gaps

The comparison of cross-method families shows that no single method can meet the comprehensive needs of influenza monitoring. The core gap is the lack of methods that can handle sparse and heterogeneous HI data while maintaining reliability in the prospective prediction of emerging strains. The two supporting tensions make this point sharper. First of all, the geometry-based method provides a clear description of the antigen structure, but in addition to the directly measured serology, there is only limited extrapolation, while the sequence-based method is more naturally generalized to invisible variants, but provides weaker geometric explanatory. Secondly, the evaluation agreement is still inconsistent. Many research reports say that under random or partial retrospective splitting, the prediction is accurate, but under the time transfer and change between laboratories, the test robustness is less, which is the core of deployment.

### Move 4 Conclusion

The three method families are complementary, not competing with each other. Geometry provides an interpretable structure based on serological evidence. Matrix reconstruction provides unbiassed and intensive supervision, thus improving the calibration of heterogeneous research. The sequence model extends the forecast to the future and supports decision-making-centered evaluation. At present, no single family solves the problems of calibration and forward-looking promotion under explainable and biased sampling at the same time. A plausible next step is to combine these strengths more explicitly. Sequence models can support forward generalization. Geometry can support communication and interpretation. Assay aware reconstruction can support calibration under sparse heterogeneous measurement.

---



## Declaration of Generative AI and AI assisted technologies in the writing process

During the preparation of this work the author used Gemini and ChatGPT in order to assist in improving grammar, clarity, and academic tone of the manuscript. After using these tools, the author reviewed and edited the content as needed and took full responsibility for the content of the work.

The specific tasks are as follows:


1. Correct colloquial expressions and incorrect vocabulary, using more academic language.

2. Correct basic grammatical errors, spelling mistakes, and improper punctuation.

3. Enhance the connections and logic between sentences, avoid redundancy, and improve the fluency of the text.

4. Adjust some overly subjective expressions to a more objective and neutral academic tone.

5. Check the accuracy of reference citations in the manuscript, and ensure that the order of references in the appendix corresponds to the order of citations in the original text.

---

## References

[1] Emmanuel S Adabor and Wilfred Ndifon. Bayesian inference of antigenic and non-antigenic variables from haemagglutination inhibition assays for influenza surveillance. Royal Society Open Science, 5(7):180113, 2018.

[2] Trevor Bedford, Marc A Suchard, Philippe Lemey, Gytis Dudas, Victoria Gregory, Alan J Hay, John W McCauley, Colin A Russell, Derek J Smith, and Andrew Rambaut. Integrating influenza antigenic dynamics with molecular evolution. eLife, 3:e01914, 2014.

[3] Tal Einav and Brian Cleary. Extrapolating missing antibody-virus measurements across serological studies. Cell Systems, 13(7):561-573, 2022.

[4] Judith M Fonville, S H Wilks, Sarah L James, A Fox, M Ventresca, M Aban, L Xue, T C Jones, N M H Le, Q T Pham, et al. Antibody landscapes after influenza virus infection or vaccination. Science, 346(6212):996-1000, 2014.

[5] Bjorn F Koel, David F Burke, Theo M Bestebroer, Stefan Van Der Vliet, Gerben C M Zondag, Gaby Vervaet, Eugene Skepner, Nicola S Lewis, Monique I J Spronken, Colin A Russell, et al. Substitutions near the receptor binding site determine major antigenic change during influenza virus evolution. Science, 342(6161):976-979, 2013.

[6] Xingyi Li, Yanyan Li, Xuequn Shang, and Huihui Kong. A sequence-based machine learning model for predicting antigenic distance for H3N2 influenza virus. Frontiers in Microbiology, 15:1345794, 2024.

[7] Richard A Neher, Trevor Bedford, Rodney S Daniels, Colin A Russell, and Boris I Shraiman. Prediction, dynamics, and visualization of antigenic phenotypes of seasonal influenza viruses. Proceedings of the National Academy of Sciences, 113(12):E1701-E1709, 2016.

[8] Velislava N Petrova and Colin A Russell. The evolution of seasonal influenza viruses. Nature Reviews Microbiology, 16(1):47-60, 2018.

[9] Sheetal Sawant, Sarah Anne Gurley, R Glenn Overman, Angelina Sharak, Sarah V Mudrak, Thomas Oguin III, Gregory D Sempowski, Marcella Sarzotti-Kelsoe, Emmanuel B Walter, Hang Xie, et al. H3N2 influenza hemagglutination inhibition method qualification with data driven statistical methods for human clinical trials. Frontiers in Immunology, 14:1155880, 2023.

[10] Syed Awais W Shah, Daniel P Palomar, Ian Barr, Leo L M Poon, Ahmed Abdul Quadeer, and Matthew R McKay. Seasonal antigenic prediction of influenza A H3N2 using machine learning. Nature Communications, 15(1):3833, 2024.

[11] Wenxian Shi, Jeremy Wohlwend, Menghua Wu, and Regina Barzilay. Influenza vaccine strain selection with an AI-based evolutionary and antigenicity model. Nature Medicine, pages 1-9, 2025.

[12] Derek J Smith, Alan S Lapedes, Jan C De Jong, Theo M Bestebroer, Guus F Rimmelzwaan, Albert D M E Osterhaus, and Ron A M Fouchier. Mapping the antigenic and genetic evolution of influenza virus. Science, 305(5682):371-376, 2004.

[13] Rui Yin, Nyi Nyi Thwin, Pei Zhuang, Zhuoyi Lin, and Chee Keong Kwoh. IAV-CNN: A 2D convolutional neural network model to predict antigenic variants of influenza A virus. IEEE/ACM Transactions on Computational Biology and Bioinformatics, 19(6):3497-3506, 2021.

---





