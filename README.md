# Latent Structure in Big Five Personality Ratings

Can the 50-item Big Five questionnaire be represented by a stable, interpretable low-dimensional latent structure?

This project analyzes responses to the IPIP Big Five personality questionnaire using principal component analysis and factor analysis. The goal is not simply to reproduce the expected five-factor structure, but to examine how the recovered latent dimensions depend on methodological choices such as correlation measure, dimensionality selection, and factor rotation.

## Overview

The analysis focuses on three main questions:

1. Does the correlation structure of the questionnaire support a parsimonious five-dimensional representation?
2. Is factor analysis more appropriate than alternative dimension-reduction approaches for recovering interpretable latent personality traits?
3. How robust is the recovered structure to different correlation measures, factor specifications, and rotation strategies?

## Data

The dataset contains responses from **19,718 participants** to **50 IPIP Big Five items**, with 10 items corresponding to each of five personality domains:

- Extraversion
- Neuroticism
- Agreeableness
- Conscientiousness
- Openness to Experience

Responses are recorded on a 1–5 Likert scale.

Reverse-keyed items were recoded so that higher scores consistently correspond to higher levels of the intended trait.

## Methods

### Ordinal Correlation Structure

Because the questionnaire responses are ordinal, I compared:

- Pearson correlations
- Polychoric correlations

Polychoric correlations were used as the primary input for factor analysis because they better reflect the ordinal measurement scale.

The resulting correlation structure showed substantially stronger within-domain than between-domain associations.

### Factorability Assessment

The Kaiser–Meyer–Olkin (KMO) measure was used to assess whether the correlation structure was suitable for factor analysis.

The overall KMO was **0.91**, with most item-level values above 0.80, indicating strong shared correlation structure across the questionnaire items.

### PCA Baseline

Principal component analysis was used as a descriptive baseline.

Permutation parallel analysis identified **seven principal components** above the permutation-based noise threshold.

However, the dominant PCA loading patterns still broadly reflected the expected Big Five domains, with the additional components primarily capturing secondary variance structure.

### Factor Analysis

Factor analysis was used as the primary latent-variable model because the objective is to recover shared latent structure rather than simply explain total variance.

A **five-factor MINRES model** was fitted to the polychoric correlation matrix.

The unrotated solution showed substantial mixing across domains, while **varimax rotation** produced a much clearer simple structure in which each factor aligned closely with one of the five expected personality domains.

### Robustness Checks

The stability of the latent structure was evaluated across several modeling choices:

- Pearson vs. polychoric correlations
- 5-, 6-, and 7-factor specifications
- Varimax vs. promax rotation

Promax rotation produced a qualitatively similar domain structure to varimax.

The 6- and 7-factor solutions introduced additional residual structure and cross-loadings but did not reveal additional clearly interpretable broad personality dimensions.

## Key Results

### Five broad latent dimensions remain the most interpretable solution

Although permutation parallel analysis retained seven PCA components, the factor-analysis results supported a clearer **five-factor latent structure**.

The additional PCA dimensions appear to represent secondary or item-specific variation rather than two additional broad personality traits.

### Rotation substantially improves interpretability

The unrotated five-factor solution contained mixed loadings across domains.

After varimax rotation, the loading structure became substantially clearer, with factors aligning closely with:

- Extraversion
- Neuroticism
- Agreeableness
- Conscientiousness
- Openness

Promax rotation produced a similar mapping, indicating that the interpretation is not highly sensitive to whether factors are constrained to be orthogonal.

### The result is robust to the choice of correlation measure

Pearson and polychoric correlations produced the same broad domain structure.

However, polychoric correlations strengthened within-domain associations, making them more appropriate for the ordinal Likert responses.

### PCA and factor analysis answer different questions

The apparent difference between seven PCA components and five latent factors is not contradictory.

PCA summarizes directions of total variance, while factor analysis separates shared covariance from item-specific uniqueness. For this dataset, the latter provides a more interpretable representation of the underlying personality structure.

## Main Takeaways

- The Big Five questionnaire exhibits strong low-dimensional latent structure.
- A five-factor model provides the clearest broad interpretation of the 50 questionnaire items.
- Permutation parallel analysis detects additional variance directions, but these do not correspond to clearly separated additional personality domains.
- Polychoric correlations are better suited than Pearson correlations for the ordinal Likert responses, although the substantive conclusions are similar.
- The five-factor interpretation remains stable across factor-number and rotation sensitivity checks.

## Repository Structure

```text
big-five-factor-analysis/
│
├── README.md
├── report.pdf
│
├── data/
│   └── README.md
│
├── notebooks/
│   └── big_five_analysis.ipynb
│
└── figures/
    ├── response_distributions.png
    ├── polychoric_correlations.png
    ├── factorability_kmo.png
    ├── parallel_analysis.png
    ├── pca_loadings.png
    ├── factor_loadings.png
    └── rotation_robustness.png
