---
ShowToc: false
title: Label Inference Attacks in Federated Learning
date: 2024-12-22
draft: false
summary: Optimized label attacks and assessed risks in federated learning.
math: true
slug: "lia-fl"
url: "/research/lia-fl/"
---

## Description
We investigated privacy risks in vertical federated learning (VFL), with a primary focus on Direct Label Inference Attacks—a technique that exploits the mathematical properties of gradient signs to infer sensitive label information without model splitting. Demonstrated that this attack can achieve perfect accuracy across various datasets, underscoring critical vulnerabilities in current federated learning frameworks.

## Tech Stack
- Python, PyTorch, NumPy, Scikit-learn.

## Contributions
- Implemented a Direct Label Inference Attack by analyzing gradient signs and demonstrated its effectiveness in exposing label leakage.
- Preprocessed and aligned multi-party datasets to simulate vertical federated learning scenarios.
- Analyzed gradient-based leakage and tested privacy defense strategies such as gradient compression and DiscreteSGD.

## Supervisor: 
Professor [Oshani Seneviratne](https://oshani.info)