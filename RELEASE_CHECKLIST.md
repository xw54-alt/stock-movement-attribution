# Release Checklist

Use this checklist against the exact files being published. This checklist is optional repository documentation and does not replace a review of the data itself.

## Files and counts

- [ ] Include the intended JSON records under `data/`.
- [ ] Confirm the record IDs and file names are complete and unique.
- [ ] Confirm each `pair_id` matches its file name.
- [ ] Recompute all published counts from the final records and reconcile them with the paper.
- [ ] Confirm no unapproved source material or fields are included.

## Record consistency

- [ ] Preserve the field order documented in `DATA_DICTIONARY.md`.
- [ ] Check required fields, data types, allowed values, and score scales.
- [ ] Confirm every effect date follows its cause dates and meets the permitted time interval.
- [ ] Confirm cause and effect source references are distinct and URLs are canonical.
- [ ] Confirm multi-cause records have exactly one primary cause.
- [ ] Check that stock-change values, directions, and impact-strength scores agree.
- [ ] Confirm descriptions and framework annotations refer to the same entities and events.
- [ ] Remove drafting artifacts and verify source references.

## Rights and publication

- [ ] Exclude copied full-text news articles and the GDELT distractor corpus unless separately cleared for release.
- [ ] Confirm record descriptions are original annotations and do not reproduce source articles.
- [ ] Keep third-party source metadata distinct from the material licensed under `LICENSE`.
- [ ] Confirm the license applies only to material the authors can license.
- [ ] Confirm the repository URL and paper citation in `README.md`, `CITATION.cff`, and `CITATION.bib` are current.
- [ ] Check the public repository while signed out to ensure the files can be viewed and downloaded.
- [ ] Create a versioned release and record checksums for the final data files.
