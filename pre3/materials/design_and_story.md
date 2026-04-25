# Design and Story — 3MT Slide and Non-Specialist Explanation

This document explains (a) how the one-page slide was designed and (b) how I will explain the research story to a non-specialist audience. It is intended to document my design and storytelling choices. It is **not** a script to read aloud.

---

## (a) Slide design

### Format and readability

* **Format:** The slide is provided as a one-page HTML file (`3mt_slide_no_overflow.html`). A text-based and machine-readable, as required by the assignment.
* **Layout:** The slide uses a single 16:9 view with a left-to-right research flow: **research context → three connected studies → overall message**.
* **Readability:** I reduced the amount of text on the slide so that it can support a three-minute talk without becoming a written report. The slide uses short labels, manually broken lines, and large visual blocks.
* **Colour and contrast:** The slide uses a restrained academic colour palette: dark blue for the overall thesis message, teal for structural attention, and warm gold for physical modelling. The colours separate the three studies while keeping the slide visually consistent.

### Content on the slide

The slide is built around one simple starting point:

> **A graph = nodes + edges.**

This sentence makes the research accessible to a non-specialist audience. The left panel introduces biomedical examples of graphs, such as molecules, proteins, and disease networks. It also states the core challenge: **prediction alone is not enough** in scientific and biomedical settings.

The centre and right parts of the slide present the three studies as one connected research progression rather than as three unrelated projects:

1. **Local evidence — Local motifs**
   The first study asks what small graph pattern supports a prediction. It focuses on decodable local motifs, so the model can provide human-readable evidence.

2. **Global dependency — Structural attention**
   The second study moves beyond local neighbourhoods and asks how distant parts of a graph should be compared. It uses structural similarity to make graph attention more transparent.

3. **Physical law — Long-range physics**
   The third study focuses on molecular systems, where important interactions may occur over long distances. It adds physical priors so the model is not only data-driven but also scientifically grounded.

The slide therefore shows the thesis logic as:

> **Local evidence → Global dependency → Physical law**

The bottom takeaway summarises the full story: trustworthy biomedical graph AI should combine these three levels of structure.

### Design choices

* **One clear research story:** The slide does not try to show all technical details or all experimental results. Instead, it communicates the central argument of the research.
* **Progression across studies:** The three studies are arranged as a conceptual progression from local patterns to global relations to physical constraints.
* **Minimal technical jargon:** Terms such as graph kernels, equivariance, and reciprocal-space modelling are not foregrounded on the slide. They can be briefly explained orally if needed.
* **Visual support rather than script:** The slide is designed to guide the spoken explanation. It gives the audience anchor points but does not contain a full script.

---

## (b) Explaining the research story to a non-specialist audience

### Core message in plain language

My research is about making graph-based AI more trustworthy for biomedicine. Many biomedical problems can be represented as graphs: atoms connected by chemical bonds, proteins connected by spatial contacts, or genes connected by biological interactions.

A model that only gives a prediction is not enough for scientific use. Scientists also need to know what structural evidence the model used, whether the model can reason beyond nearby connections, and whether it respects important physical rules.

The core message is:

> **Graph AI should not only make predictions; it should make its reasoning easier to inspect.**

### Storytelling structure for the audio presentation

I will use a simple three-part structure.

1. **Start with the problem**
   I will explain that biomedical data are often connected systems. In these systems, the relationships between entities are as important as the entities themselves. This is why graphs are useful.

2. **Explain why prediction alone is insufficient**
   I will give an everyday explanation: if an AI model predicts that a molecule may be useful or that a biological network indicates risk, researchers still need to ask, “Why did the model say that?” In science, a useful model should provide evidence, not just an answer.

3. **Present the three studies as one research path**
   I will explain the three studies in order:

   * First, I look at **local evidence**: what small graph pattern matters?
   * Second, I look at **global dependency**: how are distant parts of the graph related?
   * Third, I look at **physical law**: what molecular interactions must the model respect?

This helps the audience understand that the thesis is not a collection of separate methods. It is one research direction: building structure directly into graph AI.

### Strategies used for a non-specialist audience

1. **Simple definition first**
   I begin with “a graph = nodes + edges” before introducing any method. This avoids assuming that the audience already knows graph learning.

2. **Concrete biomedical examples**
   I use molecules, proteins, and disease networks as examples, because they are easier to imagine than abstract graph datasets.

3. **Plain-language replacements**
   I will replace technical terms with simpler explanations when speaking:

   * “local motif” → “a small meaningful pattern in the graph”
   * “attention” → “which parts of the graph the model compares”
   * “long-range interaction” → “an effect between parts that are far apart”
   * “physical prior” → “a scientific rule built into the model”

4. **A single repeated question**
   I will keep returning to the question: **Can we see why the model made this prediction?** This keeps the talk coherent.

5. **Avoiding unnecessary technical detail**
   I will not explain equations, benchmark tables, or implementation details in the 3MT audio. The goal is to communicate the research motivation and significance clearly.

### What this document is not

This document is not a script for the audio presentation. During the recording, I will use only short note-card prompts and speak from understanding, in line with the assessment rule that reading from a script is not permitted.

Possible note-card prompts:

* graph = nodes + edges
* biomedical examples: molecule, protein, disease network
* prediction alone is not enough
* local evidence → global dependency → physical law
* make graph AI easier to inspect
* trustworthy biomedical AI

---

## File list in this submission

| Item                       | File(s)                                                   |
| -------------------------- | --------------------------------------------------------- |
| One-page slide             | `3mt_slide_no_overflow.html`, `3mt_slide_no_overflow.svg` |
| Design & story description | `design_and_story.md`                                     |
| Audio link                 | `audio_link.md` or uploaded audio file                    |

After recording the audio presentation, I will add the audio file or audio link and submit the required links to the forum post.
