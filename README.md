# Beyond Performance: Evaluating LLM Explanations and Errors in CrowdRE Requirement Classification

This repository contains the appendix and codes for the ISEC 2027 paper: "Beyond Performance: Evaluating LLM Explanations and Errors in CrowdRE Requirement Classification"

**Authors:** Uttam Kumar (IIT Patna), Vimaleswar A (IISER Bhopal), Arpit Sharma (IISER Bhopal)

**Abstract:**
Crowd-based Requirements Engineering (CrowdRE) leverages digital platforms to collect requirements from diverse stakeholders, but the resulting heterogeneous and unstructured data make manual classification labor-intensive and prone to errors. Although Large Language Models (LLMs) have shown promise for requirements classification, existing studies have largely emphasized aggregate classification performance, providing limited insight into explanation quality and underlying failure patterns reflected in model outputs. To address this gap, we systematically evaluate LLM-based CrowdRE sector classification by jointly examining classification performance, class separability, explanation quality, and reasoning failures. We evaluate four open-source LLMs using three prompting strategies across seven classification tasks, comprising Binary, Tertiary, and Quaternary tasks with high-F1 (HF1) and low-F1 (LF1) class combinations, and a Quinary task covering all five sectors. Classification performance is measured using Macro-F1, while generated explanations are evaluated using CTC, BERTScore, and ROUGE-L against verified reference explanations. The highest Macro-F1 of 92.64\% is achieved by Llama-3.3-70B with FSR on Binary HF1. Qwen2.5-72B achieves the highest CTC of 59.42\% and BERTScore of 74.64\% with FSR on Tertiary HF1, and the highest ROUGE-L of 46.93\% with EZS on the Binary HF1 task. Furthermore, explanation quality scores exhibit lesser reductions than classification performance as task granularity increases, indicating that the two capture distinct aspects of model behavior. Analysis of 879 misclassifications identifies Incorrect Logical Rule as the predominant error type, accounting for 68.37\% of errors, followed by Hallucination at 13.65\%, Decompositional Reasoning Failure at 10.69\%, and Surface Feature Reliance at 7.28\%. These findings highlight the importance of evaluating LLM-based requirements classification beyond label prediction by jointly considering explanation quality and underlying error patterns.


In short the study evaluates 4 open-source LLMs across multiple classification granularities and prompting strategies, with a joint analysis of:

- Sector classification performance
- Explanation quality
- Reasoning failures reflected in misclassified requirements



## Repository Structure

```text
.
├── Codes/
│   ├── dataset_gen.py
│   ├── experiment.py
│   ├── score.py
│   └── misclassified.py
│
├── dataset_gold/
│   ├── Experiment_dataset/
│   ├── Binary_dataset/
│   ├── Tertiary_dataset/
│   ├── Quaternary_dataset/
│   └── Quinary_dataset/
│
└── README.md

```

## Overview

The **`Codes/`** directory contains the scripts used for dataset generation, LLM inference, evaluation, and error analysis.

1. **`dataset_gen.py`** — Generates balanced Binary, Tertiary, Quaternary, and Quinary datasets using hierarchical sampling with a fixed random seed.  
2. **`experiment.py`** — Runs the LLM inference experiments across the selected datasets and prompting strategies and saves the generated classifications and explanations.  
3. **`score.py`** — Computes classification and explanation quality metrics, including Macro-F1, CTC, BERTScore, ROUGE-L, ROUGE-1, ROUGE-2 and METEOR, for the generated results.  
4. **`misclassified.py`** — Extracts misclassified requirements from prediction files and organizes them by true-predicted label pairs for explanation-driven error analysis.
