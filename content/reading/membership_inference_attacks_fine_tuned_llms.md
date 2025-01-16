---
ShowToc: false
title: Membership Inference Attacks Against Fine-tuned Large Language Models via Self-prompt Calibration
date: "2024-01-18"
draft: false
summary: A novel study introducing self-prompt calibration for membership inference attacks (MIAs) against fine-tuned large language models, improving reliability and practicality in privacy assessments.
math: true
---

### Overview
This paper presents an innovative approach to Membership Inference Attacks (MIAs) targeting fine-tuned large language models (LLMs). The proposed **Self-calibrated Probabilistic Variation-based MIA (SPV-MIA)** addresses limitations of existing methods, such as dependency on overfitting and access to high-quality reference datasets.

### Contributions
The study makes three major contributions:
1. **Self-prompt Calibration:** A method to generate reference datasets by prompting the target LLM, enabling attacks without unrealistic assumptions.
2. **Probabilistic Variation Metric:** A robust membership signal leveraging LLM memorization rather than overfitting.
3. **Experimental Validation:** Demonstrates superior privacy risks using SPV-MIA across various LLMs and datasets, achieving an average 23.6% improvement in AUC compared to baseline methods.

### Methodology
#### Self-prompt Calibration
Existing MIAs rely on reference datasets, often impractical to obtain. The authors propose using the target LLM to generate a self-prompt dataset, mimicking the training data distribution. This reference model significantly enhances attack performance.

#### Probabilistic Variation Assessment
By focusing on LLM memorization, the study introduces a probabilistic variation metric to measure membership likelihood, mitigating the reliance on overfitting. This involves analyzing symmetrical perturbations and paraphrased text variations.

### Experimental Findings
- **Datasets:** WikiText-103, AG News, and XSum.
- **Models:** GPT-2, GPT-J, Falcon-7B, and LLaMA-7B.
- SPV-MIA outperformed existing MIAs, with an average AUC of 0.924 and TPR@1%FPR of 46.9%.
- **Resilience:** Demonstrated robustness in scenarios with limited data and diverse sources for self-prompts.

### Implications
This work highlights critical privacy risks in fine-tuned LLMs and underscores the importance of considering memorization over overfitting. Future research should extend SPV-MIA to other LLM paradigms and explore defensive strategies.

---

### Reference
Fu, W., Wang, H., Gao, C., Liu, G., Li, Y., & Jiang, T. (2024). Membership Inference Attacks Against Fine-tuned Large Language Models via Self-prompt Calibration. *Proceedings of the 38th Conference on Neural Information Processing Systems (NeurIPS 2024)*. [Read the full paper](https://arxiv.org/abs/2311.06062).
