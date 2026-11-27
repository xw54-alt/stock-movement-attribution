# Financial Causal-News Dataset

This repository contains structured annotations linking reported cause events to stock-movement effects. The records are intended for research on retrieving news evidence associated with observed stock-price movements.

## Repository contents

```text
.
├── CITATION.bib
├── CITATION.cff
├── DATASET_CARD.md
├── DATA_DICTIONARY.md
├── LICENSE
├── README.md
├── RELEASE_CHECKLIST.md
└── data/  (one JSON file per record)
```

Each JSON file contains one pair record. The field definitions and data conventions are in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).

## Dataset scope

The paper reports 500 queries/pairs, 136 companies, 9 major sectors, 578 benchmark-positive article records, and coverage from 2020 through 2025. Please verify these totals against the released files. The dataset includes structured annotations and source metadata; it does not include full-text news articles.

The records describe retrospective evidence attribution. They do not establish structural causality and are not investment advice. See [`DATASET_CARD.md`](DATASET_CARD.md) for the dataset's purpose and limitations.

## License

The authors' original annotation contributions are released under CC BY-NC 4.0. The license does not grant rights to third-party articles or publisher content. See [`LICENSE`](LICENSE) for the scope and license links.

## Citation

Please cite the associated paper as the primary scholarly reference when using this dataset, and identify the dataset repository and release you used. [`CITATION.cff`](CITATION.cff) sets the paper as the preferred citation; [`CITATION.bib`](CITATION.bib) contains the paper entry. The OpenReview record is used until the final ACL Anthology citation is available.

## Data conventions

- Use each record's `date` field for the event chronology; `source_info.published_date` records when the source article was published.
- Preserve the JSON field order defined in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).
- Do not redistribute source article text under this dataset license.
