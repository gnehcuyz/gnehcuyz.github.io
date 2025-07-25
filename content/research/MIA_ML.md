---
ShowToc: false
title: Membership Inference Attacks for Machine Learning Models
date: 2025-01-08
draft: false
summary: Analyzed ML vulnerabilities with pipelines, metrics, and visualizations.
math: true
slug: "mia-ml"
url: "/research/mia-ml/"
---

## Description
I conducted research on privacy vulnerabilities in machine learning models by implementing membership inference attacks (MIAs) to evaluate their reliability and disparities. Our study revealed that different MIA methods—and even repeated runs of the same method—can yield inconsistent results, raising concerns about their robustness. To address this, we proposed a systematic evaluation framework based on coverage and stability metrics, and introduced ensemble strategies to improve the accuracy and consistency of attack results. 

This work culminated in the paper [*Membership Inference Attacks as Privacy Tools: Reliability, Disparity, and Ensemble*](https://arxiv.org/abs/2506.13972v2), which has been accepted by ***ACM CCS 2025***.

## Tech Stack
- Python, NumPy, Matplotlib.

## Contributions
- Built **data pipelines** for processing attack predictions across multiple seeds.
- Created **visualizations**, including Venn diagrams and upset diagrams, to identify patterns and disparities in attack outcomes.
- Automated **data processing** workflows with Shell Scripts to handle large datasets.
- Calculated metrics such as Jaccard similarity, set variance, and entropy for reliability analysis.


## Supervisor: 
Professor [Lei Yu](https://leiyucs.github.io)

