---
ShowToc: false
title: Practical Membership Inference Attacks Against Large-Scale Multi-Modal Models - A Pilot Study
date: "2024-01-24"
draft: false
summary: An investigation of membership inference attacks (MIAs) targeting large-scale multi-modal models like CLIP, introducing practical attack strategies without shadow training.
math: true
tags: [Membership Inference Attack, Multi-Modal Model]
---

### Overview
This paper explores privacy risks in large-scale multi-modal models, such as CLIP, focusing on Membership Inference Attacks (MIAs). These attacks identify whether a data point was used in model training, revealing potential privacy vulnerabilities. The study develops practical strategies to perform MIAs without shadow training, addressing computational challenges in large-scale models.

### Contributions
The study introduces three key MIA strategies:
1. **Cosine Similarity Attack (CSA):** A baseline method using cosine similarity between image and text features.
2. **Augmentation-Enhanced Attack (AEA):** Improves CSA by aggregating cosine similarity changes across data transformations.
3. **Weakly Supervised Attack (WSA):** Leverages non-member data (e.g., data created after the model's training) to enhance attack accuracy.

### Methodology
#### Cosine Similarity Attack (CSA)
This attack predicts membership based on cosine similarity scores, which are higher for training data due to the model's optimization during training.

#### Augmentation-Enhanced Attack (AEA)
Enhances CSA by applying transformations (e.g., cropping, rotation) to inputs and measuring the resulting changes in cosine similarity. Members exhibit larger decreases in similarity than non-members.

#### Weakly Supervised Attack (WSA)
Uses a set of guaranteed non-members (e.g., data from after the model’s publication) to estimate membership distributions. This method identifies "pseudo-members" and trains an attack model for improved inference accuracy.

### Experimental Findings
- **Datasets:** Experiments used datasets like LAION, CC12M, and MSCOCO, combining large-scale web-scraped data for evaluation.
- **Performance:** WSA showed the best results, improving membership accuracy by 17% over CSA and achieving seven times better accuracy at low false-positive rates.
- **Insights:** Multi-modal models are more vulnerable to MIAs than previously assumed, with larger models (e.g., ViT-L/14) exhibiting more significant privacy risks.

### Implications
The findings highlight the need for privacy-preserving measures in large-scale multi-modal models. Future research directions include:
- Developing efficient privacy defenses for multi-modal systems.
- Extending the proposed attacks to other foundational models like GPT-3 and BERT.

---

### Reference
Ko, M., Jin, M., Wang, C., & Jia, R. (2023). Practical Membership Inference Attacks Against Large-Scale Multi-Modal Models: A Pilot Study. [Read the full paper](https://arxiv.org/abs/2310.00108).
