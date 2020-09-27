## Requirement

- Environment: Python == 3.6.7 
- Packages: Numpy, Pandas (SQLitle3), Scipy, scikit-learn

## Introduction

### Objectives
Hospital Length of Stay (LOS) in a hospital is an index that can be defined as the days of admission. It is an important factor for allocating medical resources. In stead of focusing on adults population, we characterizing the ICU LOS for neonatal group (age < 1 year)



### Dataset 
This repository is based on MIMIC-III v1.4 dataset [6], which comprises 61,532 intensive care
unit stays: about 50000 stays for adult patients and 8000 for
neonatal patients, during the course of admission of the
Beth Israel Deaconess Medical Center from June 2001 to
October 2012.


### Features
Based on Neonatal Acute Physiology (SNAP) [2], National InstituteOf Child Health And Human Development (NICHHD) [3], Clinical Risk Index for Babies (CRIB)[4], we extract the feature listed below:

-  Lab Test Features:
    1. Anion Gap value
    2. BANDS (Immature band forms) value
    3. Bicarbonate value
    4. Bilirubin value
    5. BUN (Blood urea nitrogen) value
    6. Creatinine value−Chloride value
    7. Glucose max/min value
    8. Hematocrit max/min value
    9. Potassium max/min value
    10. Platelet value
    11. PT (Prothrombin Time) value
    12. PTT (Partial Prothrombin Time) value
    13. Sodium max/min value
- Blood Gas Features:
    1. Arterial oxygen partial pressure (PaO2 value)
    2. Arterial carbon dioxide partial pressure (PaCO2) value

## File Description


### extract_neonate.py
SQL syntax extract the neonate patients rows. 

### neo_los_label_prepare.ipynb
Calculate the noenate hospital length of stay, binarize to CLASS 1: LOS < mean(LOS), and CLASS 2: LOS > mean(LOS)

### First_day_lab_test.ipynb
This is based on [https://github.com/MIT-LCP/mimic-code]. Calculating the lab test biomarkers we interested.

### First_day_blood_gas.ipynb
This is based on [https://github.com/MIT-LCP/mimic-code]. Calculating the blood gas test biomarkers we interested.


### PO2_score.ipynb 
Calculate PO2 score based on [2, 3, 4] definition. Scored as binary normal and abnormal.
(So do Glucose_max_score.py, Potassium_max_score.py.....)



### Model.ipynb

Feature selection and Classification
Load all feature files and merge to a single dataframe. Classification using Logisitc Regression and RandomForest  



### Utility.py
Simple helper functions of pandas dataframe manipulation.



```
## Reference

-    [1] Mimic-iii, a freely accessible critical care database. https://mimic.physionet.org/.
-    [2] D. K. R. et al, “Score for neonatal acute physiology: A physiologic severity index for neonatalintensive care.” [Online]. Available: https://pubmed.ncbi.nlm.nih.gov/8441569/
-    [3]W. E. e. a. Horbar JD, Onstad L, “Predicting mortality risk for infants weighing 501 to 1500grams at birth: a national institutes of health neonatal research network report.
-    [4] The crib (clinical risk index for babies) score: a tool for assessing initial neonatal risk and com-paring performance of neonatal intensive care units. https://pubmed.ncbi.nlm.nih.gov/8100927/.
-    [5] MIMIC Code Repository (https://github.com/MIT-LCP/mimic-code)
