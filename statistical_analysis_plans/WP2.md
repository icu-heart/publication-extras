# Work Package 2 – Identifying myocardial infarction using artificial intelligence methods applied to routine continuous cardiac monitoring  

**Leads:** Craig Nicolson, Rosalyn Pearson

**Additional:** Steph Burns, Mohammad Kouli, Sinziana Radulescu, Stella Prizeman-Green, Annemarie Docherty

## Aims & objectives
### Aim
What is the incidence of myocardial infarction (MI) determined using artificial intelligence (AI) methods applied to routine continuous cardiac monitoring?
#### Objectives
* Assemble retrospective continuous cardiac monitoring data 
* Remove/deal with artefact in data  
* Validate use of 5-lead ECG when compared to 12-lead ECG for detection of ischaemia
* Identify MI in continuous cardiac monitoring  

## Methods
### Design
Retrospective cohort study

### Study population and setting
This study will focus on two cohorts with distinct purposes:
1.	All cardiology admissions (Royal Infirmary Edinburgh (RIE) 114, RIE 103) of adults.
2.	All intensive care admissions (RIE 118, RIE 116D) of adults.

### Variables

#### Predictors
* Continuous cardiac monitoring: 3 lead ECG, arterial blood pressure from hospital Mindray monitors
* Episodic 12 lead ECG: XML export and pre-derived waveform features from MUSE ECG machines
Other variables
* Hourly e-record data from ICCA: demographics; physiological; continuous drugs (i.e. inotropes/vasopressors); intermittent drugs
* Admission diagnosis: from Wardwatcher
* Lab biomarker data: Troponin T, creatinine, NSE, potassium etc. From Apex/iLabs
* Comorbidity information: label for cardiovascular disease derived from SMR01, Wardwatcher and Primary Care. Multimorbidity as identified in work package 1.
* Bedspace occupation: from Wardwatcher
* Admission and discharge dates: from ICCA/SMR01

#### Outcomes
Incidence of identified myocardial infarction 

### Data sources
The specific data sources are detailed in Table 1 of the overall application (found at the end of section D) and in the Data Selection Form.  

### Data management
Data for this project will reside in the NHS Lothian safe-haven (DataLoch) and will be acquired from a range of data sources outlined above.  

## Analysis

### Data preparation, cleaning and noise removal
The Mindray waveform data will be received in as a SQLite AtriumDB instance, unpacked from raw HL7 and pseudonymised by DataLoch. We will then carry out checks for data quality and completeness, before cleaning the data and removing noise (e.g. power line interference and baseline wander) via filtering techniques in the frequency (Butterworth filter, notch filter, Fourier transform) and/or mixed time-frequency (discrete wavelet transform) domains. 

### Segmentation of data
Data will be split into segments, e.g. 10 second windows

### Addressing artefacts in the data
Waveform artefacts are regions of data affected by confounding external factors, such as washing or moving the patient, or taking blood tests. This alters the underlying waveform and will interfere with model development. Statistical methods will be developed to identify (and classify) segments including artefacts and they will be discarded.

### Feature extraction
A range of features and feature extraction techniques will be explored, including
* Morphological features of the waveform (locations and amplitudes of PQRST, areas, slopes, skew and kurtosis), with special attention given to the ST segment, which is known to be indicative of ischaemia
* Statistical signal features such as power, mean, variance and higher order statistics as well as measures of complexity like entropy, Lyapunov exponents and autocorrelation
* Measures of heart rate variability: the RR interval and derivatives
* Frequency information from the power spectrum and wavelet filter banks
* Wavelet transform (for simultaneous time-frequency information): either specific coefficients from discrete wavelet transform or spectrograms from continuous wavelet transform
* Signal decomposition and extraction of eigenvalues (principal components analysis, independent components analysis, empirical mode decomposition)
* Deep features from machine learning, e.g. autoencoder latent space or use of convolutional or recurrent neural networks

### Validation of 5-lead ECG for detection of ischaemia
Ischaemia is known to be visible on 12-lead ECG; in fact, changes to 12-lead ECG form part of the gold-standard diagnosis for type-2 MI. Following consultation with cardiologists, we hypothesise that signs of ischaemia will also be detectable (either visibly or statistically) via 5-lead ECG. However, we must establish that this is indeed the case. 
For this purpose, we have identified a cohort of patients from cardiology (cohort 1), in which presence of ischaemia will be high, and where 12-lead ECGs will be commonplace. We will use this cohort to identify ischaemia in 12-lead ECG and assess the degree to which this is detectable in 5-lead ECG. If we find 5-lead is not sufficient for our purposes, we will explore other options such as alternative placement of 5-lead electrodes, which may allow us to more effectively capture ischaemia. 

### Serialisation
From now on using cohort 2, ECG segments will be grouped by patient and arranged in time order. 

### Change quantification
For each patient, successive ECG segments will be compared to a baseline segment and/or to additional previous segments, to quantify the change in the extracted features and establish a trajectory. 
We will visualise patient feature trajectories, quantify morphological change and apply manifold and transformation deviation techniques.

### Identification of MI
We will use information from our change quantification output, alongside baseline or endpoint features, to identify MI. We will investigate a range of techniques including 
* A statistical assessment of the feature trajectory e.g. applying thresholds for ischaemia or looking for points of inflection
* Unsupervised learning such as clustering of patients and labelling of clusters based on expert assessment in conjunction with 12-lead ECG from MUSE and/or lab biomarker data  
* Classification of e.g. "MI" vs "no-MI", or types of MI/ischaemia by statistical models (e.g. logistic regression) and AI models (e.g. support vector machines, random forests and neural networks)




