# Statistical Audit and Data Quality Assessment Evaluation

PhD thesis: Attribute-Based Approach for Semantic Type Detection and Data Quality Assessment in Diverse Data Sources and Domains

Author: Marcelo Valentim Silva

University: Curtin University, Perth, Western Australia

This repository contains the research code, retained inputs, generated workbooks, prompts, execution records, selected dataset-level outputs, figures, and supporting documentation associated with the Statistical Audit and operational Data Quality Assessment evaluation reported in Chapter 6 of the PhD thesis Attribute-Based Approach for Semantic Type Detection and Data Quality Assessment in Diverse Data Sources and Domains.

The repository covers two complementary components:

1. the Statistical Audit of large-scale Semantic Type Detection assignments over the Kaggle + VizNet corpus; and
2. the empirical operational evaluation of the HeadersIQ Data Quality Assessment component, including runtime analysis, detailed dataset cases, HeadersIQ sensitivity analysis, and evidence from the public HeadersIQ Code Runner.

Author-identifying repository metadata is intentionally limited while related research outputs remain subject to anonymous review.

## Chapter 6 scope

### Statistical Audit

The Statistical Audit begins with Kaggle + VizNet Universe B, which contains 118,639 attribute records.

- 102,205 columns received one of the 39 available `FinalFormat` assignments.
- 16,434 columns had no assigned `FinalFormat` and were outside the semantic-assignment approval estimate.
- The `FinalFormat`-assigned universe was partitioned into:
  - 53,763 strict trivial columns; and
  - 48,442 non-trivial columns requiring scrutiny.
- A finite-population, area-and-abbreviation-stratified probability sample of 2,288 columns was drawn from the non-trivial universe.
- Seven purposively selected rare-format cases were added for diagnostic coverage.
- The complete reviewed set therefore contains 2,295 columns.

The 2,288-column probability sample supports inferential estimation. The seven additional cases support format-level diagnostic analysis.

### GPT-assisted review

The main review protocol was developed through an initial 300-row pilot and then frozen. The complete set of 2,295 reviewed rows, including the original pilot cases, was subsequently processed in batches of a few hundred rows using the same final standardised prompt.

The review was conducted through the standard ChatGPT web interface. The retained prompt, batching procedure, source fields, completed `GPT_*` fields, and analysis workbooks provide procedural traceability. Repeating the model-assisted review is not guaranteed to produce identical judgements.

### Operational DQA evaluation

The operational study examines forty retained successful HeadersIQ executions covering 88,856,947 analysed cells. It evaluates observed end-to-end runtime, throughput, dataset-size effects, validation-profile differences, reported DQI outcomes, and HeadersIQ behaviour.

The study measures elapsed time conditional on successful execution. It does not estimate platform failure rates, run-completion probability, robustness to malformed inputs, or expected time including retries.

### Detailed DQA cases

Ten datasets were selected for detailed analysis because they provide contrasting evidence concerning:

- successful format-specific validation;
- direct data conditions;
- semantic-assignment propagation;
- context-dependent validation rules;
- identifier roles;
- conditional missingness;
- unsupported semantic coverage;
- score sensitivity; and
- substantial validation workload without reported DQIs.

The detailed review is supported by nineteen dataset-level artefacts:

- ten Discoveries documents; and
- nine DQA summary workbooks.

Samsung Heart Rate did not generate a DQA summary workbook because no DQI was reported.

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

The public interface and its supporting artefacts correspond to the implementation elements reported in Table 6.17 of the thesis:

- the HeadersIQ public entry page;
- the Code Runner interface;
- the Appendix 6.3 User Guide;
- local-upload and Kaggle input options;
- the current Formats Dictionary and Abbreviations Dictionary;
- the enabled processing stages;
- automatic header checking;
- Discoveries documents;
- DQA summary workbooks; and
- supporting code and execution files.

The Code Runner itself is deployed separately from this research-artefact repository. This repository preserves the Chapter 6 documentation and evaluation evidence associated with the user-facing implementation, including the User Guide, execution records, selected generated outputs, runtime analysis, and detailed case evidence.

The application source code does not need to be duplicated in this repository when it is maintained in a separate HeadersIQ implementation repository. Before the final release, add the public source-code repository link in the Related Resources section if a sanitised version is available. Production credentials, server secrets, uploaded user data, temporary generated files, and environment-specific security configuration must not be published.

## Repository structure

```text
Statistical-Audit-and-DQA-Evaluation/
├── README.md
├── code/
│   ├── DeepAnalysis_on118K.ipynb
│   └── operationalDQA/
│       ├── RuntimeAnalysis.ipynb
│       ├── HeadersIQSensitivityAnalysis.ipynb
│       └── supporting_scripts/
├── dataInputs/
│   ├── AnalysedColumnsKaggleViznetFiltered.xlsx
│   └── operationalDQA/
│       └── All_DQA_Execution_Log_Comparison.xlsx
├── dataProducts/
│   ├── GPTAnalysisOn2295.xlsx
│   ├── GPTOutputsOn2295.xlsx
│   ├── K_V_superset_suspicious_abbrev.xlsx
│   ├── KaggleViznet_95CI_StatAudit_UniverseAndSample.xlsx
│   ├── abbrev_review_summary.xlsx
│   └── operationalDQA/
│       ├── executionAnalysis/
│       ├── detailedCases/
│       │   ├── discoveries/
│       │   └── dqaSummaries/
│       ├── figures/
│       └── identifierRoleSensitivity/
├── prompts/
│   ├── Appendix6_1_Final_Statistical_Audit_Prompt.txt
│   └── Appendix6_2_Abbreviation_Reaudit_Prompt.txt
└── documentation/
    ├── Appendix6_3_HeadersIQ_Code_Runner_User_Guide.pdf
    ├── Chapter6_Artefact_Manifest.md
    └── Reproduction_Notes.md
```

The folder names above define the intended final structure. Some folders should be created only when their corresponding Chapter 6 files are uploaded.

## Upstream Chapter 5 processing

The Statistical Audit uses the consolidated Kaggle + VizNet semantic-assignment output produced by the header-centric Semantic Type Detection pipeline reported in Chapter 5.

The upstream Semantic Type Detection, SemTab metadata, and Knowledge Graph processing notebooks belong to the Chapter 5 research materials and are not duplicated here.

The retained Chapter 6 input is:

- `dataInputs/AnalysedColumnsKaggleViznetFiltered.xlsx`

This workbook contains the consolidated attribute-level records from which the Chapter 6 audit universes, probability sample, and rare-format diagnostic cases were constructed.

## Statistical Audit files

### Code

#### `code/DeepAnalysis_on118K.ipynb`

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
- focused abbreviation re-audit.

### Retained input

#### `dataInputs/AnalysedColumnsKaggleViznetFiltered.xlsx`

Consolidated Kaggle + VizNet Universe B input used to construct the Statistical Audit populations and reviewed set.

### Generated products

#### `dataProducts/KaggleViznet_95CI_StatAudit_UniverseAndSample.xlsx`

Sampling workbook containing the retained universe partitions, complete reviewed set, area and stratum summaries, and FinalFormat coverage summaries.

The workbook includes:

- `Nontrivial_Sample`
- `Nontrivial_Universe`
- `Trivial_Universe`
- `Trivial_cleaned_orig_multi`
- `Area_Summary`
- `Strata_Summary`
- `Formats_Summary_BeforeCoverage`
- `Formats_Summary_AfterCoverage`
- `Formats_Added_ByCoverage`

#### `dataProducts/GPTOutputsOn2295.xlsx`

Completed GPT-assisted review workbook for the 2,295 reviewed columns. It retains the source fields, review-order reference, and completed `GPT_*` fields.

#### `dataProducts/GPTAnalysisOn2295.xlsx`

Analysis workbook containing the global metrics, disagreement summaries, format-level results, area-level results, transition summaries, keyword suggestions, and supporting views used in the Statistical Audit analysis.

#### `dataProducts/K_V_superset_suspicious_abbrev.xlsx`

Targeted 795-row Kaggle + VizNet superset slice containing the eleven abbreviation mappings selected for focused re-audit.

#### `dataProducts/abbrev_review_summary.xlsx`

Summary workbook containing the abbreviation re-audit decision counts and suggested alternative interpretations.

## Operational DQA evaluation files

### Code to upload

Upload to `code/operationalDQA/`:

- the notebook or script used to harmonise and analyse the forty retained execution records;
- the notebook or script used to calculate descriptive statistics, Spearman correlations, and the log-log regression;
- the notebook or script used to generate the runtime figures;
- the notebook, script, or workbook used for the Ecommerce Events and Online Retail role-aware HeadersIQ sensitivity calculations; and
- any supporting functions required to reproduce the reported Chapter 6 tables and figures.

Suggested names are:

- `RuntimeAnalysis.ipynb`
- `Generate_Runtime_Figures.ipynb`
- `HeadersIQSensitivityAnalysis.ipynb`

Use the original retained filenames when they already appear in the thesis, repository records, or generated outputs.

### Input data to upload

Upload to `dataInputs/operationalDQA/`:

- `All_DQA_Execution_Log_Comparison.xlsx`, or the final harmonised forty-execution workbook used for Table 6.11 and the runtime analysis; and
- any small retained input workbook required for the role-aware HeadersIQ sensitivity calculations.

### Execution-analysis products to upload

Upload to `dataProducts/operationalDQA/executionAnalysis/`:

- the final statistical summary workbook;
- the source table for the workload comparisons;
- any retained regression-output file; and
- any derived table used to produce the reported runtime results.

### Figures to upload

Upload to `dataProducts/operationalDQA/figures/`:

- the final execution-time figure;
- the log-log relationship figure;
- the throughput figure;
- the selected workload-comparison figure; and
- any other Chapter 6 figure generated directly from the forty-execution analysis.

Use the same figure numbers or filenames used in the thesis where practical.

## Detailed case outputs

Upload the ten Discoveries documents to:

`dataProducts/operationalDQA/detailedCases/discoveries/`

Upload the nine DQA summary workbooks to:

`dataProducts/operationalDQA/detailedCases/dqaSummaries/`

The ten detailed cases are:

1. 622 UCI Datasets
2. Samsung Heart Rate
3. NFL Fantasy Data
4. Doctoralia Brasil
5. Hotel Bookings
6. Online Retail
7. F1 Pit Stops
8. Ecommerce Events
9. Household Power Consumption
10. TMDB Movies

The repository should contain one Discoveries document for each case and one DQA summary workbook for each case except Samsung Heart Rate.

## Identifier-role sensitivity files

Upload to `dataProducts/operationalDQA/identifierRoleSensitivity/`:

- the retained calculation for Ecommerce Events;
- the retained calculation for Online Retail;
- any workbook or script showing the strict and role-aware HeadersIQ values; and
- a short note identifying which duplicate-related findings were excluded and how overlapping DQI findings were handled.

The role-aware recalculation must preserve:

- the original analysed-cell denominator;
- all missingness findings;
- all non-identifier DQI findings; and
- the existing overlap-control procedure.

## Prompts

Upload to `prompts/`:

### `Appendix6_1_Final_Statistical_Audit_Prompt.txt`

The final standardised prompt used for the complete 2,295-row GPT-assisted review. The prompt may retain its historical reference to the first 300 items because that wording formed part of the frozen instruction set.

### `Appendix6_2_Abbreviation_Reaudit_Prompt.txt`

The final standardised prompt used for the focused 795-row abbreviation re-audit.

The prompt files should match the corresponding thesis appendices.

## Code Runner documentation

Upload to `documentation/`:

### `Appendix6_3_HeadersIQ_Code_Runner_User_Guide.pdf`

A standalone copy of the Code Runner User Guide reproduced in Appendix 6.3 of the thesis.

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

The guide documents the observable user-facing workflow. It does not replace source-code documentation or describe production server configuration.

## Artefact manifest

Create:

`documentation/Chapter6_Artefact_Manifest.md`

The manifest should map each repository file to the thesis evidence it supports.

Recommended structure:

| Repository item | Research role | Thesis section, table, figure, or appendix |
|---|---|---|
| `DeepAnalysis_on118K.ipynb` | Statistical Audit construction and analysis | Sections 6.2.3 to 6.2.5; Algorithms 6.1 to 6.3 |
| `GPTOutputsOn2295.xlsx` | Completed GPT-assisted review | Section 6.2.5 |
| `GPTAnalysisOn2295.xlsx` | Audit metrics and disagreement summaries | Section 6.2.5 |
| `abbrev_review_summary.xlsx` | Abbreviation re-audit summaries | Tables 6.9 and 6.10 |
| Forty-execution log | Operational runtime evidence | Table 6.11 |
| Runtime-analysis code | Correlations, regression, and figures | Section 6.3.3 |
| Ten Discoveries documents | Narrative DQA evidence | Detailed DQA case analysis |
| Nine DQA summary workbooks | Structured DQA evidence | Detailed DQA case analysis |
| Identifier-role sensitivity files | Strict and role-aware HeadersIQ estimates | Table 6.14 |
| Final audit prompt | Main GPT-assisted review protocol | Appendix 6.1 |
| Abbreviation re-audit prompt | Focused abbreviation-review protocol | Appendix 6.2 |
| Code Runner User Guide | Public operational workflow | Appendix 6.3 and Table 6.17 |

## Reproduction notes

Create:

`documentation/Reproduction_Notes.md`

Document:

- the input file required for each notebook;
- expected relative paths;
- software and Python version, when known;
- important package versions, when known;
- random seed used for sampling;
- execution order;
- generated output files;
- known environment assumptions;
- whether Kaggle access is required;
- which results are deterministic;
- which GPT-assisted steps are only procedurally traceable;
- the deployment environment relevant to the operational evaluation, where recorded; and
- the location of the separately maintained Code Runner source code, when publicly available.

## Reproducibility and repeatability

The following components are computationally reproducible from the retained inputs and code:

- universe partitioning;
- fixed-seed probability sampling;
- rare-format coverage checking;
- workbook generation;
- aggregation of completed GPT fields;
- summary-table generation; and
- statistical analysis of the retained execution log.

The GPT-assisted annotation process is procedurally traceable but has limited repeatability because it was conducted through the ChatGPT web interface without API-level generation controls.

The reported confidence interval quantifies sampling uncertainty under the stated probability-sampling design. It does not incorporate uncertainty arising from model judgement error, prompt sensitivity, stochastic model behaviour, model updates, or the informed-review protocol.

The public Code Runner supports operational inspection and use. Reproduction of the complete deployed application additionally depends on the separately maintained application source, dependencies, and environment-specific deployment configuration.

## Interpretation boundaries

The Statistical Audit approval estimate applies to the 48,442-column non-trivial `FinalFormat`-assigned universe under the stated informed GPT-assisted review protocol. It should not be generalised automatically to:

- the 53,763 strict trivial columns;
- the 16,434 columns without an assigned `FinalFormat`;
- datasets outside the analysed Kaggle + VizNet corpus; or
- later pipeline configurations without a new audit.

The operational runtime analysis uses one retained successful execution per dataset and characterises observed end-to-end platform behaviour. It is not a controlled benchmark of one immutable software build and does not estimate failure rates or retry-adjusted execution time.

The role-aware HeadersIQ results are sensitivity estimates. They do not retrospectively replace the strict scores produced by the operational implementation.

## Data provenance and redistribution

Original datasets may remain subject to their providers' licences and terms of use.

This repository should contain only:

- retained derived research inputs that can be shared;
- generated research workbooks;
- analysis code;
- prompts;
- figures;
- selected outputs;
- the Code Runner User Guide; and
- supporting documentation.

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
- temporary files not used by the reported analysis.

## Related resources

- HeadersIQ public entry page: https://headersiq.github.io/
- HeadersIQ Code Runner: https://headersiq-runner.australiaeast.cloudapp.azure.com
- HeadersIQ application source: add the final public source-code repository URL here before the frozen release, when available.
- Chapter 5 research materials: add the final Chapter 5 repository URL here if cross-repository provenance is required.

## Final repository checklist

Before creating a frozen release:

1. remove the two Chapter 5 Semantic Type Detection and Knowledge Graph notebooks from this Chapter 6 repository;
2. confirm that `DeepAnalysis_on118K.ipynb` and the five Statistical Audit workbooks are present;
3. upload the forty-execution log and operational-analysis code;
4. upload the runtime figures and derived analysis products;
5. upload the ten Discoveries documents;
6. upload the nine DQA summary workbooks;
7. upload the two identifier-role sensitivity calculations;
8. upload the final Statistical Audit prompt;
9. upload the final abbreviation re-audit prompt;
10. upload the standalone Appendix 6.3 Code Runner User Guide;
11. create the artefact manifest;
12. create the reproduction notes;
13. add the public Code Runner source link if a sanitised source repository is available;
14. remove temporary, duplicate, superseded, private, or restricted files;
15. confirm that filenames match the thesis artefact tables;
16. verify that notebooks and workbooks open without corruption; and
17. update this README if the final repository structure differs.

## Release

After the final materials are uploaded, create a tagged release such as:

`chapter6-v1.0`

Suggested release title:

`Chapter 6 Statistical Audit and DQA Evaluation Artefacts`

Suggested release description:

`Frozen release of the Statistical Audit, operational Data Quality Assessment evaluation, detailed case outputs, Code Runner documentation, and supporting research artefacts reported in Chapter 6.`

Do not add personal citation metadata until the anonymous-review requirements have ended.

## Citation

During anonymous review, repository-level citation metadata may remain neutral.

The thesis may identify the scholarly author separately from the repository account:

Silva, M. V. (2026). *Statistical Audit and Data Quality Assessment evaluation code and supporting artefacts for Chapter 6*. GitHub repository: `HeadersIQ/Statistical-Audit-and-DQA-Evaluation`.

After anonymous review, add a `CITATION.cff` file containing the final author, title, year, repository URL, version, and ORCID information where appropriate.

## Status

This repository is a research-artefact collection. Some folders and files described in this README may be added while the final Chapter 6 archive is being completed.
