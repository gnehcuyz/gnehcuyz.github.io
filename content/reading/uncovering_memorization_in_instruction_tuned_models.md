---
ShowToc: false
title: Using LLMs to Uncover Memorization in Instruction-Tuned Models
date: "2024-10-11"
draft: false
summary: A study introducing a black-box prompt optimization approach to uncover higher levels of memorization in instruction-tuned LLMs.
math: true
tags: [Large Language Model, Memorization]
---

### Overview
This paper investigates memorization in large language models (LLMs), focusing on how instruction-tuned models can reveal more pre-training data than their base counterparts. It introduces a **black-box prompt optimization method**, leveraging an attacker model to generate effective prompts that induce training data leakage from instruction-tuned models like Alpaca and Vicuna.

### Contributions
The paper highlights three major contributions:
1. **Prompt Optimization Approach:** A method to optimize prompts iteratively, increasing overlap between generated outputs and training data while minimizing prompt similarity to the original training context.
2. **Higher Memorization Discovery:** Demonstrates that instruction-tuned models can expose up to 23.7% more training data compared to baseline methods.
3. **Automated Attack Exploration:** Introduces automated strategies for auditing memorization in LLMs, identifying privacy risks through efficient and reproducible techniques.

### Methodology
#### Black-box Prompt Optimization
This approach uses an iterative rejection-sampling process to optimize prompts. The attacker model generates candidates that maximize output overlap with training data while penalizing prompt similarity to the ground truth.

#### Evaluation Metrics
The study employs **ROUGE-L** to measure memorization (overlap between generated and true data) and **Longest Common Subsequence Prompt-Overlap (LCSP)** to quantify prompt similarity with training data.

### Experimental Findings
- **Datasets and Models:** Evaluated on models like Alpaca, Tulu, and Vicuna across datasets such as GitHub, ArXiv, and C4.
- **Results:** The proposed method achieves:
  - 12.4% higher memorization detection in instruction-tuned models than base models.
  - 12.5% more training data extraction compared to white-box methods like Greedy Coordinate Gradient (GCG).
- **Insights:** Larger sequence lengths and open-source attacker models (e.g., Zephyr) enhance attack efficacy.

### Implications
The findings raise concerns about instruction-tuned models' vulnerability to data leakage. The study calls for robust privacy safeguards in LLM training and instruction-tuning processes.

---

### Reference
Kassem, A. M., Mahmoud, O., Mireshghallah, N., et al. (2024). Using LLMs to Uncover Memorization in Instruction-Tuned Models. [Read the full paper](https://arxiv.org/abs/2403.04801).
