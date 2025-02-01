---
ShowToc: false
title: Membership Inference Attacks Against NLP Classification Models
date: "2023-09-19"
draft: false
summary: A comprehensive analysis of privacy risks in NLP classification models, focusing on membership inference attacks (MIAs) at both sample and user levels.
math: true
tags: [Membership Inference Attack, NLP]
---

### Overview
This paper addresses privacy concerns in NLP classification models, focusing on how these models can leak private information through Membership Inference Attacks (MIAs). It explores both **sample-level MIAs** and introduces **user-level MIAs**, demonstrating the latter's stronger privacy risks due to aggregated data features.

### Contributions
The study makes three key contributions:
1. A systematic analysis of privacy risks in NLP classification models.
2. A suite of MIA methods for sample-level and novel user-level inferences.
3. Experimental results showcasing user-level MIAs' heightened accuracy (up to 25% better than sample-level MIAs).

### Methodology
#### Sample-Level MIAs
These attacks infer if a single data sample was part of the model's training data. Features such as cross-entropy loss, rank, and confidence are used, with a threshold distinguishing members from non-members.

#### User-Level MIAs
Unlike sample-level, user-level MIAs aggregate information from multiple samples tied to a user. This study proposed three types:
- **Threshold-based:** Using average statistics of user data features.
- **Learning-based:** Leveraging machine learning models trained on aggregated user features.
- **Sample-to-user-level:** Combining individual sample predictions to infer user membership.

### Experimental Findings
Using datasets like Reddit and Amazon reviews, the experiments highlight:
- User-level MIAs are more effective than sample-level, especially with Transformer-based models like BERT.
- Privacy risks increase with more classes, larger vocabularies, and longer token sequences.
- User contributions across multiple data classes increase their susceptibility.

### Implications
The research emphasizes the need for stronger privacy measures in NLP models, as current practices are insufficient to prevent MIAs. Future directions include:
- Auditing data collection processes using MIAs.
- Developing text perturbation methods to mitigate privacy risks.


### Reference
Shejwalkar, V., Inan, H. A., Houmansadr, A., & Sim, R. (2021). Membership Inference Attacks Against NLP Classification Models. *Proceedings of the 35th Conference on Neural Information Processing Systems (NeurIPS 2021)*. [Read the full paper](https://arxiv.org/abs/2111.07960).
