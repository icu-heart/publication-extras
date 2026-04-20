# Work Package 3 – The association of haemodynamic instability with organ-specific and longer-term outcomes  
**Leads:** Mohammad Kouli

**Additional:** Craig Nicolson, Rosalyn Pearson, Steph Burns, Sinziana Radulescu, Stella Prizeman-Green, Annemarie Docherty

## Aims & objectives 

### Aim: 
To quantify haemodynamic instability in combination with other patient factors to predict routinely collected organ-specific (delirium, Acute kidney injury (AKI), major adverse cardiac events (MACE)) and non-organ-specific (death, critical care support, longer term healthcare trajectories) outcomes in critically unwell patients.

### Objectives: 
1.	Determine the incidence, duration and severity of haemodynamic instability in critically ill patients using hourly validated physiological observations recorded in ICCA, along with high frequency Mindray waveform data. We will explore different thresholds for our parameters, and in different subgroups of patients, including critically ill patients with cardiovascular disease.  

2.	Determine the incidence of organ-specific outcomes including AKI, Delirium and MACE using routinely collected data within ICU.

3.	Explore the association of haemodynamic instability with organ-specific outcomes.

4.	Identify groups patients that are at higher risk of the above outcomes, and consider strategies to mitigate these risks.

5.	(Follow-on work with amendment to data application) Within a subset of patients we will ascertain if the addition of peri-operative physiological data from a wearable device (Wellcome LEAP SAVE, PI Ewen Harrison) improves risk prediction.  


## Methods 

### Design 
Retrospective cohort study. 

### Population
All patients admitted to ICU (118/116) in the Royal Infirmary of Edinburgh with an ICCA electronic patient record.

### Variables 
#### Variables/predictors 
Physiological variables contributing to haemodynamic instability:
Heart rate, heart rhythm, invasive blood pressure, oxygen saturations (related to inspired oxygen), end-tidal CO2 monitoring, respiratory rate, central temperature, haemoglobin concentration.

#### Other variables
##### Predisposing factors: 
age, ethnicity, sex, socioeconomic status (Scottish Index of Multiple Deprivation), comorbidities increasing risk of cardiovascular disease (e.g. hypertension, diabetes), multimorbidity (DL-2023-059 SMR Multimorbidity and end-organ dysfunction), frailty (electronic Frailty index), prior hospital admissions (number of prior admissions with cardiovascular diagnoses, number of prior emergency admissions). 
##### Precipitating factors: 
diagnosis on admission to hospital, diagnosis on admission to critical care, admission type (emergency vs planed), severity of illness on admission.  
##### Time-varying factors: 
transfusions, lab results (e.g. creatinine, lactate), organ support (eg invasive mechanical ventilation, vasopressor requirement), complications (e.g. new infection), cardiac events (e.g. new arrhythmia).  

#### Outcomes
Organ specific
* AKI: Urea, Creatinine, urine output, use of renal replacement therapy as per KDIGO guidelines
* Delirium: CAM-ICU positive, RASS, use of anti-psychotic medication including haloperidol, quetiapine, trazadone
* Major Adverse Cardiac Events (MACE): myocardial infarction, stroke, heart failure, coronary artery revascularisation, cardiovascular mortality.

Non-organ specific
* All-cause mortality
* Organ support
* Longer term healthcare trajectories

### Data sources 
The specific data sources are detailed in Table 1 of the overall application (found at the end of section D) and in the Data Selection Form.    

### Data management 
Data for this project will reside in the NHS Lothian safe-haven DataLoch and will be acquired from a range of data sources outlined above.   

### Analysis
#### Prepare data: clean and remove noise
* Downsample ICCA Clinical and hourly validated monitoring data and MindRay Waveform data to provide minute by minute summary measure physiological data.
* Carry out data wrangling, data cleaning (including application of in-house artifact detection methods) and exploratory data analysis using R/Python to summarise and characterise the different data: raw physiological data; required ICCA clinical data; and data obtained from DataLoch sources prior to modelling. 
* Identify missing data and input where possible or impute if required.

#### Characterise haemodynamic instability
* Create features that represent the characteristics of haemodynamic instability: Heart rate, heart rhythm, invasive blood pressure, oxygen saturations (related to inspired oxygen), end-tidal CO2 monitoring, respiratory rate, central temperature, haemoglobin concentration.
* Extract features at different time points
* Construct summary measures such as number, and duration of instability (relative to total monitoring time) and area under the curve measures such as pressure time index (PTI)  
* Using these features and summary measures, determine the incidence, duration and severity of haemodynamic instability
* Explore different thresholds for parameters, and in different subgroups of patients, including critically ill patients with cardiovascular disease.  

#### Determine incidence of organ specific outcomes
* Use routinely collected data within ICU (ICCA) to determine the incidence of organ-specific outcomes in the cohort

#### Evaluate association of haemodynamic instability with organ-specific outcomes
* Explore a range of models including logistic regression, random forest, and gradient boosting machines (XGBoost). 
* Once the dataset is of an adequate size, consider time series techniques such as recurrent neural networks and dynamic time warping. 
* For all models, split the dataset into training and internal validation sets. Deploy k-fold cross validation methodologies to prevent overfitting. Evaluate model performance on the validation set using appropriate classification and regression metrics. Consider techniques such as SHAP and LIME to aid clinical interpretability.

#### Identify high-risk patients
* Using the developed model, identify groups patients that are at higher risk of the above outcomes
* Consider strategies to mitigate these risks

#### Validate model
We aim to externally validate this model in an ICU dataset from NHS Greater Glasgow and Clyde Health board.


