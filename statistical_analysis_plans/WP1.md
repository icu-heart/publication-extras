# Work Package 1 – Ethical application of machine learning to improve risk prediction in ICU patients with cardiovascular disease
**Leads:** Stella Prizeman-Green

**Additional:** Craig Nicolson, Rosalyn Pearson, Steph Burns, Mohammad Kouli, Sinziana Radulescu, Annemarie Docherty
 
## Aims & objectives
### Aim 1: Prediction
To investigate how accounting for dynamic changes across the patient stay can be used to improve upon static baseline risk prediction of mortality among critical care patients with cardiovascular disease. 

#### Objectives
* Develop baseline prediction models of mortality among Boston (MIMIC IV [1]) critical care patients with cardiovascular disease using features measured at time of admission to critical care as input. 
* Develop prediction models including time-varying features measured across the patient stay as input.
* Compare model performance between static and time varying risk prediction. 
* Externally validate best performing model in Lothian critical care population. 

### Aim 2: Causal inference
To develop baseline causal models for estimating the average treatment effect of different transfusion thresholds on mortality among cardiovascular critical care patients, and to investigate whether these models can be improved upon by accounting for time-varying confounding across the patient stay. 

#### Objectives
* Develop a causal estimate of the average treatment effect of different transfusion thresholds at admission on mortality among Boston (MIMIC IV) critical care patients with cardiovascular disease, based on features measured at time of admission to critical care. 
* Develop a model estimating the treatment effect of different transfusion strategies across the patient stay, taking account of treatment-affected time-varying confounding in addition to static features measured on admission. 
* Compare models in terms of mapping to real-world causal structure, including sensitivity analyses to assess accuracy of estimates.  
* Repeat analyses in Lothian critical care population, including re-evaluation of differing causal structure between different settings. 

## Methods

### Design
Retrospective cohort study. 

### Study population and setting
Models will be tested in two populations, with one acting as a baseline population for initial model development, and another being used for external validation (Aim 1 – prediction) and repetition of findings (Aim 2 – causal inference):  
	 
1.	Baseline: all adults with cardiovascular disease admitted to critical care at the Beth Israel Deaconess Medical Center, Boston, 2008 – 2022 (MIMIC-IV).
2.	External validation & findings repetition: all adults with cardiovascular disease in NHS Lothian ICU population as per overall application.

Cardiovascular disease will be defined based on work currently ongoing within the group (WP0 SMR Multimorbidity and end-organ dysfunction) testing definitions from different sources to identify the definition with the best discrimination. 

### Variables

Note: the same variables will be used for both analyses, however treated differently as input features in the predictive context of Aim 1 and as exposures, mediators and confounders in the causal context of Aim 2. For clarity of presentation these will be described as input features below, with the key exposure in causal analyses noted.  
Input features
In baseline models, input features will be measured at time of admission to critical care only. In time-varying models, changing values during the patient stay will be included. While all features can vary over time, they have been grouped below according to whether values are anticipated to change during the course of the index admission. 

Consistent across admission:
Predisposing factors:  
-	Demographics: age, ethnicity, sex, socioeconomic status (Scottish Index of Multiple Deprivation) 
-	Comorbidities increasing risk of cardiovascular disease (e.g. hypertension, diabetes) and multimorbidity, as identified in WP0. Comorbidities identified using HDR-UK Caliber phenotypes and primary care records in Lothian dataset. 
-	Frailty, defined by electronic frailty index in Lothian dataset, treated as a continuous variable. 
-	Prior admissions: number of prior admissions with cardiovascular diagnoses, number of prior emergency admissions (categorised as 0, 1-3, 4+)

Precipitating factors: 
-	Diagnosis at hospital & critical care admission 
-	Type of critical care admission (emergency vs planned)
-	Severity of illness at critical care admission 

Variable across admission: 
-	Transfusions (treated as exposure of interest for causal models in Aim 2) 
-	Lab results (e.g. haemoglobin, markers of renal function)  
-	Daily organ support 
-	Physiological variables (e.g. heart rate, blood pressure) 
-	Complications (e.g. new infection) 
-	Cardiac events (e.g. new arrhythmia, myocardial infarction)

### Outcomes 

Mortality (including time and cause of death), adverse cardiac events.

### Data sources
The specific data sources are detailed in Table 1 of the overall application (found at the end of section D) and in the Data Selection Form.

## Analysis

Given the use of the same populations and datasets, some analytical elements will be shared by both aims. 

### Baseline characteristics
Building on work currently ongoing in the research group (WP0), the population of patients with cardiovascular disease will be selected based on the definition giving the best discrimination in the critical care population. Baseline characteristics summarising differences between this group and the rest of the critical care population will be reported.  

Continuous variables will be reported as mean and standard deviation where variables are normally distributed, else median and interquartile range. Categorical variables will be summarised with count and percentage. Two-sided p-values will be reported, using ANOVA or Kruskall-Wallis tests for continuous and chi-squared test for categorical variables. 

### Missing data

Missing data will be explored and handled based on patterns in missingness. For variables containing data missing at random, missing data will be imputed using multiple chained equations, otherwise missing data will be treated as its own category.

### Bias

The impact of selection bias deriving from critical care admission practices will be assessed and compared between both populations, for which admission practices are notably different. To reduce the impact of poor model calibration in groups underrepresented in the target population (e.g. ethnicities, ages), bias-mitigation approaches such as oversampling of underrepresented groups will be explored. 


### Aim 1: Prediction

Models such as logistic regression, tree-based models and neural networks will be tested, initially using only features measured on admission to critical care. Particular attention will be paid to survival analysis (both statistical and deep methods, e.g. those detailed in [2]). The most successful models will then be extended to incorporate full time-varying data, both features and effects. Performance metrics will be reported for model comparison, including discrimination (ROC/c-statistic) and calibration (calibration curves). Model interpretability will be considered during model selection, including the use of post-hoc explainability techniques (e.g. SHAP, LIME). The selected model will be externally validated in the Lothian critical care population. 

### Aim 2: Causal inference

Directed acyclic graphs (DAGs) will be developed based on expert clinical knowledge to represent the assumed underlying causal relationships between the primary exposure of interest (transfusion thresholds), the outcome (mortality in critical care), and possible mediators or confounders. In baseline analyses only factors measured at time of admission to critical care will be included, with propensity scores calculated using inverse probability weighting to estimate the average treatment effect from time of admission. In time-varying analyses DAGs will be re-formulated to include the effect of features over time, with methods such as the parametric g-formula and marginal structural models used to estimate the joint effect of the exposure over time. 

To assess the impact of unobserved confounding in the estimates, sensitivity analyses using negative control exposures and outcomes will be conducted. Data-driven methods for DAG derivation will also be tested with effects re-estimated as a sensitivity analysis. Analyses will be repeated in the Lothian population, with DAGs re-evaluated in context of the new clinical setting. 

## Citations 
1. 	Johnson AEW, Bulgarelli L, Shen L, et al (2023) MIMIC-IV, a freely accessible electronic health record dataset. Sci Data 10:1. https://doi.org/10.1038/s41597-022-01899-x
2. 	Wiegrebe S, Kopper P, Sonabend R, et al (2024) Deep learning for survival analysis: a review. Artif Intell Rev 57:65. https://doi.org/10.1007/s10462-023-10681-3
 
