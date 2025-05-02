---
ShowToc: false
title: Real-Time E-commerce Analytics System
date: 2025-04-30
draft: false
summary: Built a modular real-time analytics platform using Kafka, Spark, Postgres, and Superset for live event ingestion and dashboarding.
math: true
---

## Description

This real-time analytics system ingests user interaction events from an e-commerce simulation, processes them using PySpark Structured Streaming, stores them in Postgres, and visualizes insights through Apache Superset. It supports modular, scalable ETL stages and enables near real-time monitoring of customer behaviors and event trends.

[Github Repo](https://github.com/gnehcuyz/Real-Time-E-commerce-Analytics-with-Spark-and-Kafka)

## Tech Stack
- Python, PostgreSQL, Docker, Apache Kafka, Apache Zookeeper, Apache Spark, Apache Superset.

## Contributions
- Streaming behavioral event data from a retail dataset using a custom **Kafka** producer, and develop **PySpark streaming** jobs to parse, transform, and structure the data into feature-rich records suitable for downstream analysis and modeling.
- Managing data persistence using **Postgres**, with optimized batch inserts and schema enforcement to ensure analytical readiness and data quality.
- Creating real-time dashboards in **Apache Superset** to visualize key metrics such as event volume, user activity patterns, and conversion-related behavior.
- Using **Docker Compose** to coordinate the full pipeline, enabling reproducible analytics workflows across containerized services.

