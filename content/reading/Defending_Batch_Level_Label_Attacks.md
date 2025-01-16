---
ShowToc: false
title: "Defending Batch-Level Label Inference and Replacement Attacks in Vertical Federated Learning"
date: "2024-10-07"
draft: false
summary: "Explores vulnerabilities in VFL models to label inference and backdoor attacks and proposes effective defenses like CAE and DCAE."
math: true
---

## Introduction

This paper explores the vulnerabilities of Vertical Federated Learning (VFL) models to batch-level label inference and backdoor attacks. The authors demonstrate that even with Homomorphic Encryption (HE) protection, batch-level gradients can be exploited to infer labels with high accuracy. Key contributions include:

- Demonstrating label inversion and replacement attacks through gradient manipulation.
- Proposing Confusional Autoencoder (CAE) and its enhanced version, DiscreteSGD-enhanced CAE (DCAE), as defense strategies.
- Balancing privacy and task accuracy better than existing techniques like Differential Privacy and Gradient Sparsification.

## Related Work

Key points:
- Introduction of a new label inversion attack specific to VFL settings that leverages batch-level gradients for high accuracy.
- A novel backdoor attack approach enabling gradient modifications while preserving task performance.
- Development of defense methods combining autoencoders with entropy regularization for robust label protection.

## VFL Framework with Homomorphic Encryption

The VFL framework uses HE to ensure data security during collaborative training. Each party manages a portion of the feature vector, with encrypted updates protecting sensitive data. This framework enables secure multi-organization collaboration while maintaining efficiency.

## Batch-Level Label Inference Attacks

Threat model assumptions:
1. Attackers control the training process of one passive party and access its local model.
2. They can access batched-averaged gradients and encrypted per-sample gradients but cannot modify updates or coordination protocols.

Unlike prior models, attackers in this scenario can act only at the batch/population level and do not rely on balanced auxiliary labeled samples.

## Label Replacement Backdoor Attacks

Backdoor attacks involve replacing some labels stealthily through gradient manipulation. This method allows attackers to inject triggers into the model without affecting overall task accuracy, causing mislabeling in targeted scenarios.

## Defense Mechanisms

The proposed defenses include CAE and DCAE, which obscure true labels through noise and confusion. These methods effectively counter label inference and backdoor attacks while maintaining task performance.

## Experiments

- **Batch-Level Label Inference Attacks**: Performance improves with increased class diversity but becomes challenging as the search space grows.
- **Backdoor Attacks**: Achieve over 90% success with well-chosen trigger patterns and amplification rates.
- **Defenses**: CAE and DCAE significantly reduce attack success while preserving task accuracy.

## Thoughts After Reading

- **Accuracy Trade-offs**: Future research should minimize accuracy loss while enhancing privacy.
- **Testing Beyond Image Data**: Expanding to text, time-series, and graph data can evaluate defense robustness across diverse fields like healthcare and finance.

## Reference
Ye, M., Zhou, C., Ji, S., et al. (2022). *Defending Against Membership Inference Attacks via Adversarial Examples and Ensemble Learning*. [arXiv:2202.12968](https://arxiv.org/abs/2202.12968)