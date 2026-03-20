# eeml-nli-compact-vs-bert

Controlled empirical study of a compact encoder-only Transformer versus BERT on SNLI, with emphasis on efficiency, calibration, and diagnostically meaningful failure modes.

## Overview

This repository contains the final materials for a controlled comparison between a compact Transformer encoder trained from scratch and a fine-tuned BERT baseline on the SNLI benchmark.

The study is framed not as a simple leaderboard comparison, but as an investigation of **where compactness remains useful and where semantic quality begins to break down** under efficiency constraints. In addition to aggregate classification quality, the analysis covers:

- model size and measured inference throughput,
- confidence calibration before and after temperature scaling,
- diagnostic slice analysis,
- confusion patterns across NLI classes,
- exploratory architectural ablations,
- multi-seed verification for the compact model.

## Final results

The final experiments show a clear quality-efficiency trade-off:

- **BERT** remains the stronger model in overall predictive quality.
- The **compact Transformer** reaches **0.7914 ± 0.0056 test macro-F1** in a three-seed evaluation.
- Relative to BERT, the compact model is **10.94× smaller** and **18.37× faster** in measured inference throughput.
- The largest degradation is concentrated in diagnostically harder regions of the task, especially the **neutral** class, **low-overlap** pairs, and examples containing **negation**.
- **Temperature scaling** improves confidence calibration for both models.

Taken together, the results suggest that compact encoders remain useful in efficiency-first settings, but their first losses appear in exactly those regions that require finer semantic discrimination and more reliable confidence estimates.

## Repository contents

```text
abstract/    EEML research abstract
report/      Full experimental report
notebooks/   Main notebook used for training and evaluation
results/     Exported metric tables and analysis artifacts
figures/     Final plots used in the report
src/         Optional supporting code
```

## Main artifacts

- **EEML research abstract** in PDF/DOCX
- **Full report** with figures, tables, discussion, and limitations
- **Final notebook** with calibration, diagnostic slices, ablations, and multi-seed analysis
- **Exported results** for metrics, calibration, and slice-based evaluation

## Reproducibility

The experiments were developed in a Kaggle notebook environment using SNLI and the `bert-base-uncased` tokenizer. The repository is intended to provide the final research artifacts and reporting materials rather than large training checkpoints.

## Notes

This repository focuses on final experimental results and interpretable analysis. Heavy model files and raw datasets are intentionally omitted.
