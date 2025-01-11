---
ShowToc: true
title: Label Inference Attacks Against Vertical Federated Learning
date: 2024-09-16
draft: false
summary: Evaluates privacy risks of vertical federated learning (VFL) and proposes label inference attacks with outstanding performance, highlighting vulnerabilities and defense limitations.
math: true
---

# Introduction
- **Focus**: Privacy risks in Vertical Federated Learning (VFL), a framework enabling multi-party collaboration without sharing raw data.
- **Problem**: Adversaries can exploit VFL's structure to infer sensitive label information.
- **Key Insight**: Gradients and bottom model vulnerabilities allow label inference.

# Contributions
1. Introduced three types of label inference attacks (direct, passive, active).
2. Demonstrated attack feasibility across multiple datasets and scenarios.
3. Evaluated potential defenses and highlighted their limitations.
4. Shared insights into VFL vulnerabilities and proposed future research directions.

# Methodology
- **Passive Label Inference Attack**: Exploits bottom model representations with a small labeled dataset to infer labels.
- **Active Label Inference Attack**: Enhances attack performance by manipulating the federated model to rely on adversary data.
- **Direct Label Inference Attack**: Analyzes gradients to infer labels directly (limited to training data).

# Results
- High inference accuracy on various datasets (e.g., CIFAR-10, CIFAR-100, BHI).
- Active attacks outperformed passive ones by boosting bottom model expressiveness.
- Defenses like noisy gradients and gradient compression showed limited effectiveness.

# Discussion
- **Defenses Evaluated**:
  - Noisy Gradients
  - Gradient Compression
  - Privacy-Preserving Deep Learning
  - DiscreteSGD (a modified SignSGD)
- **Findings**:
  - Existing defenses mitigate only some attack types and often degrade model performance.
  - Calls for novel defense strategies tailored to VFL.

# Future Work
- Expand evaluations to other ML models and architectures (e.g., logistic regression, gradient boosting trees).
- Investigate additional privacy risks in VFL and design robust defense mechanisms.

# Conclusion
This work sheds light on inherent privacy risks in VFL, proposing effective attacks and emphasizing the urgency of developing tailored defenses to protect sensitive data.

# Reference
- Fu, C., Zhang, X., Ji, S., et al. (2022). *Label Inference Attacks Against Vertical Federated Learning*. Proceedings of the 31st USENIX Security Symposium. [Link to paper](https://www.usenix.org/conference/usenixsecurity22/presentation/fu-chong)
