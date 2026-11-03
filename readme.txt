# Spanish Higher Education ABSA Dataset

## Overview

This repository contains an anonymized dataset of Spanish-language student feedback from higher education, structured for Aspect-Based Sentiment Analysis (ABSA).

The dataset contains **62,258 aspect-level instances derived from 41,874 unique student comments**. Each record associates a student comment with a sentiment label, an institutional aspect, and a thematic category.

The dataset was prepared for research on sentiment analysis, aspect-based sentiment analysis, natural language processing, and the analysis of student feedback in higher education.

## Dataset File

`spanish_higher_education_absa_dataset.csv`

**Encoding:** UTF-8  
**Format:** CSV  
**Language:** Spanish

## Dataset Size

- **Aspect-level instances:** 62,258
- **Unique comments:** 41,874
- **Sentiment classes:** 2
- **Institutional aspects:** 12
- **Thematic categories:** 78

### Sentiment Distribution

| Sentiment | Instances |
|---|---:|
| Negative | 36,073 |
| Positive | 26,185 |
| **Total** | **62,258** |

## Data Structure

The dataset contains the following fields:

| Field | Description |
|---|---|
| `businessLevel` | Organizational or analytical level associated with the feedback instance. |
| `comentario` | Anonymized student comment in Spanish. |
| `Valor` | Sentiment label assigned to the comment-aspect instance (`Positivo` or `Negativo`). |
| `nombreAspecto` | Institutional aspect associated with the feedback. |
| `nombreTema` | Thematic category associated with the feedback. |
| `comment_id` | Deterministic identifier used to group instances originating from the same normalized comment. |

## Aspect-Level Structure

The dataset follows an **aspect-level representation**.

A single student comment may refer to more than one institutional aspect. Consequently, the same `comment_id` and comment text may appear in multiple rows when the comment is associated with different aspects or thematic categories.

Therefore, the **62,258 rows should not be interpreted as 62,258 independent student comments**. They represent aspect-level instances derived from **41,874 unique comments**.

Researchers performing machine-learning experiments should take this structure into account when partitioning the dataset. In particular, instances sharing the same `comment_id` should be kept within the same data partition to reduce the risk of information leakage between training, validation, and test sets.

## Privacy and Anonymization

The public dataset was prepared to reduce the risk of disclosure of personal information contained in free-text responses.

Direct identifiers detected during the privacy review were replaced with neutral placeholders, including:

- `[PERSON]`
- `[STUDENT_ID]`
- `[EMAIL]`
- `[PHONE]`

Additional institutional or contextual variables present in the research dataset were excluded from the public release to further reduce disclosure risk.

The public dataset therefore contains only the variables required to support the intended ABSA research use.

## Data Quality and Repeated Rows

The public release preserves the **62,258 aspect-level instances** used in the research dataset.

Because selected contextual variables were removed from the public version, some records may appear identical across the six released fields. These records should **not automatically be interpreted as accidental duplicates**.

Removing them solely on the basis of equality across the public fields would modify the experimental dataset and may affect reproducibility.

## Recommended Uses

The dataset may support research on:

- Aspect-Based Sentiment Analysis (ABSA)
- Sentiment classification
- Natural Language Processing in Spanish
- Educational data mining
- Student experience analytics
- Higher education quality analysis
- Comparative evaluation of machine-learning and language models

## Reproducibility Considerations

For experiments involving train/validation/test partitions, researchers are encouraged to perform group-aware splitting using `comment_id`.

This prevents instances derived from the same normalized student comment from being distributed across different partitions.

Any additional preprocessing, filtering, resampling, or label transformation should be explicitly documented when reporting results obtained from this dataset.

## Citation

If you use this dataset in academic research, please cite the associated dataset record and the corresponding research article.

The definitive DOI and bibliographic information should be obtained from the Zenodo record associated with the released version.

## Authors

**Anabel Pineda-Briseño**  
ORCID: 0000-0002-5296-4210

**Jimy Oblitas Cruz**  
ORCID: 0000-0001-7652-6672

## Version

**Version 1.0.0**

Initial public release of the anonymized Spanish Higher Education ABSA Dataset.

## License and Use

Users should consult the license and usage conditions specified in the associated Zenodo record before reusing or redistributing the dataset.