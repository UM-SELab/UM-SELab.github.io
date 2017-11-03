---
layout: post
title:  "Deep learning for Pharmaceutical Formulation Prediction"
date:   2017-11-01
categories: Pharmaceutics 
author: Yilong Yang, Zhuyifan Ye, Yan Su, Jing Jing, Xiaoshan Li, Defang Ouyang
---

Current pharmaceutical industry faces great pressure of reduced healthcare costs and less number of new active pharmaceutical ingredients (APIs). This means pharmaceutical industry should employ more efficient and systematic ways in both drug discovery and development processes.[1] In drug discovery area, scientists now widely use high-throughput screening, combinatorial chemistry, and computer-aided drug design to accelerate rapid drug discovery and development.[2] However, today formulation development still strongly relies on the traditional trial-and-error approach by individual experiences of pharmaceutical scientists, which is laborious, time-consuming and cost-expensive. Moreover, it is difficult to achieve optimum formulations by trial-and-error studies in the laboratory. Simplification of formulation development becomes essential to formulation scientists. Thus, it is necessary to develop an efficient and systematic method for formulation development to keep pace with the requirements of the pharmaceutical industry.[3] Deep learning as an automatic general-purpose learning procedure has widely adopted in many domains of science, business, and government [4]. Unlike the conventional machine learning techniques with required domain expertise to design a feature extractor, deep learning can automatically transform low-level representation to more abstract level [5]. Moreover, deep learning is more sensitive to irrelevant and particular minute variations, which make deep learning methods reach higher accuracy rather than the conventional machine learning methods [6]. In this paper, we aims to apply deep learning techniques for pharmaceutical formulation prediction. Three different types of pharmaceutical formulations were selected as the model systems, including solid dispersions (SD), oral fast disintegrating films (OFDF), and oral sustained release matrix tablets (SRMT). 

### Aim 
The aim of this research is to use deep learning to predict pharmaceutical formulations.

### Method  
In this paper, oral fast disintegrating films (OFDF), oral sustained release matrix tablets (SRMT) and solid dispersion (SD) were chosen as model systems for different types of dosage forms. Meanwhile, 100-200 failed or successful formulation data were extracted from Web of Science for each system. Different dataset selection methods were investigated. Deep learning with improved dataset selection algorithm can effectively predict the performance of formulations on small dataset with imbalanced input space.
{% include img.html url="md-fis.png" %}

### Results
One of the main difficulties in pharmaceutical prediction is the small dataset with imbalanced input space due to the limited experimental data. Evaluation criteria in pharmaceutics were applied to assessing the accuracies of the three feed forward neural network models. Moreover, Automatic dataset selection algorithm was developed for selecting the representative data to validation dataset. The accuracies of all three models were above 75%, which showed good prediction in pharmaceutical formulations. 

| Formulation | Training Set (%) | Validation Set (%) | Testing Set (%) |
|:-----------:|:----------------:|:------------------:|:---------------:|
|     OFDF    |       91.21      |        90.00       |      80.00      |
|     SRMT    |       81.13      |        75.00       |      75.00      |
|      SD     |       90.29      |        90.00       |      75.00      |


### Conclusion 
In summary, the deep learning with the dataset selection algorithm was firstly developed for the prediction of pharmaceutical formulations on small dataset. The proposed model could effectively predict the key parameters for formulation development, which could significantly decrease the development timeline and material usage of drug product. The cross-disciplinary integration of pharmaceutics and artificial intelligence may shift the paradigm of pharmaceutical researches from experience-dependent studies to data-driven methodology. 






