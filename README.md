# Assessing Heart Disease Risk in the US
J.Jones, MPH

## Table of Contents

- [Background](#background)
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Key Aims](#key-aims)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Discussion](#discussion)
- [Conclusion](#conclusion)
- [References](#references)

### Background
Cardiovascular disease (CVD) is the top leading non-communicable disease in the United States, indicating that there needs to be more preventionary mechanisms in play to reduce this burden. Although there are several risk factors for heart disease, such as hypertension, diabetes, and smoking, nutritional intake also impacts this rate. Previous studies have found that dietary modifications could help avoid cardiovascular diseases and cardiovascular risk factors. Specifically, reduced sodium intake has been associated with lower prevalence of hypertension, one of the main risk factors for heart disease.

According to the CDC, approximately 90% of Americans (ages 2+) ingest an excessive amount of sodium. The 2020–2025 Dietary Guidelines for Americans advises Americans to consume less than 2300 mg of sodium per day. High sodium intake has been found to increase high blood pressure in several studies, however further research must be analyzed to support intervention implementation that can decrease the national burden of cardiovascular disease. In this study, the association between high sodium levels and heart disease among adults in the US will be assessed, as well as several social factors that may potentially be linked to increased CVD risk. 


### Project Overview
This research study explored if there is a higher risk of heart disease among adults who consume a nutritional intake with high sodium levels, and populations that may be  disproportionately affected due to social factors. Social factors such as age, gender, race, income, and education can potentially increase risk of negative cardiovascular health outcomes. This research aims to identify if there is an association between CVD and high sodium levels, while addressing social determinants to measure potential disparities. 

### Data Sources
From the United States Department of Agriculture (USDA) National Nutrient Database, datasets obtained in the study are from What We Eat in America (WWEIA) and the National Health and Nutrition Examination Survey (NHANES) from 2017-2018. The WWEIA provides data based on nutritional intake derived from NHANES, and will be utilized to assess the predictor variable. The NHANES datasets obtained in the study provide demographics and medical information to assess explanatory and outcome variables. The WWEIA’s purpose is to gather dietary consumption data from NHANES participants within the dietary interview component. The dietary intake data are used to estimate intakes of nutrients, energy, and other food components from the foods and beverages ingested over the 24-hour period leading up to the interview. The National Center for Health Statistics (NCHS), Division of Health and Nutrition Examination Surveys of the Department of Health and Human Services (DHHS) controls the survey sample design and all other aspects of data collection, while the Food Surveys Research Group (FSRG) of the USDA operates the upkeep, methodology, and review and processing of the dietary data. 

### Tools
- SAS

### Data Cleaning and Preparation
The following was performed for data cleaning and preparation:
1. Data inspection
2. Handling missing values through inclusion/exclusion criteria
3. Data cleaning and formatting

### Key Aims
The data analysis measured a potential association between high sodium intake levels and cardiovascular disease by addressing the following:
- Is there a higher risk of heart disease among adults who consume a nutritional intake with high sodium levels?
- Which populations are disproportionately affected? What are some external barriers that impact individuals from receiving nutritional intake within the recommended guidelines of sodium levels? How can this be improved?

### Data Analysis
Chi-square test was assessed to determine the association between CVD diagnosis and the covariates. Fisher’s exact test was used to determine the association between CVD and high sodium intake vs. recommended levels.
``` SAS
proc freq data=mergedfinal;
table sodium*CVD/chisq;
run;
```

A logistic regression was conducted to measure the association between sodium levels as a continuous variable and heart disease diagnosis, while also measuring the covariates which include age, gender, race, income, and education.
``` SAS
proc logistic data= mergedfinal;
model CVD= DR1TSODI RIDAGEYR RIAGENDR RIDRETH3 INHHIN2 DMDEDUC2
run;
```
### Results
A total of 2321 participants in the study reported their sodium intake levels from the dietary intake questionnaire. 66.05% reported high sodium intake levels (2300+ mg) and the average sodium intake level was 3193mg. This supports previous literature indicating the daily average of sodium intake is relatively high for Americans, higher than the recommended dietary intake of less than 2300 mg. 
![Sodium Intake levels](https://github.com/JJ9218/Heart-Disease-Risk/assets/163039134/78d44d39-e639-4417-a166-7a76cef67f36)

When measuring the association between heart disease diagnosis and sodium intake levels by conducting a Chi-square and Fisher’s Exact Test, the results indicated a lack of an association between high sodium intake levels (binary) and CVD diagnosis with Chi-square probability of 0.9257 and a two-sided Pr <=P of 1.000, rejecting the null hypothesis. The likelihood of an individual being diagnosed with CVD was relatively low when measuring for high sodium intake levels, which remained consistent when measuring sodium intake levels continuously and categorically shown in Table 2. Among those who were diagnosed with CVD, individuals who consumed a daily dietary intake more than 3,000mg of sodium were more likely to be diagnosed compared to those who consumed within the recommended dietary intake levels. 
![CVDsodiumv](https://github.com/JJ9218/Heart-Disease-Risk/assets/163039134/748f90ba-aa7e-48b5-a6d7-2ba2dc46fdde)

A logistic regression was conducted for measuring all covariates including age, gender, race, income, and education. Among those who had high sodium level intakes and were diagnosed with CVD, the age groups remained mostly consistent. However, those who followed the recommended dietary intake were more likely to be diagnosed with CVD the older they were. This indicates that age may potentially have an impact on CVD diagnosis. Among those with a high sodium level intake, Non-Hispanic White (29%) and Non-Hispanic Black people (27%) were the majority that represented CVD diagnosis. Non-Hispanic Black people with high sodium intake levels were more likely to have CVD diagnosis compared to other ethnic minority groups. When conducting a logistic regression for addressing all covariates and sodium as a continuous variable, odds ratio estimates collectively suggest there is not statistically significant association. However, socioeconomic factors (specifically income and education levels) in this study compared with other variables had more of a likelihood to be associated with sodium intake levels and CVD.
![CVDsodium](https://github.com/JJ9218/Heart-Disease-Risk/assets/163039134/e160de09-d068-4b71-b984-92dc72e32772)

### Discussion
Further research is necessary for identifying a stronger association between high sodium intake levels and CVD. This research study lacked several factors that could have strengthened this association. First, utilizing surveys when conducting dietary consumption levels have more risk of margin of error due to survey bias; it is a possibility that participants were not providing their accurate nutritional type and amount consumed, as well as, the survey only measured dietary consumption for one day. For further accuracy and consistency, it is recommended to utilize surveys that are longer than one day to assume normal dietary consumption. Next, geographic location was a missing variable within this dataset. Participants all were located in the United States for the duration of the interview component, however, it did not account for specific geographic location. When considering the social and nutritional epidemiology of a non-communicable disease in relation with individual behaviors such as dietary consumption, geographic location is integral when it comes to measuring how some areas may be disproportionately impacted. For example, hypertension levels in African Americans in Philadelphia are the highest in comparison to other races/ethnicities in the city. Communities that live in neighborhoods defined as food swamps or food deserts (areas that have an abundance of processed, unhealthy food markets, yet a lack of access to fresh food markets) have less access to affordable fresh foods which lead to unhealthy eating behaviors, to a higher risk of diet-related conditions such as hypertension or diabetes. 

In addition, hypertensive data was a variable missing from the medical conditions dataset that could have potentially strengthened the association between CVD and high sodium intake levels. Given that previous literature states an association between hypertension and high sodium levels, with hypertension being a major risk factor for CVD, measuring hypertension diagnosis along with this research would have been an important covariate for CVD diagnosis. The medical conditions dataset provided CVD-related symptoms such as angina and shortness of breath, and the WWEIA dataset did provide other nutrients that could potentially impact the relationship such as cholesterol, potassium, sugar, fats, etc. With angina being a major symptom of CVD and is used to assess potential CVD diagnosis, participants who have answered no to CVD diagnosis but experience angina frequently could have been measured to potentially have CVD. Other nutrients such as cholesterol, potassium, sugar, and fats in previous literature are also linked to cardiovascular diseases and may have also been measured to see if its association with high sodium intake levels increases their risk. However, when also considering these factors, the study population decreased drastically, which could lead to skewed results for the research being conducted. The datasets lacked high frequency when including answered questions of each variable that could have contributed to a more significant link. 


### Conclusion
In conclusion, further research is necessary when conducting the social and nutritional epidemiology of CVD when measuring for sodium intake levels. This study indicated that the odds between high sodium intake levels and CVD is not likely, however other conditions and variables that should be highly considered for future analysis include other nutritional intake such as cholesterol, fats, sugar, and potassium. Medical conditions that may assess potential CVD diagnosis also include symptoms such as angina and shortness of breath, as well as other conditions that have previously shown to have associations with high sodium intake levels and is a risk factor of CVD, such as hypertension. Additionally, time constraints regarding dietary intake levels should also be extended for further accuracy. Overall, social and nutritional factors can potentially have an impact on CVD diagnosis, but there must be further actions taken to strengthen this association. 


### References
1. Arnett, D. K., Ziaeian, B., Yeboah, J., Williams Sr, K. A., Virani, S. S., Smith Jr, S. C., Muñoz, D., Miedema, M. D., Michos, E. D., McEvoy, J. W., Lloyd-Jones, D., Khera, A., Dennison Himmelfarb, C., Hahn, E. J., Goldberger, Z. D.,
2. Buroker, A. B., Albert, M. A., & Blumenthal, R. S. (2019). 2019 ACC/AHA guideline on the primary prevention of cardiovascular disease: A report of the American College of Cardiology/American Heart Association Task Force on Clinical Practice Guidelines. Circulation, 140(11). https://doi.org/10.1161/cir.0000000000000725
3. Benjamin, E. J., Muntner, P., Alonso, A., Bittencourt, M. S., Callaway, C. W., Carson, A. P., Chamberlain, A. M., Chang, A. R., Cheng, S., Das, S. R., Delling, F. N., Djousse, L., Elkind, M. S. V., Ferguson, J. F., Fornage, M., Jordan, L. C., Khan, S. S., Kissela, B. M., Knutson, K. L., … Virani, S. S. (2019). Heart disease and stroke statistics—2019 update: A report from the American Heart Association. Circulation, 139(10). https://doi.org/10.1161/cir.0000000000000659
4. CDC. (2021, December 21). Sodium. Centers for Disease Control and Prevention. Retrieved December 1, 2022, from https://www.cdc.gov/heartdisease/sodium.htm
5. CDC. (2022, October 14). Heart disease facts. Centers for Disease Control and Prevention. Retrieved December 1, 2022, from https://www.cdc.gov/heartdisease/facts.htm
6. Go Red for Women. (2020, January 28). In Philly, the Neighborhood You Live In Could Determine Your Lifespan. Activists Are Pointing to the Food We Eat. Philadelphia Magazine. Retrieved March 18, 2022, from https://www.phillymag.com/sponsor-content/philly-neighborhood-lifespan/#:~:text=Food%20deserts%20develop%20as%20grocery,between%2040%20and%2050%20percent.
7. Graham, G. (2015). Disparities in cardiovascular disease risk in the United States. Current Cardiology Reviews, 11(3), 238–245. https://doi.org/10.2174/1573403x11666141122220003
8. Grillo, A., Salvi, L., Coruzzi, P., Salvi, P., & Parati, G. (2019). Sodium intake and hypertension. Nutrients, 11(9), 1970. https://doi.org/10.3390/nu11091970
9. Grines, C. L., Klein, A. J., Bauser‐Heaton, H., Alkhouli, M., Katukuri, N., Aggarwal, V., Altin, S. E., Batchelor, W. B., Blankenship, J. C., Fakorede, F., Hawkins, B., Hernandez, G. A., Ijioma, N., Keeshan, B., Li, J., Ligon, R. A.,
10. Pineda, A., Sandoval, Y., & Young, M. N. (2021). Racial and ethnic disparities in coronary, vascular, structural, and congenital heart disease. Catheterization and Cardiovascular Interventions, 98(2), 277–294. https://doi.org/10.1002/ccd.29745
11. Heidenreich, P. A., Trogdon, J. G., Khavjou, O. A., Butler, J., Dracup, K., Ezekowitz, M. D., Finkelstein, E. A., Hong, Y., Johnston, S. C., Khera, A., Lloyd-Jones, D. M., Nelson, S. A., Nichol, G., Orenstein, D., Wilson, P. W. F., & Woo, Y. J. (2011). Forecasting the future of cardiovascular disease in the United States. Circulation, 123(8), 933–944. https://doi.org/10.1161/cir.0b013e31820a55f5
12. Hirsch, J. A., Melly, S., Moore, K., Rollins, H., Quick , H., Song, G., Washington, R., & Whitley, J. (2019). Close to Home: The Health of Philadelphia's Neighborhoods. Philadelphia Health Rankings. Retrieved March 2023, from https://phillyhealthrankings.org/
13. Lopez, E. O., Ballard, B. D., & Jan, A. (2022). Cardiovascular Disease. National Library of Medicine. Retrieved December 1, 2022, from https://www.ncbi.nlm.nih.gov/books/NBK535419/
14. NHANES. (2021). NHANES 2017-2018 questionnaire data. Centers for Disease Control and Prevention. Retrieved December 3, 2022, from https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Questionnaire&CycleBeginYear=2017
15. NIH. (2022, March). Cardiac Catheterization. National Heart Lung and Blood Institute. Retrieved December 1, 2022, from https://www.nhlbi.nih.gov/health/cardiac-catheterization
16. Patel, Y., & Joseph, J. (2020). Sodium intake and heart failure. International Journal of Molecular Sciences, 21(24), 9474. https://doi.org/10.3390/ijms21249474
17. Ravera, A., Carubelli, V., Sciatti, E., Bonadei, I., Gorga, E., Cani, D., Vizzardi, E., Metra, M., & Lombardi, C. (2016). Nutrition and cardiovascular disease: Finding the perfect recipe for Cardiovascular Health. Nutrients, 8(6), 363. https://doi.org/10.3390/nu8060363
18. Shah, B., Newman, J. D., Woolf, K., Ganguzza, L., Guo, Y., Allen, N., Zhong, J., Fisher, E. A., & Slater, J. (2018). Anti‐inflammatory effects of a vegan diet versus the American heart association–recommended diet in coronary artery disease trial. Journal of the American Heart Association, 7(23). https://doi.org/10.1161/jaha.118.011367
19. USDA. (2022). WWEIA documentation and data sets: USDA ARS. USDA Agricultural Research Service. Retrieved December 1, 2022, from https://www.ars.usda.gov/northeast-area/beltsville-md-bhnrc/beltsville-human-nutrition-research-center/food-surveys-research-group/docs/wweia-documentation-and-data-sets/
20. Wang, Y.-J., Yeh, T.-L., Shih, M.-C., Tu, Y.-K., & Chien, K.-L. (2020). Dietary sodium intake and risk of cardiovascular disease: A systematic review and dose-response meta-analysis. Nutrients, 12(10), 2934. https://doi.org/10.3390/nu12102934 
