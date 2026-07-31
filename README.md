# Statistical Audit and DQA Evaluation

**PhD thesis:** *Attribute-Based Approach for Semantic Type Detection and Data Quality Assessment in Diverse Data Sources and Domains*  
**Author:** Marcelo Valentim Silva  
**University:** Curtin University, Perth, Western Australia

This repository contains the research code, retained inputs, generated workbooks, execution records, selected dataset-level outputs, and supporting documentation associated with the Statistical Audit and operational Data Quality Assessment evaluation reported in Chapter 6 of the PhD thesis.

The repository covers two complementary components:

1. the Statistical Audit of large-scale Semantic Type Detection assignments over the Kaggle + VizNet corpus; and
2. the empirical operational evaluation of the HeadersIQ Data Quality Assessment component, including forty retained successful executions, ten detailed dataset cases, identifier-role sensitivity analysis, and evidence from the public HeadersIQ Code Runner.

## Statistical Audit scope

The Statistical Audit begins with Kaggle + VizNet Universe B, containing 118,639 attribute records.

- 102,205 columns received one of the 39 available `FinalFormat` assignments.
- 16,434 columns had no assigned `FinalFormat` and were outside the FinalFormat-assignment audit.
- The FinalFormat-assigned universe was partitioned into 53,763 strict trivial columns and a non-trivial universe of 48,442 columns.
- A finite-population, area-and-abbreviation-stratified probability sample of 2,288 columns was drawn from the non-trivial universe.
- Seven purposively selected rare-format cases were added for diagnostic coverage.
- The complete reviewed set therefore contains 2,295 columns.

The original 2,288-column probability sample supports inferential estimation. The seven additional cases support diagnostic coverage of rare FinalFormats.

## GPT-assisted reviews

### Main 2,295-column Statistical Audit review

The main review protocol was developed through an initial 300-row pilot and then frozen. The complete set of 2,295 reviewed rows, including the original pilot cases, was subsequently processed in batches of a few hundred rows using the same final standardised prompt.

The completed outputs are retained in:

- `dataProducts/GPTOutputsOn2295.xlsx`
- `dataProducts/GPTAnalysisOn2295.xlsx`

### Focused 795-row abbreviation re-audit

A second GPT-assisted review was conducted after the disagreement analysis identified eleven suspicious abbreviation mappings.

The eleven mappings were matched against the full Kaggle + VizNet superset, producing a 795-row targeted slice. All 795 rows were reviewed using the final standardised abbreviation re-audit prompt. The retained outputs include the row-level `GPT_abbrev_decision` fields and the aggregate decision and suggested-interpretation summaries.

The completed outputs are retained in:

- `dataProducts/K_V_superset_suspicious_abbrev.xlsx`
- `dataProducts/abbrev_review_summary.xlsx`

Both GPT-assisted reviews were conducted through the standard ChatGPT web interface. Their retained prompts, batching procedures, source fields, completed GPT fields, and output workbooks provide procedural traceability. Repeating either model-assisted review is not guaranteed to produce identical judgements.

The final standardised prompts are reproduced in Appendix 6.1 for the 2,295-column Statistical Audit and Appendix 6.2 for the 795-row abbreviation re-audit. They are not duplicated in this repository.

## Operational DQA evaluation

The operational study examines forty retained successful HeadersIQ executions covering 88,856,947 analysed cells. It evaluates observed end-to-end execution time, throughput, dataset-size effects, validation-profile differences, reported DQI outcomes, and HeadersIQ behaviour.

The operational statistical analysis, detailed cross-case interpretation, and identifier-role sensitivity analysis were conducted through ChatGPT-assisted research sessions using the retained execution log and dataset-level outputs as inputs. This repository preserves those source materials and final evidence. It does not claim the existence of a separate executable analysis program where no such program was retained.

The study measures elapsed time conditional on successful execution. It does not estimate platform failure rates, run-completion probability, robustness to malformed inputs, or expected execution time including retries.

## Detailed DQA cases

Ten datasets were selected for detailed analysis:

1. Household Power Consumption
2. Ecommerce Events
3. Online Retail
4. TMDB Movies
5. F1 Pit Stops
6. Hotel Bookings
7. Doctoralia Brasil
8. NFL Fantasy Data
9. Samsung Heart Rate
10. 622 UCI Datasets

The review is supported by nineteen dataset-level files:

- ten Discoveries documents; and
- nine DQA summary workbooks.

Samsung Heart Rate did not generate a DQA summary workbook because no DQI was reported.

Only the latest version corresponding to the retained Chapter 6 execution should be archived for each dataset.

## HeadersIQ Code Runner

The HeadersIQ Code Runner is a browser-based user-facing implementation deployed through Microsoft Azure. It allows a user to submit either a supported local tabular file or a Kaggle dataset and execute the currently enabled HeadersIQ processing path.

The user-facing path includes:

1. Data Ingestion;
2. automatic header validation;
3. Column Header Preprocessing;
4. Semantic Type Detection;
5. value-aware Data Quality Assessment;
6. execution-progress reporting;
7. dataset-level result reporting; and
8. download of generated outputs when available.

The public implementation elements reported in Chapter 6 include the HeadersIQ entry page, the Code Runner, its User Guide, local and Kaggle input options, the current lexical resources, enabled processing stages, automatic header checking, Discoveries documents, DQA summary workbooks, and supporting execution files.

This repository preserves the Chapter 6 evaluation evidence associated with the Code Runner. The deployed application and production environment are maintained separately. Production credentials, server secrets, uploaded user data, temporary generated files, and environment-specific security configuration are not included here.

## Repository contents

### `code`

#### `Attribute-BasedSemanticTypeDetectionDBKG.ipynb`

Upstream Semantic Table Interpretation notebook retained because Chapter 6 directly depends on the abbreviation information it generates.

Its `preprocess_columns` function produces:

- `abbrev_clean`
- `abbrev_desc`
- `abbrev_clean_analysis`

These fields are propagated into the `abbrev_used` indicator employed in the Statistical Audit stratification and abbreviation-risk analysis.

The notebook originated in the preceding Semantic Type Detection work but remains a direct computational dependency of Chapter 6.

#### `DeepAnalysis_on118K.ipynb`

Main Statistical Audit notebook used for:

- universe partitioning;
- strict trivial and non-trivial classification;
- finite-population sample-size calculation;
- area-and-abbreviation-stratified sampling;
- rare-format coverage checking;
- sampling-workbook construction;
- GPT-output ingestion;
- metric computation;
- disagreement analysis; and
- the focused abbreviation re-audit.

The notebook `Attribute-BasedSemanticTypeDetectionDBKGSemTab2024MetadataToKG.ipynb` is associated with the preceding SemTab and Knowledge Graph work and is not included unless a direct Chapter 6 dependency is identified.

### `dataInputs`

#### `AnalysedColumnsKaggleViznetFiltered.xlsx`

Consolidated Kaggle + VizNet Universe B workbook containing the 118,639 attribute records used to define the FinalFormat-assigned universe, strict trivial subset, non-trivial audit universe, probability sample, and rare-format coverage cases.

#### `All_DQA_Execution_Log.xlsx`

Automatically generated execution log produced by the HeadersIQ DQA component.

Although this workbook is an output of the individual DQA executions, it is retained under `dataInputs` because it served as the source dataset for the forty-execution operational analysis reported in Chapter 6.

It contains the execution-level metadata used to derive the reported analysis of:

- dataset rows, columns, and analysed cells;
- elapsed execution time;
- rows, columns, and cells processed per second;
- reported DQI outcomes;
- violating-cell counts; and
- HeadersIQ values.

### `dataProducts`

#### `KaggleViznet_95CI_StatAudit_UniverseAndSample.xlsx`

Sampling workbook containing the retained universe partitions, reviewed set, area and stratum summaries, and FinalFormat coverage summaries.

Its worksheets include:

- `Nontrivial_Sample`
- `Nontrivial_Universe`
- `Trivial_Universe`
- `Trivial_cleaned_orig_multi`
- `Area_Summary`
- `Strata_Summary`
- `Formats_Summary_BeforeCoverage`
- `Formats_Summary_AfterCoverage`
- `Formats_Added_ByCoverage`

#### `GPTOutputsOn2295.xlsx`

Completed GPT-assisted review workbook for the 2,295 reviewed columns. It retains the source fields, review-order reference, and completed `GPT_*` fields.

#### `GPTAnalysisOn2295.xlsx`

Analysis workbook containing global metrics, disagreement summaries, format-level results, area-level results, format transitions, keyword suggestions, and supporting views used in the Statistical Audit analysis.

#### `K_V_superset_suspicious_abbrev.xlsx`

Targeted 795-row Kaggle + VizNet superset slice containing the eleven suspicious abbreviation mappings selected for focused re-audit.

#### `abbrev_review_summary.xlsx`

Summary workbook containing the abbreviation re-audit decision counts and suggested alternative interpretations.

### `dataProducts/discoveries`

This folder contains the ten latest Discoveries documents corresponding to the retained Chapter 6 executions.

### `dataProducts/summaryOfDQI`

This folder contains the nine latest DQA summary workbooks corresponding to the retained Chapter 6 executions. No Samsung Heart Rate summary workbook is included because no DQI was reported for that case.

### `documentation`

#### `HeadersIQ Code Runner User Guide.pdf`

Standalone copy of the HeadersIQ Code Runner User Guide reproduced in Appendix 6.3 of the thesis.

The guide documents:

- access to the public Code Runner;
- local-file and Kaggle submission;
- automatic header validation;
- execution phases and progress monitoring;
- result-page metrics;
- Discoveries and DQA summary downloads;
- supported tabular formats;
- common failure messages;
- privacy and security guidance; and
- the quick user checklist.

The guide documents the observable user-facing workflow. It does not describe the internal research implementation, production source code, or server configuration.

## Traceability and reproducibility

The following Statistical Audit components are computationally reproducible from the retained inputs, notebooks, and completed workbooks:

- abbreviation-field generation used by the audit;
- universe partitioning;
- fixed-seed probability sampling;
- rare-format coverage checking;
- workbook generation; and
- aggregation of the completed GPT review fields.

Both GPT-assisted reviews are procedurally traceable but are not guaranteed to produce identical model-generated judgements if repeated through the ChatGPT web interface.

The forty-execution analysis, detailed cross-case synthesis, and identifier-role sensitivity analysis are documented in Chapter 6 and supported by the retained execution log and nineteen dataset-level files. No separate executable analysis program is claimed where one was not retained.

The public Code Runner supports operational inspection and use. Reproduction of the complete deployed application additionally depends on the separately maintained application source, dependencies, and environment-specific deployment configuration.

Thesis tables and figures derived from these materials are reported in Chapter 6. They are not treated as separate repository artefacts unless an independently retained source file is included.

## Interpretation boundaries

The Statistical Audit approval estimate applies to the 48,442-column non-trivial FinalFormat-assigned universe under the stated informed GPT-assisted review protocol. It should not be generalised automatically to:

- the 53,763 strict trivial columns;
- the 16,434 columns without an assigned `FinalFormat`;
- datasets outside the analysed Kaggle + VizNet corpus; or
- later pipeline configurations without a new audit.

The operational runtime analysis uses one retained successful execution per dataset and characterises observed end-to-end platform behaviour. It is not a controlled benchmark of one immutable software build and does not estimate failure rates or retry-adjusted execution time.

The role-aware HeadersIQ results are sensitivity estimates. They do not retrospectively replace the strict scores produced by the operational implementation.

## Data provenance, privacy, and redistribution

Original datasets may remain subject to their providers' licences and terms of use.

Do not upload:

- private user datasets;
- passwords or secrets;
- `.env` files;
- Kaggle API credentials;
- Azure credentials;
- HTTPS private keys or certificates;
- database or storage connection strings;
- uploaded Code Runner user files;
- generated private user outputs;
- server logs containing IP addresses or submission information;
- local absolute paths containing personal information;
- restricted or non-redistributable original datasets; or
- temporary, duplicate, or superseded files.

## Related resources

- HeadersIQ public entry page: https://headersiq.github.io/
- HeadersIQ Code Runner: https://headersiq-runner.australiaeast.cloudapp.azure.com


## Release

`chapter6-v1.0`

**Chapter 6 Statistical Audit and DQA Evaluation Artefacts**

> Frozen release of the Statistical Audit, operational Data Quality Assessment evaluation, detailed case outputs, Code Runner documentation, and supporting research artefacts reported in Chapter 6.

## Citation

Silva, M. V. (2026). *Statistical Audit and Data Quality Assessment evaluation code and supporting artefacts for Chapter 6*. GitHub repository: `HeadersIQ/Statistical-Audit-and-DQA-Evaluation`.

## Status

This repository is the Chapter 6 research-artefact collection for the Statistical Audit and operational DQA evaluation. Its final release contain only the retained files that directly support the reported chapter evidence.
