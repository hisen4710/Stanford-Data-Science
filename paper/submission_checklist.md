# PEDB PAI26 Submission Checklist

## Track + Policy
- [ ] Confirm track: **Datasets and Benchmarks**.
- [ ] Confirm blind policy for selected track on OpenReview.
- [ ] Ensure author list is final before submission.

## Format (NeurIPS Style)
- [ ] Use official NeurIPS format.
- [ ] Main paper body is **4 pages max** (references excluded).
- [ ] No appendix included in submission.
- [ ] Figures/tables readable at final PDF scale.

## Content Lock
- [x] Final taxonomy locked to 5 labels.
- [x] Final reliability numbers locked (0.5045 -> 0.6706).
- [x] Final key findings locked (INTUITION gap, completeness gap).
- [x] References section populated in draft.
- [x] All headline claims mapped to quantitative evidence.

## Files To Export
- [ ] Camera-ready PDF from final manuscript.
- [ ] Source manuscript file (LaTeX/Overleaf project or markdown archive).
- [ ] Final tables:
  - `outputs/table_move_prevalence_final.csv`
  - `outputs/table_ratings_summary_final.csv`
  - `outputs/table_move_rating_correlations_final.csv`
- [ ] Final analysis note:
  - `outputs/analysis_summary_step6_final.md`

## Final QA Before Upload
- [x] Numbers in manuscript match `*_final.csv` outputs.
- [x] Terminology consistency (`PRINCIPLE_DERIVE` everywhere in final analyses).
- [x] No overclaims (correlations framed as exploratory).
- [x] Non-expert readability pass completed.

## OpenReview Upload
- [ ] Upload PDF.
- [ ] Fill metadata (title, abstract, authors, track).
- [ ] Verify supplementary/data links are correct.
- [ ] Submit before deadline.
