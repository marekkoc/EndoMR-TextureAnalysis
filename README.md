# EndoMR-TextureAnalysis
A repository for texture-based analysis of MR images in endometrial carcinoma classification. Implements extraction of texture features from pharmacokinetic parameter maps derived from DCE-MRI, ADC, and VIBE modalities. Includes tools for supervised and unsupervised classification to aid in tumor grading and characterization.



Oto rozszerzona wersja opisu repozytorium:

# EndoMR-TextureAnalysis

## Overview
This repository contains comprehensive tools and algorithms for advanced texture analysis of multimodal MR images in endometrial carcinoma classification and characterization. The approach is based on a research study that evaluated texture parameters computed from blood pharmacokinetic maps derived from DCE-MRI as potential biomarkers for cancer characterization and grading.

## Background and Motivation
Endometrial cancer is the most common pelvic gynecological malignancy in high-income countries with increasing incidence. Current preoperative assessment methods have limitations in accuracy and reproducibility, creating a need for improved imaging-based techniques.

The method analyzes various MRI modalities including:
- Dynamic Contrast-Enhanced (DCE) MRI parameter maps (p₁, p₃, p₄, t₀)
- Apparent Diffusion Coefficient (ADC) maps
- T1-weighted VIBE (Volumetric Interpolated Breath-hold Examination) images

Our computational approach extracts texture features from these images and applies both unsupervised clustering and supervised classification (LDA) to correlate image features with histological tumor grades, providing potential biomarkers for non-invasive tumor assessment.

## Key Features
- **Image Preprocessing Pipeline**: Tools for converting DICOM to NIFTI format, image registration, and ROI extraction
- **Pharmacokinetic Modeling**: Implementation of 6-parameter model for DCE-MRI signal analysis:
  - p₀: Signal baseline
  - p₁: Response amplitude
  - p₂: Transition slope
  - p₃: Exponential signal decrease
  - p₄: Initial signal increase
  - t₀: Bolus arrival time
- **Texture Analysis**: Extraction of 300+ texture features using:
  - Co-occurrence matrices
  - Run-length matrices
  - Gradient features
  - Wavelet-based features
- **Feature Selection**: Algorithms based on:
  - Fisher coefficient (F)
  - Mutual information (MI)
  - Classification error minimization (P)
- **Classification Methods**:
  - Supervised: Linear Discriminant Analysis (LDA), k-Nearest Neighbor
  - Unsupervised: k-means clustering
- **Visualization Tools**:
  - Parameter maps visualization
  - Texture feature visualization
  - Clustering results
  - Classification performance metrics

## Experimental Results
Initial experiments demonstrate that texture features—particularly from parameter p₃ and ADC maps—provide promising discrimination between different grades of endometrial carcinoma. The p₃ texture map provided the best discrimination (resubstitution error: 2/14, cross-validation error: 3/14), with ADC, p₁, and VIBE also showing good performance.

## Potential Applications
- Preoperative grade prediction in endometrial carcinoma
- Non-invasive tumor characterization
- Personalized treatment planning
- Integration into clinical decision support systems
- Research platform for exploring correlations between MRI texture features and histopathology
- Methodology transferable to other tumor types

## Dependencies
- Python 3.7+
- SimpleITK
- scikit-learn
- MATLAB (for some legacy components)
- ITK-SNAP
- MaZda texture analysis software

## Future Work
- Deep learning-based feature extraction
- Radiomics analysis integration
- Multiparametric scoring systems
- Clinical validation studies
- Extension to other gynecological cancers
