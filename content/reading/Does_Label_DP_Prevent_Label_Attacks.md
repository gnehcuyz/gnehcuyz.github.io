---
ShowToc: false
title: "Does Label Differential Privacy Prevent Label Inference Attacks?"
date: "2024-10-11"
draft: false
summary: "Analyzes the effectiveness of label-DP in mitigating label inference attacks and provides insights on privacy settings and attack bounds."
math: true
---

## Abstract

Label differential privacy (label-DP) trains private machine learning models with public features and sensitive labels. While label-DP provides strong privacy guarantees, models remain vulnerable to label inference attacks (LIAs). The findings show that label-DP reduces an attacker's advantage relative to a Bayes classifier but doesn't prevent attacks entirely.

## Introduction

Label-DP protects label privacy without hindering statistical inference. Key findings include:
- Label-DP reduces an attacker’s advantage but cannot fully prevent LIAs, especially for generalizable models.
- Privacy should limit an attacker’s advantage over a Bayes classifier rather than eliminate statistical inference.

## Preliminaries

Label-DP assumes public features and private labels, commonly used in:
- Online advertising.
- Recommendation systems.

### Methods for Achieving Label-DP

1. **Randomized Response (RR)**: Adds randomness to released labels.
2. **Label Private Multi-Stage Training (LP-MST)**: Predicts labels from learned priors.
3. **PATE-FixMatch (PATE-FM)**: Uses teacher models to train private student models.
4. **ALIBI**: Adds noise to labels, recovering them via Bayesian inference.

## Does Label-DP Prevent LIAs?

Experiments reveal that label-DP struggles to protect against LIAs effectively. Attack accuracy aligns closely with model test accuracy, highlighting limitations even under strong privacy settings.

## Label-DP Provably Bounds Attack Advantage

Label-DP reduces attack advantage depending on privacy parameters (ε, δ), but attacks remain possible, particularly when the feature matrix is known.

## Experiments

### Simulated Dataset (Gaussian Mixture):
- Stronger privacy (lower ε) reduces Expected Attack Utility (EAU).
- Attack advantage stays below theoretical upper bounds.

### Real-World Dataset (CTR Prediction):
- High EAU for large ε values; reduced EAU as ε decreases.
- Label-DP models approach constant prediction baselines.

## Limitations

- Focus on ε, δ-label-DP; future work could explore Rényi-DP or Gaussian-DP.
- Limited real-world dataset evaluation highlights a need for broader testing.

## Thoughts After Reading

- Comprehensive testing on diverse datasets is essential to improve label-DP robustness.


## Reference
Ji, S., Pan, X., Zhang, X., et al. (2022). *Privacy-Preserving Machine Learning with Differential Privacy and Secure Multiparty Computation*. *Proceedings of the 2022 IEEE International Conference on Data Engineering (ICDE)*, pp. 1854–1865. [DOI:10.1109/ICDE53745.2022.00354](https://ieeexplore.ieee.org/abstract/document/9833321)






