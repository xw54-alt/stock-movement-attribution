# Dataset Card

## Name

Financial Causal-News Dataset for Stock-Movement Attribution

## Purpose

The dataset supports research on retrieving and analyzing news evidence associated with observed stock-price movements. Each record links one or more reported cause events to an effect and includes annotations describing the proposed mechanism and supporting evidence.

## Unit of data

Each JSON file contains one cause–effect pair record. The record identifier is stored in the `pair_id` field and corresponds to the file name.

## Coverage

The paper reports 500 queries/pairs, 136 companies, 9 major sectors, 578 benchmark-positive article records, and a 2020–2025 time span. Verify these statistics against the files in the release.

## Construction and annotation

Annotators identify candidate drivers in analyst reports and financial commentary, align them with dated source articles, and record effect-side outcomes. Scoring and categorical fields follow the definitions in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).

## Contents and exclusions

Records contain structured annotations, event descriptions, dates, entity and sector labels, source metadata, stock-movement fields, reasoning-chain steps, rationales, counterfactual analyses, confounders, confidence scores, and business-model mappings.

The release does not include full-text news articles or research code. Source metadata and links identify third-party material but do not grant rights to that material.

## Intended uses

- Research on evidence retrieval, financial news, and retrospective event attribution.
- Analysis of annotation structure, temporal ordering, and alternative explanations.
- Educational and non-commercial research consistent with the license.

## Limitations

- The annotations record retrospective attribution and do not establish verified structural causality.
- Coverage favors events with substantial reporting and retrospective commentary; less-covered events may be underrepresented.
- Publisher and analyst coverage can reflect selection and framing biases.
- Source articles may change, become unavailable, or require subscriptions.
- The scores are annotator judgments, not calibrated probabilities or forecasts.
- The dataset is not investment advice and should not be used alone to make trading decisions.

## License

The authors' original annotations are intended for non-commercial reuse with attribution under CC BY-NC 4.0. Third-party source content remains subject to its own rights and terms.
