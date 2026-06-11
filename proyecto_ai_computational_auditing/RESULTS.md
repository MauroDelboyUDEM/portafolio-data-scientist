# Results: Computational Auditing Framework for Generative AI

## Overview

This document summarizes the main empirical results of the **Computational Auditing Framework for Generative AI**, focused on measuring token-based computational differences across languages.

The analysis introduces the **Token-Linguistic Inequality Index (IDTL/TLII)**, a metric designed to quantify how many more tokens a language requires compared to English when expressing semantically equivalent content.

---

## Dataset

The empirical analysis uses the **FLORES-200 parallel corpus**, which provides semantically equivalent sentences across multiple languages.

### Languages analyzed

* English
* Spanish
* Portuguese
* German
* Simplified Chinese

### Sample size

* 997 parallel observations

---

## Tokenizer

The analysis uses the `cl100k_base` tokenizer implemented through the `tiktoken` Python library.

This tokenizer was selected because it is associated with contemporary large language model ecosystems and allows a practical evaluation of token-based computational efficiency.

---

## Main Metric: IDTL / TLII

The Token-Linguistic Inequality Index is defined as:

```math
IDTL_i = \frac{Tokens_i}{Tokens_{English}}
```

Values greater than 1 indicate that a language requires more tokens than English to express semantically equivalent content.

---

## Descriptive Results

| Language           | Average Tokens | IDTL |
| ------------------ | -------------: | ---: |
| English            |          25.88 | 1.00 |
| Portuguese         |          38.29 | 1.49 |
| Spanish            |          40.01 | 1.56 |
| German             |          40.74 | 1.59 |
| Simplified Chinese |          48.90 | 1.89 |

---

## Key Finding

The results show that some languages require substantially more tokens than English to represent comparable semantic content.

In practical terms:

* Portuguese requires approximately **49% more tokens** than English.
* Spanish requires approximately **56% more tokens** than English.
* German requires approximately **59% more tokens** than English.
* Simplified Chinese requires approximately **89% more tokens** than English.

This suggests that tokenization can create measurable computational differences across languages.

---

## Statistical Validation

The analysis includes several statistical validation procedures:

* Bootstrap confidence intervals
* Friedman test for repeated measures
* Wilcoxon post-hoc pairwise comparisons
* Mixed-effects modeling

The Friedman test indicated statistically significant differences across languages, supporting the hypothesis that token consumption varies systematically by language.

Most pairwise Wilcoxon comparisons were statistically significant, with the main exception being the comparison between Spanish and German.

---

## Optimization Results

An exploratory token optimization procedure was also evaluated under semantic preservation constraints.

The observed reductions were limited:

| Language           | Original Tokens | Optimized Tokens | Reduction % | Mean Similarity |
| ------------------ | --------------: | ---------------: | ----------: | --------------: |
| English            |           25.88 |            25.88 |       0.006 |           1.000 |
| Spanish            |           40.01 |            39.94 |       0.147 |           0.999 |
| Portuguese         |           38.29 |            38.28 |       0.023 |           1.000 |
| German             |           40.74 |            40.74 |       0.006 |           1.000 |
| Simplified Chinese |           48.90 |            48.90 |       0.000 |           1.000 |

These results suggest that superficial linguistic reformulation has limited capacity to reduce token consumption when strict semantic preservation is required.

---

## Interpretation

The results do not imply intentional bias in tokenizer design. Instead, they show that apparently neutral computational infrastructures can generate measurable efficiency differences across languages.

In token-priced AI systems, these differences may affect:

* API usage cost
* Context window consumption
* Latency
* Computational load
* Multilingual scalability

---

## Research Contribution

This project contributes to:

* Generative AI auditing
* Responsible AI
* Computational linguistics
* Multilingual NLP
* LLM cost optimization
* AI governance
* Operations research applied to language systems

---

## Main Conclusion

Tokenization should not be treated only as a technical preprocessing step. It is also a computational layer capable of producing measurable operational differences across languages.

The proposed IDTL/TLII framework offers a reproducible way to quantify, compare and monitor these differences in generative AI systems.
