# Diabetes-Prediction-using-MySQL

# INTRODUCTION

# In the ever-evolving landscape of healthcare, data-driven approaches are playing a pivotal role in predicting and managing various medical conditions. This project leverages MySQL, a powerful relational database management system, to develop a predictive model for assessing the risk of diabetes in females. To achieve this, we will harness a comprehensive diabetes dataset, which contains a wide array of health-related features and outcomes.

# This endeavor underscores the profound impact of data analytics on healthcare, enabling us to take proactive steps towards a healthier future.



create database diabetes;

use diabetes;

create table diagnosis(Pregnancies int , Glucose int, Blood_Pressure int , Skin_Thickness int,
Insulin int , BMI double , Diabetes_Pedigree_Function double , Age int , Outcome Boolean);

select * from diagnosis;

# Number of Females in the dataset

select count(Pregnancies) from diagnosis;

# Number of Females in the dataset is 768

# Average age of females in the datset

select AVG (Age) from diagnosis;

# Average age of a female in the dataset is 33.2409

# Average number of pregnancies a female delievered

select AVG(Pregnancies) from diagnosis;

# Average number of pregnancies is 3.8451
# Approximately 4

# 1. AGE

# Diabetes can develop at any age, but it is more commonly diagnosed in individuals who are 45 years or older. 
# However, with the increasing prevalence of obesity and unhealthy lifestyles, diabetes is now being diagnosed at younger ages, including in women in their 20s and 30s. 
#Age is just one of many risk factors for diabetes, and genetics, lifestyle, and other factors also play a significant role in its development.

# lets have a hypothesis that females get commonly diagnosed after the age of 45

# this hypothesis is just as assumption to get the number females who are likely get diabetes it may not be completely true

select count(Age) from diagnosis where Age >= 45;

# Hence, 133 females out of 768  are likely to be diabetic

# 2. Obesity

# Obesity is also a symptom  of  diabetes

# Obesity is typically defined as having a body mass index (BMI) of 30 or higher. 
# So, for a female to be considered obese, her BMI would need to be 30 or above.

select count(BMI) from diagnosis where BMI >= 30;

# Hence, 472 Females out of 768  are obese 

# 3. Pregnancies 

# it is believed that if women has more than 4 pregnancies she is likely to get diabetes

select count(Pregnancies) from diagnosis where pregnancies > 4;

# 276 woman have 4 and above pregnancies they are likely to get diabetes

# 4. BP - Diastolic Value

# For age 18 - 39 the Diastolic Value is 68


select count(Age) from diagnosis where Age  between 18 and 39 and Blood_Pressure < 68;

# 241 women who are between 18 - 39 of age don't have normal BP


# For age 60 and above Diastolic value is 68

select count(Age) from diagnosis where Age > 60 and Blood_Pressure < 68;

# 5 women who are above 60 years old don't have normal BP

# For age 40 - 59 the Diastolic value is 74 

select count(Age) from diagnosis where Age between 40 and 59 and Blood_Pressure < 74;

# 62 women who are 40 - 59 years old don't have normal BP

# Hence, in total (241 + 5 + 62) = 308 women out of 768 don't have normal BP


# 5.  Glucose

# if a person has glucose greater than or equal to 140mg then they don't have normal glucose

select count(Glucose) from diagnosis where Glucose >= 140;

# 197 women out of 768 don't have normal glucose


#6. Insulin

#if a person has insulin above 166 then they will definitely will have diabetes

select count(Insulin) from diagnosis where Insulin >= 166;

# 133 women out of 768 have diabetes

# Conclusion:

# In conclusion, through the SQL queries and analysis performed on the dataset, we have identified that 133 women out of the 768 women in the dataset exhibit diabetes. 
#This confirmation is based on the observation that their age and insulin values align, suggesting a strong correlation between these variables and the presence of diabetes.
# Furthermore, our analysis has unveiled several other significant findings. 
#I have identified abnormalities in key health indicators, including diastolic blood pressure, glucose levels, BMI, and indicators of obesity. These findings underscore the importance of early detection and intervention in managing diabetes and related health issues, emphasizing the critical role of data-driven healthcare analysis in improving the well-being of individuals.
# In summary, my exploration of the dataset has not only confirmed the presence of diabetes in a subset of the population but has also shed light on other critical health factors that warrant attention and further investigation to promote better health outcomes.





