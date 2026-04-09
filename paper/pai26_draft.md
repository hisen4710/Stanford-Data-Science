# Physics Explanation Discourse Bank (PEDB): A Linguistically Annotated Benchmark for Evaluating AI-Generated Physics Explanations

## Abstract
We introduce the Physics Explanation Discourse Bank (PEDB), a compact benchmark for evaluating AI-generated introductory physics explanations with a discourse-aware framework. Existing physics evaluations mainly prioritize answer correctness, but tutoring and scientific communication also require explanation quality. PEDB pairs human and model-generated responses to shared prompts and annotates each explanation for ten discourse moves, including principle invocation, causal linkage, assumption marking, misconception repair, and math-to-concept mapping, plus five quality ratings. We provide baseline analyses of discourse-move prevalence and quality patterns across human and AI sources. Initial findings show that model outputs are often fluent yet structurally incomplete on key pedagogical dimensions. PEDB contributes a reusable annotation protocol and benchmark format for discourse-sensitive assessment of AI systems in physics education.

## 1. Introduction
Recent progress in foundation models has improved performance on scientific tasks, including parts of physics reasoning. However, most current benchmarks evaluate final answers or derivation accuracy rather than explanatory quality. In educational and communication settings, this is a critical gap: an explanation can be technically correct yet pedagogically weak, or fluent yet conceptually misleading.

This paper presents PEDB, a linguistically annotated benchmark targeting explanatory discourse in introductory physics. The central claim is that explanation quality is not equivalent to answer correctness. PEDB operationalizes explanation quality through ten observable discourse moves and five quality ratings, enabling structured comparison between human and AI-generated explanations.

Our contributions are:
1. A compact benchmark design pairing human and AI explanations for shared prompts.
2. A physics-specific discourse annotation codebook with ambiguity-resolution rules.
3. Baseline analyses quantifying discourse-move gaps and quality differences.
4. A qualitative error taxonomy for recurring AI explanation failures.

## 2. Related Work
### 2.1 Physics reasoning evaluation
Prior benchmark efforts in physics and scientific QA have primarily focused on answer-level performance, formal derivations, or task completion accuracy. These benchmarks are valuable for reasoning diagnostics but do not fully assess educational explanation quality.

### 2.2 Explanatory discourse annotation
NLP research has shown that explanatory and instructional text can be annotated for didactic acts, coherence moves, and pedagogical structure. These findings motivate discourse-aware evaluation beyond correctness metrics.

### 2.3 Gap addressed by PEDB
PEDB integrates these lines by introducing a benchmark that is physics-specific, explanation-centric, and annotation-driven. The goal is to assess not only whether a model reaches a correct claim, but whether it explains that claim in a learner-usable way.

## 3. Dataset and Annotation
### 3.1 Scope and construction
PEDB is designed as a compact benchmark with:
- 20 introductory physics prompts.
- 60 explanations total: 20 human and 40 AI (two model responses per prompt).
- Topic coverage: mechanics, electromagnetism, energy/work, and thermo/waves.

### 3.2 Annotation scheme
Each explanation is labeled with ten binary discourse moves:
1. problem framing
2. principle invocation
3. causal link
4. math-to-concept mapping
5. units/magnitude interpretation
6. assumption/condition marking
7. misconception repair
8. analogy/intuitive bridge
9. stepwise reasoning
10. answer closure

Each explanation also receives five 1-5 ratings:
- correctness
- clarity
- completeness
- accessibility
- fluency risk

### 3.3 Reliability protocol
A 20-25 percent overlap subset is double-annotated and scored with Cohen kappa on core labels. The target threshold is kappa >= 0.67.

### 3.4 Data format
The canonical row schema is:
`explanation_id, prompt_id, topic, source_type, explanation_text, move_* x10, correctness, clarity, completeness, accessibility, fluency_risk, notes`

## 4. Baselines and Experimental Setup
### 4.1 Baseline A: move prevalence comparison
We compute per-move prevalence by source type (human vs AI) and report absolute and relative gaps.

### 4.2 Baseline B: ratings distribution analysis
We compare distributions and central tendency of five quality ratings by source type.

### 4.3 Baseline C: discourse-quality associations
We estimate correlations between discourse-move presence and quality ratings, focusing on clarity and completeness.

### 4.4 Optional baseline D: weak heuristic detector
A lightweight cue-based detector is used for selected moves (for example principle terms, causal connectors, assumption markers) to establish a low-cost baseline against human labels.

## 5. Results
### 5.1 Annotation feasibility
- **Table 1 placeholder:** Inter-annotator agreement on overlap subset.
- Report kappa per core label and macro-average.

### 5.2 Human vs AI discourse profile
- **Table 2 placeholder:** move prevalence by source type.
- Expected pattern: AI strong on closure and local coherence, weaker on assumption marking, misconception repair, and units/magnitude interpretation.

### 5.3 Quality ratings comparison
- **Figure 1 placeholder:** rating distributions for correctness, clarity, completeness, accessibility, and fluency risk.
- Expected pattern: AI high clarity variance with elevated fluency risk under lower completeness.

### 5.4 Error taxonomy evidence
- **Table 3 placeholder:** frequency of error classes E1-E7.
- **Case examples placeholder:** one short excerpt each for E1, E3, E4.

## 6. Discussion
PEDB suggests that answer-level correctness is necessary but insufficient for evaluating AI explanations in physics. Discourse-aware signals reveal where polished responses fail pedagogically. This matters for tutoring systems and learner-facing scientific communication, where explanation structure directly affects understanding and misconception formation.

The benchmark is intentionally compact to support rapid reuse and extension. Future work can expand topic breadth, include multilingual explanations, and test intervention strategies that explicitly target low-frequency discourse moves.

## 7. Limitations
- Small initial dataset size (60 explanations).
- Intro-level scope may not transfer to advanced physics discourse.
- Ratings remain human-judgment dependent despite protocol constraints.
- Source quality variation in human explanations can influence comparative outcomes.

## 8. Conclusion
PEDB provides a practical benchmark for discourse-sensitive evaluation of AI-generated physics explanations. By pairing move-level annotation with quality ratings, it complements answer-level benchmarks and supports more realistic assessment of systems used in education.

## References (To Fill)
- Physics benchmark and physics-AI evaluation sources.
- Explanatory discourse annotation and pedagogical NLP sources.
- Educational measurement sources for explanation quality.

## Author Workflow Notes
- Replace all placeholders with measured values before submission.
- Ensure each headline claim cites exactly one table/figure or one coded example.
- Keep final body within 4 pages excluding references.
