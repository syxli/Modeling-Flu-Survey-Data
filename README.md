# **Predicting H1N1 and Seasonal Flu Vaccination**
#### **Collaborators**: 
[**Lavanya Acharya**](https://github.com/LAcharya) | [**Katrin Ayrapetov**](https://github.com/Kaayrapetov) | [**Sean Li**](https://github.com/syxli)  

### **Introduction**
In 2009, a novel strain of influenza virus, commonly referred to as “swine flu”, spread first across the United States and quickly around the world causing a pandemic. From April 2009 to April 2010, the CDC estimates that there were 60.8 million cases, 274,304 hospitalizations, and 12,469 deaths in the United States alone. A vaccine for the H1N1 flu virus became publicly available in October 2009. 

--------------------------  
<img src="figures/clinic.png" width=600 />

###### **Figure 1.** *A view of a newspaper headline near Times Square in New York, New York, USA, on 27 April 2009. Photo by EPA/BGNES (Left). An H1N1 flu vaccination clinic held in San Francisco in December 2009, Justin Sullivan/Getty Images (Right)*

--------------------------

From August 2009 to May 2010, one or more doses of the *seasonal flu vaccine* were administered to 31.6 million children and 91.6 million adults. During the same time period, one or more doses of the *H1N1 vaccine* were administered to 29.1 million children and 80.8 million adults. 

#### **National H1N1 Flu Survey**

In 2009, the US National Center for Health Statistics conducted [National H1N1 Flu Survey](https://www.cdc.gov/nchs/nis/data_files_h1n1.htm) over phone. The phone survey asked respondents whether they had received the H1N1 and seasonal flu vaccines, in conjunction with questions about themselves. The questions covered the respondents’ social, economic, and demographic background, opinions on vaccine effectiveness and risks, and behaviors towards mitigating transmission. The [survey](https://ftp.cdc.gov/pub/Health_Statistics/NCHS/Dataset_Documentation/NIS/nhfs/nhfspuf_QUEX.PDF) is sixty pages long. 

Below is a description of the survey from the [CDC page for National Immunization Surveys](https://ftp.cdc.gov/pub/Health_Statistics/NCHS/Datasets/nis/nhfs/nhfspuf_readme.txt):

--------------------------

**"** *The National 2009 H1N1 Flu Survey (NHFS) was sponsored by the 
National Center for Immunization and Respiratory Diseases 
(NCIRD) and conducted jointly by NCIRD and the National 
Center for Health Statistics (NCHS), Centers for Disease 
Control and Prevention (CDC). The NHFS was a list-assisted 
random-digit-dialing telephone survey of households, designed
to monitor influenza immunization coverage in the 2009-10 season.*

*The target population for the NHFS was all persons 6 months or
older living in the United States at the time of the 
interview. Data from the NHFS were used to produce timely estimates 
of vaccination coverage rates for both the monovalent pH1N1 and
trivalent seasonal influenza vaccines.* **"**

--------------------------

### Data
Data was obtained from [DrivenData](https://www.drivendata.org/about/), a website that hosts data science competitions and crowdsources social challenges from across the world. This particular dataset was from the [Flu Shot Learning](https://www.drivendata.org/competitions/66/flu-shot-learning/) competition. 

The data consists of 36 features consisting of binary, ordinal and categorical responses. The [data dictionary from DrivenData](https://www.drivendata.org/competitions/66/flu-shot-learning/page/211/) is below:

---------------------------------------
Variable | Description | Values|
---------|-------------|-------|
h1n1_concern | Level of concern about the H1N1 flu.|0 = Not at all concerned; 1 = Not very concerned; 2 = Somewhat concerned; 3 = Very concerned.
h1n1_knowledge | Level of knowledge about H1N1 flu.|0 = No knowledge; 1 = A little knowledge; 2 = A lot of knowledge.
behavioral_antiviral_meds | Has taken antiviral medications. | (binary)
behavioral_avoidance | Has avoided close contact with others with flu-like symptoms. | 0 = No; 1 = Yes.
behavioral_face_mask | Has bought a face mask. | 0 = No; 1 = Yes.
behavioral_wash_hands | Has frequently washed hands or used hand sanitizer. |(0 = No; 1 = Yes.
behavioral_large_gatherings | Has reduced time at large gatherings. | 0 = No; 1 = Yes.
behavioral_outside_home | Has reduced contact with people outside of own household. | 0 = No; 1 = Yes.
behavioral_touch_face | Has avoided touching eyes, nose, or mouth. | 0 = No; 1 = Yes.
doctor_recc_h1n1 | H1N1 flu vaccine was recommended by doctor. | 0 = No; 1 = Yes.
doctor_recc_seasonal | Seasonal flu vaccine was recommended by doctor. | 0 = No; 1 = Yes.
chronic_med_condition | Has any of the following chronic medical conditions: asthma or an other lung condition, diabetes, a heart condition, a kidney condition, sickle cell anemia or other anemia, a neurological or neuromuscular condition, a liver condition, or a weakened immune system caused by a chronic illness or by medicines taken for a chronic illness. | 0 = No; 1 = Yes.
child_under_6_months | Has regular close contact with a child under the age of six months. | 0 = No; 1 = Yes.
health_worker | Is a healthcare worker. | 0 = No; 1 = Yes.
health_insurance | Has health insurance. | 0 = No; 1 = Yes.
opinion_h1n1_vacc_effective | Respondent's opinion about H1N1 vaccine effectiveness. | 1 = Not at all effective; 2 = Not very effective; 3 = Don't know; 4 = Somewhat effective; 5 = Very effective.
opinion_h1n1_risk | Respondent's opinion about risk of getting sick with H1N1 flu without vaccine. | 1 = Very Low; 2 = Somewhat low; 3 = Don't know; 4 = Somewhat high; 5 = Very high.
opinion_h1n1_sick_from_vacc | Respondent's worry of getting sick from taking H1N1 vaccine. | 1 = Not at all worried; 2 = Not very worried; 3 = Don't know; 4 = Somewhat worried; 5 = Very worried.
opinion_seas_vacc_effective | Respondent's opinion about seasonal flu vaccine effectiveness. | 1 = Not at all effective; 2 = Not very effective; 3 = Don't know; 4 = Somewhat effective; 5 = Very effective.
opinion_seas_risk | Respondent's opinion about risk of getting sick with seasonal flu without vaccine. | 1 = Very Low; 2 = Somewhat low; 3 = Don't know; 4 = Somewhat high; 5 = Very high.
opinion_seas_sick_from_vacc | Respondent's worry of getting sick from taking seasonal flu vaccine. |1 = Not at all worried; 2 = Not very worried; 3 = Don't know; 4 = Somewhat worried; 5 = Very worried.
age_group | Age group of respondent. | '65+ Years', '55 - 64 Years', '45 - 54 Years', '18 - 34 Years', '35 - 44 Years'
education | Self-reported education level. | College Graduate, Some College, 12 Years, < 12 Years
race | Race of respondent. | 'White', 'Black', 'Hispanic', 'Other or Multiple'
sex | Sex of respondent. | Male, Female
income_poverty | Household annual income of respondent with respect to 2008 Census poverty thresholds. | <= USD 75,000, Above Poverty, > USD 75,000, Below Poverty 
marital_status | Marital status of respondent. | Married, Not Married
rent_or_own | Housing situation of respondent. | Rent, Own
employment_status | Employment status of respondent. | Employed, Not in Labor Force, Unemployed
hhs_geo_region | Respondent's residence using a 10-region geographic classification defined by the U.S. Dept. of Health and Human Services. | Values are represented as short random character strings.
census_msa | Respondent's residence within metropolitan statistical areas (MSA) as defined by the U.S. Census. | MSA, Not Principle  City, MSA, Principle City, Non-MSA
household_adults | Number of other adults in household | top-coded to 3. |
household_children | Number of children in household | top-coded to 3. |
employment_industry | Type of industry respondent is employed in. | Values are represented as short random character strings.
employment_occupation | Type of occupation of respondent. | Values are represented as short random character strings.

-----------------------------

### Models and Metrics

Three Models were tested for their ability to predict whether respondents were vaccinated or unvaccinated: 
* Logistic Regression
* Neural Network
* XGBoost

The models were compared on four metrics: 
* Recall
* Precision
* Accuracy
* ROC_AUC

Recall score was chosen to be the most important metric to compare models. This was because the goal was to minimize the number of respondents falsely classified as vaccinated, in order to capture as many unvaccinated respondents as possible. 

### Methodology

#### Exploratory Data Analysis and Cleaning

The survey was done over phone and respondents were allowed to provide no response to the question asked. 



