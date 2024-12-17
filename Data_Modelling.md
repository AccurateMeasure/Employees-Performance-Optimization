# Power BI Report Model

The modelling schema type used for this project is known as snowflake schema. This is because the dimension tables are normalized with some connected to other dimension tables, creating a more complex network rather than a straight forward star schema. The model design have a disconnected date dimension table and measures table to improve dynamic interactions, organize measures for easy maintenance and better collaborations. This model design also helps in reducing data redundancy and improving query performance by breaking down the dimensions into related tables as seen in the diagram below:

![PowerBI Report Model](https://github.com/user-attachments/assets/91742b95-8d6e-4515-aa76-9c4dbefe0f30)

This model is made of 3 facts tables and 23 dimensions tables namely:

## Facts Tables
  - T_Emp_Hist
  - T_Emp_Curr
  - T_Performance

## Dimensions Tables
  - T_Employees
  - T_Department
  - T_JobLevel
  - T_Location
  - T_JobCategory
  - T_JobType
  - T_SalaryGrade
  - T_Ethnicity
  - T_Gender
  - T_HireSource
  - T_ExitReason
  - T_ExitType
  - T_Perf_Boxes
  - T_Perf_Periods
  - T_RecordReason
  - T_Skill_Level_Exp
  - T_Emp_Skill
  - T_Skill_Level
  - T_Skills
  - Calendar
  - T_Weekend
  - T_Hols
    
with a fact to fact relationship between T_Performance and T_Emp_Hist which allows performance to be analyzed in the context of employees historical changes.
