
# EndoMR-TextureAnalysis
A repository for texture-based analysis of MR images in endometrial carcinoma classification. Implements extraction of texture features from pharmacokinetic parameter maps derived from DCE-MRI, ADC, and VIBE modalities. Includes tools for supervised and unsupervised classification to aid in tumor grading and characterization.

## Overview
This repository contains tools and algorithms for texture analysis of MR images for endometrial carcinoma classification. The approach is based on a research study that evaluated texture parameters computed from blood pharmacokinetic maps derived from DCE-MRI as potential biomarkers for cancer characterization.

## Background
The method analyzes various MRI modalities including:
- Dynamic Contrast-Enhanced (DCE) MRI parameter maps (p₁, p₃, p₄, t₀)
- Apparent Diffusion Coefficient (ADC) maps
- T1-weighted VIBE images

Our computational approach extracts texture features from these images and applies both unsupervised clustering and supervised classification (LDA) to correlate image features with histological tumor grades.

## Study Design
The research was conducted on data from 14 endometrial carcinoma patients with histologically verified diagnosis. Each patient's dataset contained six different image types: four pharmacokinetic parameter maps derived from DCE-MRI signal modeling, and two conventional MR images (ADC and VIBE). The histological grade provided by pathologists after tumor extraction served as ground truth for supervised learning experiments.

## Methodology
1. **Image Acquisition**: 
   - 1.5T MRI system (Siemens Avanto)
   - VIBE: 192×192 matrix, 48 slices, 1.3×1.3×2.0 mm³ voxels
   - DCE-MRI: 256×256 matrix, 12 slices, 1.17×1.17×5.0 mm³ voxels, 160 volumes at 2.49s intervals
   - DWI: 128×128 matrix, 20 slices, 2.34×2.34×6.0 mm³ voxels
  
   <table align="center">
     <tr>
       <td><img src="figs/fig1a.png" alt="Results 1"></td>
       <td><img src="figs/fig1b.png" alt="Results 2"></td>
     </tr>
     <tr>
       <td align="center"><i><span style="font-size:smaller;">a)</span></i></td>
       <td align="center"><i><span style="font-size:smaller;">b)</span></i></td>
     </tr>
   </table>

  


2. **Signal Modeling**:
   - 6-parameter pharmacokinetic model fitted to DCE-MRI time courses
   - Parameters include signal baseline (p₀), amplitude (p₁), transition slope (p₂), decay rate (p₃), initial rise (p₄), and bolus arrival time (t₀)
  
     <table align="center">
     <tr>
       <td><img src="figs/results1.png" alt="Results 1"></td>
       <td><img src="figs/results2.png" alt="Results 2"></td>
     </tr>
     <tr>
       <td align="center"><i><span style="font-size:smaller;">Fig. 1: Analysis window</span></i></td>
       <td align="center"><i><span style="font-size:smaller;">Fig. 2: Parameter maps</span></i></td>
     </tr>
   </table>

3. **Texture Analysis**:
   - Approximately 300 texture features computed using MaZda software
   - Features derived from parameter distributions within ROIs marked by radiologists
   - Feature selection using Fisher coefficient, mutual information, and classification error minimization

4. **Classification and Clustering**:
   - Linear Discriminant Analysis for supervised grade classification
   - k-means clustering for unsupervised tissue characterization
   - Evaluation using resubstitution and leave-one-out cross-validation errors

## Key Results
- Parameter p₃ texture map showed best discrimination between carcinoma grades (resubstitution error: 14.3%, cross-validation error: 21.4%)
- ADC maps also demonstrated good classification performance
- Well-separated clusters in unsupervised analysis confirmed information content in texture features
- Colored visualization of clustering results was assessed as useful by radiologists for anatomical and pathophysiological exploration

## Potential Applications
- Preoperative assessment of endometrial carcinoma grade
- Non-invasive tumor characterization
- Support for surgical therapy planning
- Potential transferability to other tumor systems
- Contribution to personalized modeling of human blood-vessel systems in cancer

## Limitations
- Small sample size (pilot study with 14 patients)
- Need for validation on larger datasets
- Manual ROI selection requiring expert knowledge
