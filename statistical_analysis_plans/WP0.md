# Work Package 0 - Defining multimorbidity in critical care admissions and its impact on care processes, care transitions  and outcomes
(DataLoch Project Reference DL_2023_059)

**Leads:** Sinziana Radulescu

**Additional:** Stella Prizeman-Green, Craig Nicolson, Rosalyn Pearson, Steph Burns, Mohammad Kouli, Sinziana Radulescu, Annemarie Docherty
 
## Aims and objectives 

1) What is the interplay between pre-disposing factors, such as multimorbidity, polypharmacy,
and frailty, precipitating factors such as diagnosis and illness severity, treatments and 
outcomes in patients admitted to critical care?
    1. Can distinct patient clusters be derived based on the pre-disposing and precipitating factors?
    2. What is the effect of these distinct clusters, subsequently mediated by treatments, on
organ dysfunction?
    3. Can prediction modelling enhance our understanding of the influence the previously
identified clusters exert on end-organ dysfunction, care-transitions and long-term outcomes in ICU
patients?

2) Can the application of causal inference methods from ICU observational data, such as target
trial emulation, explore the impact of various treatment strategies in the different patient
clusters identified.

## Methods

### Design
Cohort study

### Study population, setting
All critical care admissions from 01/01/2013 to 31/12/2022 in NHS Lothian Critical Care Units aged 18 and older, defined from Wardwatcher. 

### Variables

#### Predictors
Pre-disposing factors will include multimorbidity, frailty and polypharmacy. 

* Multimorbidity will be defined using existing definitions, such as Elixhauser, Charlson and the HDR-UK Caliber phenotypes. 
* Frailty will be defined from the electronic Frailty index (EFI) and the clinical frailty score in the SICSAG dataset. The EFI will be evaluated as a continuous measure as well as in the following recognised categories: fit (a score below 0.12), mildly frail (0.12 to 0.24), moderately frail (0.24 to 0.36), or severely frail (0.36 and above). 
* Polypharmacy will be defined using community prescribing data (PIS) for the 90-day period before admission.

Other variables will include: 

* Demographics: age at presentation, sex, deprivation (as measured by SIMD), ethnicity
* Previous health care resource use: previous hospital admissions (including diagnosis on admission; admission type), previous ED attendances (including diagnosis on attendance), previous outpatient attendance (including specialty).
* Acute illness features: ED and hospital diagnoses, time to ICU admission, care transitions before ICU Admission, ICU admission diagnosis, severity of illness, daily organ support, daily organ dysfunction (derived from Trak labs and WW), laboratory test results, admission source and discharge destination, care transitions after discharge.

#### Outcomes
Primary:

* 30 day mortality

Other outcomes: 

* Mortality: ICU, hospital, 90 day, 1 year, 5 year; (WW, SMR01, NRS deaths)
* Hospital readmission: 30d, 90d, 1 year, 5 year. (SMR01)
* Hospital resource use (SMR01, SMR00)
* Care transitions (Trak, SMR01)
* Complications: e.g. cardiovascular outcomes (SMR01, primary care, NRS deaths, Trak labs), hospital associated infection (defined from Wardwatcher)


### Data sources

Data sources will be: Trak ED, Trak inpatients, Trak labs, NRS Deaths, SMR01, SMR00, Dataloch-defined datasets used to derive Caliber comorbidities (including primary care) and eFI, Wardwatcher, PIS.

### Analysis
We will examine baseline characteristics and summarise these as follows: mean and standard deviation (SD) ore median (interquartile range) will be provided for continuous variables, and count (n) and percentage (%) for categorical variables. To examine differences between multimorbidity and health outcomes, ANOVA/Kruskall-Wallis will be used for continuous variables and chi-squared will be used for categorical variables. 

#### Clustering
We will use methods such as latent class analysis (LCA) to identify and identify clusters of multimorbidity, frailty and polypharmacy.  

We will compare the following characteristics between clusters:
* Demographics 
* Healthcare resource use trajectories 
* Acute illness features and patterns of organ dysfunction 
* Other outcomes such as mortality, hospital readmission and complications

#### Prediction modelling
We will use prediction modelling to identify those at highest risk of the following outcomes:
* Mortality: ICU, hospital, 90 day, 1 year, 5 year
* Hospital readmission: 30d, 90d, 1 year, 5 year
* Hospital resource use 
* Care transitions 
* Complications: e.g. cardiovascular outcomes, hospital associated infection 

We will report appropriate metrics for model performance and model fit e.g. discrimination, calibration, classification indices. Modelling methods will include: logistic regression (or other GLMs and Cox models (cause-specific where there is a competing risk of death)).
	
To identify groups of patients with similar care pathways, we will use a previously reported method (Grant RW, , et al. JAMA Netw Open. 2020;3(12):e2029068.) which uses a combination of clinical expertise and clustering methods (latent class analysis and K-means clustering) to firstly reduce the complexity of the data and secondly identify groups of patients with similar care pathways. We will compare clusters among patients with and without multimorbidity, can determine clinical relevance of clusters by evaluating outcomes for each pathway. 

#### Missing data
Missing data will be evaluated and multiple imputation of all missing data using chained equations will be performed if appropriate. 

#### Bias 
In order to minimise bias, we will aim to adjust for variables identified as potential confounders, such as: 
* Age, sex, ethnicity, SIMD 
* COVID-19 status or COVID-19 period 

We will stratify patients by the COVID-19 period, examine the baseline characteristics, and perform sensitivity analysis. Moreover, we will include a COVID-19 period variable in our statistical models, to help adjust for the COVID period specific effects. We will also consider performing propensity score matching for COVID-19 versus non-COVID-19 period patients. 

#### Target trial emulation 
We aim to use causal inference methods that involve simulating a randomized trial from observational data. Note that the trial emulation component will require additional variables and detailed methods, which will be submitted as an amendment as the PhD progresses (expected: within 12 months).



