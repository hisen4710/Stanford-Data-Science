# PEDB Annotation Specification

## Dataset Target
- Prompts: `20`
- Explanations: `60`
  - Human: `20`
  - AI: `40` (two model responses per prompt)

## Required Row Schema
Each explanation is one row with the following required fields:

`explanation_id, prompt_id, topic, source_type, explanation_text, move_problem_framing, move_principle_invocation, move_causal_link, move_math_to_concept, move_units_magnitude_interpretation, move_assumption_condition_marking, move_misconception_repair, move_analogy_intuitive_bridge, move_stepwise_reasoning, move_answer_closure, correctness, clarity, completeness, accessibility, fluency_risk, notes`

## Field Definitions and Constraints
- `explanation_id`: unique string identifier following the ID conventions below, no duplicates.
- `prompt_id`: prompt identifier (`P01` to `P20`).
- `topic`: one of `mechanics`, `em`, `energy_work`, `thermo_waves`.
- `source_type`: one of `human`, `ai`.
- `explanation_text`: raw explanation text, plain UTF-8, no markdown formatting required.
- `move_*`: binary integer (`0` or `1`) following `docs/codebook.md`.
- `correctness`: integer `1`-`5`.
- `clarity`: integer `1`-`5`.
- `completeness`: integer `1`-`5`.
- `accessibility`: integer `1`-`5`.
- `fluency_risk`: integer `1`-`5`.
- `notes`: free text; use `REVIEW:` prefix when uncertain.

## ID Conventions
- Prompt IDs: `P01` ... `P20`
- Explanation IDs:
  - Human: `H_P##_01`
  - AI model A: `A_P##_01`
  - AI model B: `B_P##_01`

Example:
- `H_P03_01` = human explanation for prompt 3
- `A_P03_01` = AI model A explanation for prompt 3
- `B_P03_01` = AI model B explanation for prompt 3

## File Contracts

### 1) Master annotations file
`data/annotations/pedb_annotations_master.csv`

### 2) Overlap subset file (for agreement)
`data/annotations/pedb_annotations_overlap.csv`

### 3) Prompt sheet (owned by collaborator)
`data/templates/pedb_prompts.csv`

### 4) Source provenance log
`data/templates/pedb_sources.csv`

## CSV Header (Canonical)
```csv
explanation_id,prompt_id,topic,source_type,explanation_text,move_problem_framing,move_principle_invocation,move_causal_link,move_math_to_concept,move_units_magnitude_interpretation,move_assumption_condition_marking,move_misconception_repair,move_analogy_intuitive_bridge,move_stepwise_reasoning,move_answer_closure,correctness,clarity,completeness,accessibility,fluency_risk,notes
```

## Example Row
```csv
A_P07_01,P07,em,ai,"Increasing resistance lowers current because charge flow faces more opposition; by Ohm's law, if voltage stays fixed, current must decrease.",1,1,1,1,0,1,0,0,1,1,4,4,3,4,3,""
```

## Annotation Procedure
1. Run pilot on first `12` explanations.
2. Resolve label collisions and freeze codebook v1.0.
3. Annotate remaining `48` explanations in three batches (`16/16/16`).
4. Mark any uncertain decisions in `notes` with `REVIEW:` plus a short reason.
5. Revisit only `REVIEW` rows in second pass.

## Quality Gates
- **Schema gate:** all required columns present and typed correctly.
- **Range gate:** all `move_*` in `{0,1}` and all ratings in `1..5`.
- **Completeness gate:** no blank required fields.
- **Consistency gate:** prompt-level counts must equal 3 rows per prompt (1 human + 2 AI).

## Inter-Annotator Agreement Protocol
- Select overlap subset: `12-15` explanations.
- Annotators work independently.
- Compute Cohen's kappa for core labels:
  - `move_principle_invocation`
  - `move_causal_link`
  - `move_math_to_concept`
  - `move_assumption_condition_marking`
  - `move_misconception_repair`
- Acceptance target: `kappa >= 0.67`.
- If below threshold, document confusion class and apply one guideline patch only.

## Handoff to Collaborator (Quant Claims Needed)
Provide these three outputs from analysis scripts:
1. Human vs AI discourse-move prevalence (all 10 moves).
2. Correlation matrix: discourse moves vs `clarity` and `completeness`.
3. Top failure-gap table: moves with largest AI deficit vs human.
