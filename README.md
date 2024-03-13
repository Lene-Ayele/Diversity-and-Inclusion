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

This data analysis aims to provide insights into diversity and inclusion of a multinational technology compnay over the past year. By analyzing various aspects of the data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the comapny's workplace divesity.


### Data Source

The primary dataset used for this analysis is the "salary.csv" file extracted from https://kaggle.com/datasets , containing detailed salary information from various countries across the globe.

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

The EDA involved exploring the data to answer key questions, such as:

- Are there any significant variations in salary levels based on the country?
- Are there disparities in salary levels among employees belonging to different racial or ethnic groups?
- What is the representation of various ethnicities in leadership positions within the company?
- Are there differences in salaries based on educational level?
- Is there evidence of a gender pay gap within the company?

### Data Analysis
---
*What is the representation of various ethnicities in leadership positions within the company?*
```mysql

SELECT 
    job_rank, race, COUNT(*) AS count_leadership
FROM
    salary_dataset
WHERE
    job_rank = 'Board Level'
        OR job_rank = 'Senior Level'
GROUP BY job_rank , race;
```
*Are there any significant variations in salary levels based on the country?*
```mysql

SELECT 
    country, AVG(salary) AS average_salary
FROM
    salary_dataset
GROUP BY country;
```
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
2. The analysis further revelas a gender pay gap across board, with male employees earning, on average, higher salaries than their female counterparts. Thisdiscrepancy highlights a disparity that is commonly observed in various industries and regions.
3. There is a notable difference in salary levels across different ethnic groups, with Whites and Asian individuals typically earning higher incomes compared to other ethnicities in many countries.
4.  Blacks are underrepresented in the U.K and Australia.



![Dashboard](https://github.com/Eleya1/Diversity-and-Inclusion/assets/156113418/fd55834e-7822-48b5-b4e9-ce8d1ec96ae8)



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

I enhanced the 'race' column by consolidating entries into distinct ethnicities based on racial categories. This measure was taken to streamline the extensive list of races, as certain ethnicities can be classified under a single race. For instance, individuals of Chinese, Korean, and other Asian descent were grouped under 'Asian', while those of Australian, White, and Welsh descent were categorized as 'White'. Furthermore, among the 6685 rows of data, four salary entries were indicated in hundreds, while the remainder were in hundreds of thousands, suggesting an assumption that salaries are represented on an annual basis. To ensure consistency and prevent data skewing during analysis, I adjusted the four entries by adding zeros to align them with the other entries.
