# Dataset

The dataset used for this project is a sample data stored in excel file format. The employees names and other personal identifiers are fictional to protect individual identities following the practice known as pseudonymization.
The datasets are from five(5) tables namely : T_Employees, T_Employee_updates, T_Exits, T_Performance and T_Emp_skills.

## T_Employees
T_Employees table provide distinct employees details at first startdate in the organization and have 15 columns which include: 
Employee first name,  Employee last name, Employee number, Email, Date of birth, Start date, Gender, Ethnicity, Hiresource, Location, Department, Job type, Job category, Job leve, Job title, Manager, Salary, and Salary grade.

## T_Employee_updates
T_Employee_updates table show all employees job related updates except employees exit update. Updates are made in T_Employee_updates table only for the following 5 reasons(RecordReason): Job change(lateral), Job change(promotion), Job change(downgrade),
Salary change(increase), Salary change(decrease), Team change. The T_Employee_updates table have 12 columns which include:
Employee number, As of date, RecordReason, Location, Department, Job type, Job category, Job level, Job title, Manager, Salary, Salary grade. 

## T_Exits
T_Exits table show details of all employees that exited the organization. T_Exits table carries 3 columns which include: Employee number, Exit date, and Exit reason(which could be for Carrier growth, Compensation, Culture fit, Policy violation, Retirement, 
Work performance or Other)

## T_Performance
T_Performance table provide potential and performance informations of all the employees at each review period. The table have 6 columns namely: Employee number, Review period, Review date, Performance(low, medium, high), Potential(low, medium, high), and Feedback.

## T_Emp_skills
T_Emp_skills table shows the Actual, A and Expected E skills attribute for each employee (which can be None, Low, Medium or High). T_Emp_skills table carries 10 columns which include: 
Employee number, Skill profile = Job title, Skill 1A, Skill 1E, Skill 2A, Skill 2E, Skill 3A, Skill 3E, Skill 4A, Skill 4E, Skill 5A, Skill 5E (where Skill 1 = Project management, Skill 2 = Communication, Skill 3 = Strategic thinking, Skill 4 = Data Analysis
Skill 5 = Technical).
