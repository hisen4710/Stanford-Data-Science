# PEDB Annotation Codebook (v1.0)

## Purpose
This codebook defines how to annotate discourse structure in introductory physics explanations for PEDB.

## Annotation Unit
- One full explanation text is one annotation unit.
- Label each discourse move as binary: `1` (present) or `0` (absent).
- Use evidence spans in notes when uncertain.

## General Decision Rules
1. Label what is explicitly present in the text, not what the writer may have intended.
2. A move is `1` only if it contributes explanatory function, not keyword-only mention.
3. Prefer conservative coding when evidence is ambiguous.
4. If two moves overlap, apply both only when each has distinct textual evidence.
5. If no move evidence is found, label `0` and do not infer.

## Discourse Move Labels

### 1) `move_problem_framing`
**Definition:** Restates or reframes the physics situation/question in conceptual terms before reasoning.

**Positive example:**
"Even though the speed stays constant, the direction is changing, so the motion is still changing."

**Boundary case:**
A one-clause restatement that only repeats the prompt wording without conceptual reframing.

**Non-example:**
"The answer is centripetal acceleration." (no framing)

---

### 2) `move_principle_invocation`
**Definition:** Names or clearly invokes a governing law/principle/constraint used to justify reasoning.

**Positive example:**
"By Newton's second law, a net force implies acceleration."

**Boundary case:**
Mentions formula symbolically with no link to the principle's role.

**Non-example:**
"Use this equation." (no principle grounding)

---

### 3) `move_causal_link`
**Definition:** States a mechanistic or causal relation explaining why one physical condition leads to another.

**Positive example:**
"Increasing resistance reduces current because charges face more opposition in the circuit."

**Boundary case:**
Uses causal words ("because," "therefore") but only restates algebraic manipulation.

**Non-example:**
"Current decreases when resistance increases." (descriptive only)

---

### 4) `move_math_to_concept`
**Definition:** Interprets equations/signs/terms in conceptual physics language.

**Positive example:**
"The negative sign means the induced effect opposes the change, not that energy is negative."

**Boundary case:**
Equation is written and variables are named, but no conceptual interpretation is given.

**Non-example:**
"V = IR." only

---

### 5) `move_units_magnitude_interpretation`
**Definition:** Interprets units, scale, order of magnitude, or sign direction in physical terms.

**Positive example:**
"A result in joules tells you energy transferred; microjoules implies the effect is tiny here."

**Boundary case:**
Units are included next to numbers but never interpreted.

**Non-example:**
"5 N" with no explanation of implication

---

### 6) `move_assumption_condition_marking`
**Definition:** States assumptions, idealizations, or validity conditions for the explanation.

**Positive example:**
"This result holds if we neglect air resistance and treat the rope as massless."

**Boundary case:**
Implicit simplification appears but is not explicitly marked as an assumption.

**Non-example:**
Explanation proceeds with idealized setup but never flags assumptions.

---

### 7) `move_misconception_repair`
**Definition:** Explicitly anticipates and corrects a likely beginner misconception.

**Positive example:**
"Constant speed does not mean zero acceleration if direction changes."

**Boundary case:**
States correct fact that incidentally contrasts with misconception but does not explicitly repair it.

**Non-example:**
Correct explanation with no misconception targeting.

---

### 8) `move_analogy_intuitive_bridge`
**Definition:** Uses analogy, metaphor, or intuitive mapping to aid understanding while preserving physics meaning.

**Positive example:**
"Electric potential is like height in a gravitational landscape: larger drops allow more energy release."

**Boundary case:**
Analogy appears but mapping to physics variables is incomplete.

**Non-example:**
Vague metaphor with no explanatory mapping.

---

### 9) `move_stepwise_reasoning`
**Definition:** Organizes explanation as explicit sequential reasoning steps.

**Positive example:**
"First identify forces, then compute net force, then infer acceleration direction."

**Boundary case:**
Text has multiple sentences but no clear inferential progression.

**Non-example:**
Single-shot conclusion with no chain.

---

### 10) `move_answer_closure`
**Definition:** Explicitly ties reasoning back to the original question in a final closing statement.

**Positive example:**
"So the bulb dims because total resistance rises, which lowers current through the circuit."

**Boundary case:**
Final sentence repeats earlier claim but does not connect to prompt goal.

**Non-example:**
Explanation ends abruptly without explicit closure.

## Ambiguity Resolution Rules (Critical)

### A) Causal Link vs Stepwise Reasoning
- `move_causal_link=1` requires a mechanistic why-relationship.
- `move_stepwise_reasoning=1` requires ordered inferential progression.
- A text can have one without the other.
- If sequence exists but no mechanism, set `stepwise=1`, `causal=0`.
- If mechanism is stated in one sentence without sequence, set `causal=1`, `stepwise=0`.

### B) Problem Framing vs Answer Closure
- `move_problem_framing=1` is early setup/reframing before core explanation.
- `move_answer_closure=1` is end-of-response loop closure.
- Same sentence cannot satisfy both unless it contains distinct framing and final tie-back functions.

### C) Principle Invocation vs Math-to-Concept
- Principle invocation marks the governing law.
- Math-to-concept interprets mathematical form/terms physically.
- Formula mention alone is insufficient for either unless function is explicit.

### D) Analogy vs Misconception Repair
- Analogy helps intuitively map concept.
- Misconception repair explicitly corrects wrong intuition.
- If analogy is used to correct a known misconception and correction is explicit, both may be `1`.

## Quality Ratings (1-5 Anchors)

### `correctness`
- **1:** Major scientific errors; conclusion invalid.
- **2:** Partially correct with serious conceptual mistake.
- **3:** Mostly correct but one notable inaccuracy or omission that affects understanding.
- **4:** Correct with minor imprecision that does not change core understanding.
- **5:** Scientifically correct and precise for intro level.

### `clarity`
- **1:** Hard to follow; disorganized or jargon-heavy.
- **2:** Some understandable parts, but structure is confusing.
- **3:** Generally understandable with occasional ambiguity.
- **4:** Clear progression and readable language.
- **5:** Exceptionally clear, coherent, and learner-friendly.

### `completeness`
- **1:** Bare answer; no real explanation.
- **2:** Limited explanation; key reasoning steps missing.
- **3:** Core reasoning present but important steps underdeveloped.
- **4:** Nearly complete explanation with minor gaps.
- **5:** Full reasoning chain with conditions/interpretation where relevant.

### `accessibility`
- **1:** Not suitable for beginners.
- **2:** Too advanced or opaque for first-year audience.
- **3:** Mixed accessibility; partly approachable.
- **4:** Appropriate for first-year students with minimal prior context.
- **5:** Highly accessible while remaining technically accurate.

### `fluency_risk` (misleading fluency risk)
- **1:** Low risk; wording matches reasoning quality.
- **2:** Slight polish-over-substance risk.
- **3:** Moderate risk of sounding stronger than content quality.
- **4:** High risk; fluent language masks notable reasoning gaps.
- **5:** Very high risk; highly polished but substantially misleading/incomplete.

## Annotation Workflow (Owner)
1. Pilot on 12 explanations.
2. Resolve collisions and freeze v1.0 labels.
3. Annotate remaining explanations in three batches.
4. Mark uncertain rows with `notes=REVIEW` and include evidence span.
5. Run second-pass review only on `REVIEW` rows.

## Inter-Annotator Overlap Protocol
- Double-annotate 12-15 items (20-25% overlap).
- Compute Cohen's kappa on core moves:
  - `move_principle_invocation`
  - `move_causal_link`
  - `move_math_to_concept`
  - `move_assumption_condition_marking`
  - `move_misconception_repair`
- Target kappa: `>= 0.67`.
