# Task Order Matters: Deep Learning Pipelines for Breast Ultrasound Diagnosis

**A comparative Applied AI project that studies how the order of segmentation and classification changes performance, robustness, and clinical interpretability in breast ultrasound analysis.**

## Overview
This repository contains the final project for the *Applied AI in Biomedicine* course (Politecnico di Milano).  
The work compares two end-to-end diagnostic strategies on the public BUSI breast ultrasound dataset:

- **Pipeline A (Classification → Segmentation)**
- **Pipeline B (Segmentation → Classification)**

The goal is to understand how task ordering affects:
- diagnostic accuracy,
- lesion delineation quality,
- and error propagation between stages.

## Repository Contents
- `/Classificazione_Segmentazione.ipynb`  
  Pipeline A notebook: full-image classification first, lesion segmentation second, plus unified evaluation.

- `/Segmentazione_Classificazione.ipynb`  
  Pipeline B notebook: lesion segmentation first, ROI-based benign/malignant classification second, plus unified evaluation.

- `/Report.pdf`  
  Full project report with methodology, experiments, quantitative/qualitative results, comparative analysis, and references.

## Methods at a Glance
- **Classifier:** EfficientNet-B7 (fine-tuned, weighted loss for class imbalance)
- **Segmenter:** U-Net++ (Dice/Focal/Lovasz hybrid loss)
- **Data split:** patient-wise split to reduce leakage
- **Metrics:** balanced accuracy, macro F1, Dice, IoU, sensitivity/specificity
- **Interpretability:** Grad-CAM analysis for clinical plausibility

## Key Findings
- Task ordering is a critical design choice in ultrasound CAD pipelines.
- The two pipelines show complementary strengths:
  - one is generally stronger for diagnostic discrimination,
  - the other is stronger for lesion localisation quality.
- Error propagation differs by design: classification errors can suppress downstream segmentation, while segmentation errors can degrade ROI-based classification.

## Dataset and Context
The experiments are based on the BUSI dataset (breast ultrasound images with masks and labels: normal, benign, malignant), as documented in `Report.pdf`.

## Authors
Filippo Saccomano, Daniele Uras, Gabriele Carta, Jonny A. Marques
