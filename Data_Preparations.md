# Dataset Preparations/Transformations

The T_Employees, T_Employee_updates, T_Exits, T_Perfromance, and T_Emp_skills tables were further prepared and transformed using PowerQuery editor and MDx code to apply the following transformations which resulted to the 26 tables detailed below:

## Preparations/Transformations
  
  - Remove errors and blank rows from EmployeeNumber column
  - Ensure and change data type to fit the each column data
  - Merge columns using Add column by example
  - Merge Tables(queries)
  - Append Tables(queries)
  - Unpivot columns
  - Pivot columns
  - Group Table in Advanced mode
  - Add index columns
  - Filter rows with specific column values
  - Perform calculations
  - Delete columns
  - Remove Duplicate
  - Rename columns
  - Create to two parameters(StartYear and EndYear)
  - Create date table using StartYear and EndYear parameters

## Resulting Tables

  - T_Employees
    Columns: EmployeeSysID, Employee, Email, Age, Department, Location, StartDate, EndDate, JobType, JobCategory, JobLevel, JobTitle, Manager, Salary, AgeGroup(current), Tenure, TenureGroup(current), GenderSysID,            HireSourceSysID, EthnicitySysID

  - T_Emp_Hist
    Columns: EmployeeSysID, LastUpdatedDate, AsOfDate, Salary, LocationSysID, DepartmentSysID, JobTypeSysID, JobCategorySysID, JobLevelSysID, JobTitleSysID, ExitTypeSysID, ExitReasonSysID, SalaryGradeSysID,                  RecordReasonSysID, CurrentRecord, HistoryRow, EndDate, Status, ExitDate, Tenure(AtExit), TenureGroup(AtExit), StartDate, RegrettableExit

  - T_Emp_Curr
    Columns: EmployeeSysID, LastUpdatedDate, AsOfDate, Salary, LocationSysID, DepartmentSysID, JobTypeSysID, JobCategorySysID, JobLevelSysID, JobTitleSysID, ExitTypeSysID, ExitReasonSysID, SalaryGradeSysID,                  RecordReasonSysID, HistoryRow, EndDate, Status, ExitDate, Tenure(AtExit), TenureGroup(AtExit), StartDate, RegrettableExit

  - T_ExitReason
    Columns: ExitReasonSysID, ExitReason

  - T_ExitType
    Columns: ExitTypeSysID, ExitType

  - T_RecordReason
    Columns: RecordReasonSysID, RecordReason

  - T_Department
    Columns: DepartmentSysID, Department

  - T_JobLevel 
    Columns: JobLevelSysID, JobLevel

  - T_Location
    Columns: LocationSysID, Location

  - T_JobType
    Columns: JobTypeSysID, JobType

  - T_JobCategory 
    Columns: JobCategorySysID, JobCategory

  - T_SalaryGrade
    Columns: SalaryGradeSysID, SalaryGrade

  - T_Ethnicity
    Columns: EthnicitySysID, Ethnicity

  - T_Gender
    Columns: GenderSysID, Gender

  - T_HireSource
    Columns: HireSourceSysID, HireSource

  - T_Performance
    Columns: EmployeeSysID, HistoryRow, Employee, ReviewPeriod, ReviewDate, Performance, Potential, 9Box, Salary(AtReview), StartDate, Tenure(AtReview), TenureGroup(AtReview), Age(AtReview), AgeGroup(AtReview),              LastPerformance, TenureGroupOrder, Feedback

  - T_Perf_Boxes
    Columns: BoxName, BoxCombo, PerformanceNum, PotentialNum, PerformanceLevel, PotentialLevel

  - T_Perf_Period
    Columns: Date, ReviewPeriod

  - T_Emp_Skill
    Columns: EmployeeSysID, SkillSysID, ActualSkillLevel_ID, ExpectedSkillLevel_ID, Skilled

  - T_Skill_Level_Exp
    Columns: SkillLevelSysID, SkillLevel

  - T_Skill_Level
    Columns: SkillLevelSysID, SkillLevel

  - T_Skills
    Columns: SkillSysID, Skill

  - Calender
    Columns: DateKey, Year, MonthNumber,MonthName, Quarter, WeekOfYear, WeekOfMonth, Day, DayOfWeek, DayOfYear, DayName, FutureDate, MonthEndDate, MonthStartDate, Month, WeekStartDate, WeekendIndx, HolidayIndx,              LastDayOfMonthIndx 

  - T_Weekend
    Columns: Weekday, Weekend, WeekendIndx

  - T_Hols
    Columns: Date, Hol_Indx



