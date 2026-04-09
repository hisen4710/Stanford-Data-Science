# PEDB Project Brief

## Final Title
**Physics Explanation Discourse Bank (PEDB): A Linguistically Annotated Benchmark for Evaluating AI-Generated Physics Explanations**

## One-Sentence Pitch
PEDB is a compact public benchmark that evaluates whether AI-generated introductory physics explanations are not only correct, but also discourse-complete, pedagogically legible, and aligned with how experts explain scientific ideas.

## Core Claim (Frozen)
Physics explanation quality is not equivalent to final-answer correctness; discourse structure contributes independent educational value and must be evaluated explicitly.

## Scope (Frozen)
- 20 intro-physics prompts
- 60 explanations total (20 human, 40 AI)
- 10 discourse-move labels
- 5 quality ratings
- Primary track: Datasets and Benchmarks
- Secondary relevance: Education and Training

## Research Questions
1. Which discourse moves are most predictive of pedagogically strong physics explanations for beginners?
2. How do AI-generated explanations differ from human-written explanations in discourse-move coverage and quality ratings?
3. Can a compact, physics-specific annotation scheme be applied consistently enough to serve as a reusable benchmark?

## Hypotheses
1. AI explanations will match or exceed human explanations on fluency-facing traits (surface coherence, closure) but underperform on explanatory grounding moves (assumption marking, misconception repair, unit interpretation).
2. Discourse moves linked to scientific grounding (principle invocation, causal bridge, math-to-concept mapping) will correlate more strongly with completeness than generic readability cues.
3. A constrained codebook with explicit decision rules will achieve usable reliability on core labels (target Cohen’s kappa >= 0.67 on overlap subset).

## 120-Word Abstract Stub
We introduce the Physics Explanation Discourse Bank (PEDB), a compact benchmark for evaluating AI-generated introductory physics explanations through a linguistically grounded annotation framework. Existing physics benchmarks primarily measure answer correctness, but educational usefulness also depends on explanatory discourse: principle invocation, causal bridging, assumption marking, misconception repair, and math-to-concept mapping. PEDB pairs human and model-generated explanations for shared prompts and annotates each response with discourse-move labels plus quality ratings for correctness, clarity, completeness, accessibility, and misleading fluency risk. We provide baseline analyses comparing human and AI explanations and identify failure patterns where fluent responses omit key scientific reasoning steps. PEDB supports discourse-aware evaluation for physics tutoring systems, scientific communication tools, and future benchmark development in physics-and-AI research and practical deployment decisions.

## Deliverables You Own
- `docs/project-brief.md`
- `docs/codebook.md`
- `docs/annotation-spec.md`
- `docs/error-taxonomy.md`
- `paper/pai26_draft.md`

## Immediate Execution Checklist
1. Freeze codebook v1.0 after pilot on first 12 explanations.
2. Annotate full set in three batches and flag uncertain rows with `notes=REVIEW`.
3. Finalize taxonomy from repeated error patterns.
4. Lock top three quantitative claims and map each to one table/figure.
