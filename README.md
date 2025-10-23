# DATA_ANALYSIS_PROJECT

This is a documentation of class experiences and projects during data analysis training I attended on The Incubator Hub x LITA platform so far.

[Project Overview](#project-overview)   ||
[Data Source](#data-source)    ||
[Tools](#tools)   ||
[Knowledge Obtained from Training](#knowledge-obtained-from-the-training)   ||
[Process](#process)

## Project Overview

This purpose of this is to analyze what has being taught, beyond the classrom experiences and a project to back it up.
The project will answer questions on how geographical factors as well as the status of a person/family could affect the charges placed on medical services.

## Tools

#### For Analysis:

 - Structured Query Language(SQL) : For data quering and database management

 - Microsoft Excel : For creating dashboards and gaining more insights into the data

#### For Portfolio Building and Showcase of Project:

 - Github

## Knowledge obtained from the training

- How to get the right data for answering proposed questions questions

- Techniques on how to conduct data inspection and cleaning

- How to use Excel functions

- How to write SQL queries

- How to visualize and manipulate data to provide reasonable insights

- Critical thinking


## Process

- Question definition
- Getting and loading data
- Data observation and cleaning
- Exploratory data analysis(EDA)
- Visualizations to demonstrate insights

  - ## Question Definition
  This project aims to answer for patterns influencing medical billing by exploring relationships between several variables and medical charges(target variable) and as well to make informed decisions.
  
  - ## Data Source
  The health cost data used for this project can be found [here](https://www.kaggle.com/datasets)
  The initial columns of the data are explained as follows:
     1. ID: A unique identifier assigned to each individual record, facilitating efficient data management and analysis.
     2. Smoker: A binary indicator of whether the patient is a smoker or not, as smoking habits can significantly impact healthcare costs.
     3. Age: The age of the patient, providing a crucial demographic factor that often correlates with medical expenses.
     4. Sex: The gender of the patient, offering insights into potential cost variations based on biological differences.
     5. Region: The geographic region of the patient, helping to understand regional disparities in healthcare expenditure.
     6. Charges: The medical charges incurred by the patient, serving as the target variable for analysis and predictions.
        Note: The other two columns will not be used for analysis.

  - ## Data Cleaning
  The dataset was filtered through to check for missing data and outliers which can be seen in the data filtering file.
  I also checked for duplicates using conditional formatting on excel.
  Additionally, I was able to eliminate excess decimals and added a currency to the costs on the dataset I'm working on: using MS Excel home tab.

  - ## Exploratory Data Analysis
  For the analysis, tools used are MS Excel and SQL Server Management Studio( into which I imported the medical cost data(as flat file) after creating a database according to the code below ,selecting [Id] as the primary key).
  ``` SQL
  create database My_Project
  ```

    --***HOW DOES SMOKING AFFECT MEDICAL COSTS?***

    To answer this question, I created a pivot table and a bar chart in the MS Excel environment relating smoking to medical costs.
   ![image](https://github.com/user-attachments/assets/b44a8c86-eaf6-4608-9096-e06cf024400d)
  
   ![image](https://github.com/user-attachments/assets/9e10bf55-7a5a-454f-ba23-5482917d70d0)
  
    INFERENCE: It can be seen that people who smoke spend more on medical costs, averagely.
  
    CONCLUSION: Efforts can be made to reduce medical costs considering this aspect by conducting campaigns to inform people about the dangerous health effects that smoking can have on the body system. Also, free healthcare events can be organized to assist affected people.

   --***HOW DOES GEOGRAPHICAL REGION AFFECT MEDICAL COSTS?***
  
   ![image](https://github.com/user-attachments/assets/1ceb6e1e-b155-44fc-be0c-cd5469215f94)

     INFERENCE: It is seen that in the northwest and southwest, patients averagely pay lesser costs than those in the northeast annd southeast. This can be due to more fund allocation, more facilities, more medical centres in the northwest and southwest regions.
  
     CONCLUSION: Medical funds should be evenly distributed accross all regions. More attention should be paid particularly to the northeast and southeast regions so that costs incurred by patients can as well be minimized.

    

    --***HOW DOES AGE GROUP AFFECT MEDICAL COSTS?***

     To answer this question, I manipulated the original dataset(with diverse ages) using the code below;
  
  ``` SQL
      alter table medical_cost
      add [Age group] varchar(255)
      update medical_cost
      set [Age group] =
       CASE
         when age >=60 then '60 and above'
         when age between 25 and 59 then '25-59'
         else '18-25'
      end
  ```
     Then, I selected the just created Age group column and the charges column like this ⬇️ ;  
   ``` SQL
        select AVG(charges) as Average_medical_cost, [age group] from medical_cost
        group by [Age group]
        order by AVG(charges) desc
   ```
     The above queries resulted in the table below
     |Average_medical_cost	| age group|
     |---------------------|----------|
     |21248.02	     |   60 and above|
     |13560.67 |	25-59|
     |9011.34	|18-25|
  
    INFERENCE: It is noticed that adults aged 60 and above are incurred more charges than any other age group.
  
    CONCLUSION: Old aged adults should be well monitored and eat healthy to reduce charges spent medically. Likewise, special discounts can be given to old-aged patients considering their health status which is due to ageing.

  
    - ## Data Visualization
  The image below is the dashboard of insights derived from the data
  ![image](https://github.com/user-attachments/assets/518caf29-a798-4de5-bd80-27ffb2532b22)

   
  


  

