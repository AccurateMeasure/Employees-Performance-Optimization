# Dataset Preparations/Transformations

The T_Employees, T_Employee_updates, T_Exits, T_Perfromance, and T_Emp_skills tables were further prepared and transformed using PowerQuery editor as detailed below:

## T_Employees Transformations

- Add column by example named Employee, that merges Employee FirstName, LastName and EmployeeNumber
- Remove error and blank rows from EmployeeNumber column
- Add index column named Employee sys ID
- Remove FirstName and LastName column
- Add new column Age that calculates Age using date of birth column
- Create AgeGrp column
- Add Tenure column using each Employee start date
- Add Tenure Grp 
- Change data type to match the data in each column.
- Create 9 duplicate queries with the following names and transformations.
         Name           |  Transformations
  1) T_Department       |  Select the Department column, then remove other columns and remove duplicates in departments column, Add index column named Department sys ID
  2) T_JobLevel         |  Select the JobLevel column, then remove other columns and remove duplicates in JobLevel column, Add index column named JobLevel sys ID
  3) T_Location         |  Select the Location column, then remove other columns and remove duplicates in Location column, Add index column named Location sys ID
  4) T_JobType          |  Select the JobType column, then remove other columns and remove duplicates in JobType column, Add index column named JobType sys ID
  5) T_JobCategory      |  Select the JobCategory column, then remove other columns and remove duplicates in JobCategory, Add index column named JobCategory sys ID
  6) T_SalaryGrade      |  Select the SalaryGrade column, then remove other columns and duplicates SalaryGrade, Add index column named SalaryGrade sys ID
  7) T_Ethnicity        |  Select the Ethnicity column, then remove other columns and remove duplicates Ethnicity, Add index column named Ethnicity sys ID
  8) T_Gender           |  Select the Gender column, then remove other columns and remove duplicates Gender, Add index column named Gender sys ID
  9) T_HireSource       |  Select the HireSource column, then remove other columns and remove duplicates HireSource, Add index column named HireSource sys ID
- Create a reference query T_Emp_Prep from T_Employees table and apply the following transformations
  1) Add new column RecordReason sys ID as 0 which represents new employees.
  2) Rename StartDate column to As of Date
  3) Merge T_Emp_Prep with T_Department, T_JobLevel, T_Location, T_JobType, T_JobCategory, T_SalaryGrade, T_Ethnicity, T_Gender, and T_HireSource using left join and expand to keep only
     their respective sys IDs
  4) Remove all the Non-IDs columns except the salary column


  ## T_Employee_updates
       




