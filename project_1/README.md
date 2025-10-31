## Overview

This project explores the data job market, with a special focus on data analyst positions. It was developed to gain deeper insights into current market trends and to better understand which skills drive the best career opportunities.

Using data from Luke Barousse’s Python Course, the analysis draws on detailed information about job titles, salaries, locations, and required skills. Through Python-based analysis, the project highlights key insights — including the most in-demand tools, salary patterns, and how skill demand connects with pay levels in the data analytics field.

# the questions

1. what are the most demand skills for the top 3 most popular data roles?
2. how are in-demand skills trending for data analysts?
3. How well do jobs and skills pay for data analysts ?
4. What is the most optimal skill to learn for Data Analyts?

## tools I Used:

In exploring the data analyst job market through in-depth analysis, I relied on a robust set of tools:

**Python**: Served as the core engine for processing data and uncovering key patterns.  
I incorporated these essential Python libraries:

- **Pandas**: Enabled efficient data manipulation and exploration.
- **Matplotlib**: Powered the creation of foundational data visualizations.
- **Seaborn**: Elevated my charts with more sophisticated and polished graphics.

**Jupyter Notebooks**: My interactive environment for executing code, blending scripts with inline commentary and results.

**Visual Studio Code**: The primary editor where I wrote and ran my Python programs.

## 1. what are the most demand skills for the top 3 most popular data roles?

To identify the most in-demand skills for the top 3 most popular data roles, I filtered the job postings to focus on the most common positions and extracted the top 5 skills for each of these roles. This analysis highlights the most popular job titles and their key skills, helping me prioritize which skills to focus on depending on the role I am targeting.

View my notebook with detailed steps here:[Skill_Demand](project_1\2_skills_count.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
plt.show()
```

#### Results

![2_skills_count.ipynb](images\output.png)

- Bar graph visualizing the salary for the top 3 data roles and their top 5 skills associated with each.

#### insights

- SQL is the heartbeat of every data role— it’s the first language employers look for, no matter the title.

- Python powers the future — from cleaning data to building models and pipelines, it’s the skill that opens advanced doors.

- Specialization defines your path — master Excel and Tableau for business insights, cloud tools and Spark for infrastructure, or R for deep statistical work.

## 2. how are in-demand skills trending for data analysts?

view my notebook with detailed steps here: [skill_trend](project_1\skill_trend.ipynb)

### Visualize Data

```python
df_plot=df_DA_US_percent.iloc[:,:5]
sns.lineplot(data=df_plot,dashes=False,palette='tab10')
sns.set_theme(style='ticks')
sns.despine()
plt.legend().remove()

from matplotlib.ticker import PercentFormatter
ax=plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
plt.show()
```

#### results

![skill_trend](images\skills_trend.png)
Bar graph visualizing the trending top skills for data analysts in US

#### insights

-SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
-Excel experienced a significant increase in demand starting around September, surpassing both Python and Tableau by the end of the year.
-Both Python and Tableau show relatively stable demand throughout the year with some fluctuations but remain essential skills for data analysts. Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.

## 3. How well do jobs and skills pay for data analysts ?

To conduct a salary analysis for data nerds—or, in other words, to identify the highest-paying roles and skills—I focused only on jobs in the United States and examined their median salaries. First, I looked at the salary distributions of common data jobs to get an idea of which ones pay the most

View my notebook with detailed steps here:[Salary_Analysis]()

### Visualize Data

```python
sns.boxplot(data=df_US_top6,x='salary_year_avg',y='job_title_short',order=list_job_order)
ax=plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x,pos:f' ${int(x/1000)}k'))
plt.xlim(0,600000)
plt.show()
```

#### results

![salary_distrubution for data jobs in US](images\salary_distribution.png)

- box plot visulizing salary_distrubution for the top 6
  data jobs titles .

#### insights

-Senior Data Scientist and Senior Data Engineer have the highest median salaries.
-Data Analysts earn the least — both regular and senior Data Analysts have the lowest pay ranges.
-Data Scientists show wide variation that mean large spread of salaries indicates varied experience levels or industries.
— Data Engineers and Senior Data Engineers have tighter distributions.
all roles show some very high salaries above $400k, especially Data Scientists.

### Visualize Data

```python
fig,ax= plt.subplots(2,1)
sns.barplot(data=df_DA_top_pay, x='median',y= df_DA_top_pay.index ,ax=ax[0], hue='median',palette="dark:b_r")
sns.barplot(data=df_DA_skills,x='median',y=df_DA_skills.index,ax=ax[1],hue='median',palette="light:b")
```

#### results

![highest paid and most demand skills](images\highest_paid__most_demand_skill.png)

Two seprate bar graphs visualiztion the highest paid skills and most in_demand skills for data analysts in US

#### insights

-The top graph shows specialized technical skills like dplyr, Bitbucket, and Gitlab are associated with higher salaries, some reaching up to $200K, suggesting that advanced technical proficiency can increase earning potential.

-The bottom graph highlights that foundational skills like Excel, PowerPoint, and SQL are the most in-demand, even though they may not offer the highest salaries. This demonstrates the importance of these core skills for employability in data analysis roles.

-There's a clear distinction between the skills that are highest paid and those that are most in-demand. Data analysts aiming to maximize their career potential should consider developing a diverse skill set that includes both high-paying specialized skills and widely demanded foundational skills.

## 4. What is the most optimal skill to learn for Data Analyts?

To identify the most optimal skills to learn I calculated the percent of skill demand and the median salary of these skills

View my notebook with detailed steps here:[Optimal_Skills](project_1\images\most_optimal_skills.png)

### Visualize Data

```python
import seaborn as sns
sns.scatterplot(data=df_plot, x='skill_percent',
y='median_salary',
hue='technology')
sns.despine()
```

#### Results

![optimal skill  for Data Analyts in US](images\most_optimal_skills.png)

#### insights

-Scatter plot shows that programming-related skills like Python command the highest median salaries for Data Analysts.
-Analytical tools like Power BI and Tableau appear in a significant portion of Data Analyst jobs.and they provide a good balance between demand and salary, around the $90k–$93k range.
-Database-related skills like SQL, Oracle, and SQL Server offer strong salaries; SQL is highly in demand, while Oracle and SQL Server remain valuable specialized skills.

Throughout this project, I strengthened my grasp of the data analyst job market while sharpening my Python skills, particularly in working with libraries and plotting data. Here are the key takeaways:

# What I Learned:

- **Mastered Python Libraries**: I learned to leverage Pandas for efficient data handling, and used Seaborn and Matplotlib to plot data and create clear, insightful visualizations.
- **Recognized Data Prep as a Core Step**: I discovered that cleaning and structuring data upfront is non-negotiable—it directly determines the reliability of any analysis.
- **Linked Skills to Market Needs**: The project showed me how to map in-demand skills to real job trends and salary potential, enabling smarter, data-driven career moves in tech.

#### Insights

**Skill Demand and Salary Correlation**: There is a clear correlation between the demand for specific skills and the salaries these skills command.

**Market Trends**: There are changing trends in skill demand, highlighting the dynamic nature of the data job market. Keeping up with these trends is essential for career growth in data analytics.

# Challenges I Faced

This project threw curveballs my way, but each one sharpened my skills:

- **Data Cleaning Mastery**: I wrestled with messy, incomplete, or inconsistent records and learned that **robust cleaning techniques** are the foundation of trustworthy analysis—skip this step, and everything crumbles.
- **Advanced Data Visualization Parameters**: Plotting complex datasets pushed me to explore **new visualization parameters** (like custom color maps, interactive elements, and layered plots in Seaborn/Matplotlib), turning raw numbers into clear, compelling stories.

# Conclusion

This deep dive into the data analyst job market revealed powerful trends and must-have skills that define success in this dynamic space. The findings sharpened my perspective and offer clear, practical steps for anyone aiming to thrive in data analytics. With the industry constantly shifting, regular market check-ins will be key to staying competitive. This work lays a solid base for future research and reinforces that lifelong learning and flexibility are non-negotiable in the world of data.
