# Diversity and Inclusion Analysis


## Table of Contents

- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)



### Project Overview

This data analysis aims to provide insights into diversity and inclusion aspects of a fictional multi-national technology compnay over the past year. By analyzing various aspects of the data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the comapny's workplace divesity.


### Data Source

The primary dataset used for this analysis is the "salary.csv" file extracted from https://kaggle.com, containing detailed salary information from various countries across the globe. It was sourced from reputable employment websites and survey and is made available under the CC0: Public Domain Creative Common License.

### Tools

- Excel - Data Cleaning
- MySQL - Data Analysis
- Tableau - Data visualization and Reporting

### Data Cleaning

During the data preparation phase, the following tasks were performed:

1. Data loading and inspection
2. Handling missing values and rectifying typographical errors
3. Data cleaning and formatting

### Exploratory Data Analysis

The EDA involved exploring the data to answer these key questions:

- Are there disparities in salary levels among employees belonging to different racial or ethnic groups?
- Are there differences in salaries based on educational level?
- Is there evidence of a gender pay gap within the company?

### Data Analysis

*Is there evidence of a gender pay gap within the company?*
```mysql

SELECT gender, avg(salary) as avaerage_salary
from salary_dataset
group by gender;
```
*Are there disparities in salary levels among employees belonging to different racial or ethnic groups?*
```mysql

SELECT 
    race, AVG(salary) AS average_salary
FROM
    salary_dataset
GROUP BY race;
```
*Are there differences in salaries based on educational level?*
```mysql

SELECT 
    education_level, AVG(salary) AS average_salary
FROM
    salary_dataset
GROUP BY education_level;
```

### Results

The analysis results are summarized as follows:

1. There is a clear trend where higher educational levels correspond to higher average salaries. This observation implies a strong correlation between education level and salary, indicating that individuals with advanced education tend to have greater earning potential.
2. The analysis further revelas a gender pay gap across board, with male employees earning, on average, higher salaries than their female counterparts. This discrepancy highlights a disparity that is commonly observed in various industries and regions.
3. There is a notable difference in salary levels across different ethnic groups, with Whites and Asian individuals typically earning higher incomes compared to other ethnicities in many countries.
4.  Blacks are underrepresented in the U.K and Australia.


![Overall Gender Pay gap](https://github.com/Lene-Ayele/Diversity-and-Inclusion/assets/156113418/60fa54c8-bcf8-466a-849e-9025302b7dee)






![education_level](https://github.com/Lene-Ayele/Diversity-and-Inclusion/assets/156113418/ce71be1a-7ba7-4264-9840-feaa11a69281)






![salary_disparities](https://github.com/Lene-Ayele/Diversity-and-Inclusion/assets/156113418/6625887c-364c-4333-9505-1d5c9daf3280)

### Recommendations

Based on the analysis, we recommend the following actions:

- Utilizing diverse hiring panels to reduce unconscious bias in the selection process.
- Implement transparent salary bands for all roles, ensuring that pay is based on experience, skills, and performance, irrespective of gender. This transparency can help identify and rectify pay disparities.
- Conduct regular pay equity audits to assess and address gender pay gaps. These audits should consider various factors such as job function, seniority, and performance metrics.
- Provide training for managers and HR personnel on gender biases and how to avoid them in hiring, promotions, and salary negotiations.
- Foster an inclusive workplace culture through regular diversity and inclusion training, workshops, and events that educate and encourage open dialogue among employees.
- Flexible work policies can be implemented to accommodate diverse life circumstances. This can help attract and retain a more diverse workforce.
- Set clear diversity and inclusion goals and metrics, and regularly report on progress. This could include specific targets for leadership diversity, gender pay equity, and the representation of minority groups within the workforce.

### Limitations

I consolidated the entries in the 'race' column into distinct ethnic categories based on racial classifications. This was done to simplify the extensive list of races, grouping certain ethnicities under a common racial designation. For example, individuals of Chinese, Korean, and other Asian descents were categorized under 'Asian', while those of Australian, White, and Welsh descents were labeled as 'White'. In the dataset of 6,685 rows, four salary entries were recorded in hundreds, whereas the rest were noted in hundreds of thousands. Assuming that all salaries are annual, I adjusted the four entries by appending zeros to ensure uniformity and prevent data skewing during analysis.
