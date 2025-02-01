---
ShowToc: false
title: Style Transfer in Text - Exploration and Evaluation
date: "2025-01-22"
draft: false
summary: This paper explores text style transfer (TST) using non-parallel data, introducing new evaluation metrics for transfer strength and content preservation.
math: true
tags: [Text Style Transfer, NLG, NLP]
---
[Read the paper](https://ojs.aaai.org/index.php/AAAI/article/view/11330)

## Introduction
- This paper looks at the challenges of changing the style of text without using matching input-output examples.
- It introduces two new ways to measure performance:
  - **Transfer Strength:** How well the style is changed.
  - **Content Preservation:** How much of the original content is kept.
- The methods are tested on two tasks:
  - Turning academic paper titles into news-style titles.
  - Changing reviews from positive to negative.
- Results show the models balance changing style and keeping content well.

## Related Work
- The paper talks about earlier work on style transfer in images and text.
- It explains the difficulties in text style transfer, like not having matching input-output examples and lacking good evaluation methods.
- Different approaches, like adversarial networks and multi-task learning, are reviewed.
- The authors point out the need for better ways to keep content and separate style.

## Models
- Two models are proposed:
  - The **multi-decoder model**, which has separate decoders for each style.
  - The **style-embedding model**, which adds style information during generation.
- To test these models, two metrics are used:
  - **Transfer strength:** Measures how well the new style is applied.
  - **Content preservation:** Measures how much content stays the same.
- Tests on two datasets—paper-news titles and positive-negative reviews—show these models balance style change and content retention.
- The multi-decoder model focuses more on style change, while the style-embedding model keeps more content.
- Human evaluations show the content preservation metric aligns well with human opinions.

## Evaluation
- The models manage to change style while keeping content to varying levels.
- The new metrics (transfer strength and content preservation) match human evaluations well, proving their usefulness.
- The paper notes a trade-off between style change and content retention, suggesting different models for different tasks.

## Experiment
- Two datasets are used:
  - A **paper-news title dataset** with academic paper titles and their news-style versions.
  - A **positive-negative review dataset** with Amazon reviews labeled as positive or negative.
- The datasets were split into training, validation, and test sets.
- Preprocessing steps included:
  - Filtering sentence lengths.
  - Converting text to lowercase.
  - Replacing numbers with placeholders.
- Different settings were tested to ensure fair evaluation:
  - Word embedding size: Tried values like 64, 128, etc.
  - Encoder hidden size: Tested sizes like 16, 32, 64, 128.
  - Style embedding size: Checked 32, 64, 128 dimensions.
  - Batch size: Set to 128.
  - Optimizer: Used Adadelta with a learning rate of 0.0001.

## Results and Analysis
- The content preservation metric matched human opinions with a Spearman’s correlation of 0.5656 (p < 0.0001).
- In the paper-news title task:
  - The style-embedding model got content preservation scores of 0.89-0.95 and transfer strength scores of 0.2-0.6, better than the baseline.
- In the positive-negative review task:
  - The multi-decoder model got transfer strength of 0.8 and content preservation of 0.85, doing better than the style-embedding model, which scored 0.6 and 0.75.
- The multi-decoder model improved transfer strength by 50% compared to the auto-encoder in this task, reaching 0.6.
- Overall, the models improved style change and content retention by 20~50% compared to the baseline.
