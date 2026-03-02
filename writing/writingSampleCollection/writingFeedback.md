# Writing Feedback — YIN Yujia (殷宇佳)

## Feedback on YIN Yujia's First Draft: Introduction and Literature Review

**Student:** YIN Yujia (殷宇佳)
**Topic:** Machine Learning Methods for Hemagglutination Inhibition Titer Prediction in Influenza Surveillance
**Date:** 2 March 2026
**Reviewer:** Simon Wang (with AI-assisted analysis)

**Your draft:** writing/writingSampleCollection/firstDraft.md
**Your reflection:** writing/writingSampleCollection/firstDraft.md (reflection section)
**Assessment rubric:** writing/assessment/writing_instructions_formatted.md

---

## Overall Assessment

This is one of the strongest drafts in the class. Your Introduction follows the three-move structure clearly, your Literature Review is well-organized with a taxonomy of methods (matrix completion, Bayesian, kernel-based, deep learning, sequence-based), and — critically — you include extensive citations throughout. The writing demonstrates genuine domain expertise and a thoughtful approach to structuring the survey. The main areas for improvement are: (1) the Literature Review is very long and could benefit from tighter synthesis rather than method-by-method description; (2) Move 2 (Identifying the Niche) could be more decisive in framing the gap; and (3) some sections read as catalog-style summaries rather than critical analyses. Your self-reflection shows strong metacognitive awareness — you already identify most of these issues yourself.

**Estimated current level:** Good to Excellent (8–9 range) — The structure, citation density, and domain knowledge are strong. Tightening the critical analysis and improving synthesis will push this to Excellent.

---

## Part 1: Introduction Feedback

### What Works Well

- **Move 1 is exemplary.** You establish the territory clearly: HI assays → vaccine strain selection → increasing viral diversity → need for computational models. Each claim is backed by citations (Smith et al. 2004, Koel et al. 2013, Fonville et al. 2014, etc.)
- **The practical motivation is compelling.** You explain why raw titers are unreliable (laboratory variation, dilution range limits, selective measurement) — this grounds the research in real-world challenges
- **Move 2 effectively introduces the niche.** You frame the gap as the diversity and disconnectedness of existing ML approaches for HI prediction
- **Move 3 clearly states the research purpose.** You explicitly state what the survey covers and how it contributes

### Issue 1: Move 2 Could Be More Decisive

Your Move 2 identifies the problem (diverse approaches, no unified understanding) but frames it somewhat passively: "Recent advances in machine learning have led to a diverse set of approaches..."

**Stronger framing:** "Despite a growing body of work on computational HI titer prediction, the field lacks a systematic comparison of these methods' assumptions, data requirements, and predictive accuracy across different surveillance contexts. Existing reviews [cite any if available] focus on individual method families without examining how different modeling assumptions — matrix completion vs. Bayesian vs. sequence-based — affect prediction reliability under realistic data conditions."

This version is more assertive about what's missing and why it matters.

### Issue 2: Consider Adding a Sentence About Practical Impact

Your Introduction effectively motivates the computational challenge but could more explicitly state the public health impact of improved prediction.

**Suggestion:** Add one sentence in Move 1 connecting better HI prediction to practical outcomes: "More accurate computational HI models could reduce the number of required laboratory experiments by X%, accelerating vaccine strain recommendations and reducing the time between emerging antigenic variants and public health response [citation]."

---

## Part 2: Literature Review Feedback

### What Works Well

- **The taxonomy is well-designed.** Organizing methods by approach type (matrix completion → Bayesian → kernel → deep learning → sequence-based) gives readers a clear conceptual map
- **Citation density is excellent.** Nearly every claim is supported by references
- **You show genuine understanding** of the mathematical foundations (low-rank matrix factorization, Gaussian processes, RKHS, etc.)
- **Move 3 (Research Gaps) identifies five specific gaps** — this is thorough and well-structured
- **Move 4 provides a clear conclusion** with forward-looking implications

### Issue 3: Method-by-Method Description vs. Synthesis

Your Literature Review tends to describe each method individually rather than synthesizing across methods within a category. For example, in the matrix completion section, you describe Cai et al., then Harvey et al., then Steinbrück et al. — each in sequence.

**Stronger synthesis pattern:** Instead of describing each paper independently, compare them: "Early matrix completion approaches assumed globally low-rank structure [Cai et al.], but subsequent work revealed that antigenic data often exhibits locally varying patterns that violate this assumption [Harvey et al.]. Steinbrück et al. addressed this by incorporating strain-specific substitution features, achieving improved coverage but at the cost of requiring sequence alignment data not always available in surveillance databases."

This pattern shows connections and tensions between papers, which is what distinguishes a literature review from an annotated bibliography.

### Issue 4: Critical Evaluation Is Uneven

Some methods receive thoughtful critique (e.g., you note limitations of tree-based models for antigenic cartography) while others are described without evaluation. Ensure every method or approach you discuss includes:
1. What it achieves (with specific results if available)
2. What assumptions it makes
3. What limitations it has
4. How it compares to alternatives

### Issue 5: Length Management

Your draft is substantially longer than the 1000–1500 word target. The comprehensive coverage is admirable, but for the assignment, you will need to select the most important themes and go deeper on those rather than covering everything.

**Suggestion:** Focus on 2–3 method families that are most relevant to your research and analyze them in depth, with briefer mentions of the others for context.

### Issue 6: Move 3 Gaps Are Strong but Need Prioritization

You identify five research gaps — this is thorough but may be too many for a single paper to address. Consider ranking them by importance and explicitly stating which gap(s) your work addresses.

---

## Part 3: Language and Process Feedback

### Issue 7: Writing Quality Is Generally Strong

Your language is clear, precise, and appropriately academic. A few minor suggestions:
- Some sentences are very long and could be split for clarity
- The mathematical notation (e.g., RKHS, kernel matrices) is well-handled but ensure non-specialist readers can follow

### Issue 8: Your Self-Reflection Is Excellent

Your reflection shows strong metacognitive awareness: "I should also revise at the argument level, asking whether each section strengthens the central positioning of the survey." This is exactly the right approach. Apply this principle systematically to each paragraph.

---

## Summary of Priority Actions

| Priority | Action | Impact |
|----------|--------|--------|
| 🟡 Medium | Strengthen Move 2 with more decisive gap language | Sharpens research motivation |
| 🟡 Medium | Add synthesis paragraphs that compare methods within categories | Elevates from description to analysis |
| 🟡 Medium | Ensure every method discussed includes a critical evaluation | Balances coverage with critique |
| 🟡 Medium | Trim to 1000–1500 words by focusing on 2–3 key method families | Meets assignment requirements |
| 🟢 Lower | Prioritize your 5 gaps — which does your research address? | Focuses your contribution |
| 🟢 Lower | Add practical impact sentence in Move 1 | Strengthens motivation |

---

## Next Steps

1. Read the [full writing instructions](https://github.com/tesolchina/mccpSpring2026/blob/main/writing/assessment/writing_instructions_formatted.md) carefully
2. Select 2–3 key method families and deepen the critical analysis
3. Add cross-method synthesis paragraphs
4. Trim to 1000–1500 words
5. Submit by **15 March 2026** via Moodle forum and Turnitin
