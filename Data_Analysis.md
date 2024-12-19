# Data Analysis

The relationships between tables in the data model provides a structured basis and framework to the data analyses that can be performed which include:

- Understanding employee performance trend
- Skill and competency analysis
- Employee demorgraphics and diversity
- Employee retention and turnover analysis
- Operational efficiency and workforce planning
These analyses allows us to explore complex questions and to drive meaningful conclusions that can inform strategic decisions and improve organizational outcomes.

## DAX
The following DAX formulas are some of the DAX used for advanced calculations and dynamic analysis on top of the structured data model:

- Starting Headcount = 
var snapshotdt = (min(CALENDAR[DATE KEY]))
RETURN 
IF(
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[AS OF DATE]<=snapshotdt && T_EMP_HIST[END DATE]>=snapshotdt &&  T_EMP_HIST[RECORD REASON SYS ID] <> 1000) = BLANK(),0,
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[AS OF DATE]<=snapshotdt && T_EMP_HIST[END DATE]>=snapshotdt && T_EMP_HIST[RECORD REASON SYS ID] <> 1000 ))

- Headcount = 
var snapshotdt = (max(CALENDAR[DATE KEY]))
RETURN 
IF(
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[AS OF DATE]<=snapshotdt && T_EMP_HIST[END DATE]>=snapshotdt &&  T_EMP_HIST[STATUS] = "Active" ) = BLANK(),0,
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[AS OF DATE]<=snapshotdt && T_EMP_HIST[END DATE]>=snapshotdt &&  T_EMP_HIST[STATUS] = "Active" ))

- Retention Rate = 
var stdt = MIN('CALENDAR'[DATE KEY])
var enddt = MAX('CALENDAR'[DATE KEY])
var stlist = CALCULATETABLE( VALUES(T_EMP_HIST[EMPLOYEE SYS ID]),T_EMP_HIST[START DATE]<stdt,T_EMP_HIST[AS OF DATE]<=stdt,T_EMP_HIST[END DATE]>=stdt,T_EMP_HIST[RECORD REASON SYS ID]<>1000 )
var endlist = CALCULATETABLE( VALUES(T_EMP_HIST[EMPLOYEE SYS ID]),T_EMP_HIST[START DATE]<stdt,T_EMP_HIST[AS OF DATE]<=enddt,T_EMP_HIST[END DATE]>=enddt,T_EMP_HIST[RECORD REASON SYS ID]<>1000 )
RETURN 
CALCULATE(COUNTROWS(
DISTINCT(INTERSECT(stlist, endlist)) )
)

/ 
CALCULATE(COUNTROWS(stlist))

- Turnover Rate = 
CALCULATE(
(IF( [Total Exits] = BLANK(),0,[Total Exits]))
/
(
(var stdt = min('CALENDAR'[DATE KEY])
var enddt = MAX('CALENDAR'[DATE KEY]) 
RETURN 
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[START DATE]<=stdt,
(T_EMP_HIST[AS OF DATE]<=stdt && T_EMP_HIST[END DATE] >= stdt  && T_EMP_HIST[RECORD REASON SYS ID] <> 1000 ))
+ 
CALCULATE(DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]),
T_EMP_HIST[START DATE]<=enddt,
(T_EMP_HIST[AS OF DATE]<=enddt && T_EMP_HIST[END DATE] >= enddt  && T_EMP_HIST[RECORD REASON SYS ID] <> 1000 ))

  )/2))

- Total Exits = 
var mindt = (Min(CALENDAR[DATE KEY]))
var maxdt = (MAX(CALENDAR[DATE KEY]))
RETURN 
IF(CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]), 
(T_EMP_HIST[AS OF DATE] >=mindt && T_EMP_HIST[AS OF DATE] <= maxdt && T_EMP_HIST[RECORD REASON SYS ID]=1000)) = BLANK(),0,
CALCULATE(
DISTINCTCOUNT(T_EMP_HIST[EMPLOYEE SYS ID]), 
(T_EMP_HIST[AS OF DATE] >=mindt && T_EMP_HIST[AS OF DATE] <= maxdt && T_EMP_HIST[RECORD REASON SYS ID]=1000)))

- Performance Reviews = 
var mindt = (min(CALENDAR[DATE KEY]))
var maxdt = (max(CALENDAR[DATE KEY]))
RETURN
IF(CALCULATE(
    COUNTROWS(T_PERFORMANCE),T_PERFORMANCE[REVIEW DATE]>=mindt, T_PERFORMANCE[REVIEW DATE]<=maxdt) = BLANK(),
    0,
   CALCULATE(COUNTROWS(T_PERFORMANCE),T_PERFORMANCE[REVIEW DATE]>=mindt, T_PERFORMANCE[REVIEW DATE]<=maxdt)
    )

- Low Performers % = 
var mindt = (min(CALENDAR[DATE KEY]))
var maxdt = (max(CALENDAR[DATE KEY]))
RETURN IFERROR(IF(
ISBLANK(CALCULATE(COUNTROWS(T_PERFORMANCE), T_PERFORMANCE[PERFORMANCE]="Low", T_PERFORMANCE[REVIEW DATE] >=mindt, T_PERFORMANCE[REVIEW DATE]<=maxdt)),0,
CALCULATE(COUNTROWS(T_PERFORMANCE), T_PERFORMANCE[PERFORMANCE]="Low", T_PERFORMANCE[REVIEW DATE] >=mindt, T_PERFORMANCE[REVIEW DATE]<=maxdt)
)/'Metric Library'[Performance Reviews],"")

- Skill Needed Employees = 
IF ( CALCULATE( DISTINCTCOUNT(T_EMP_SKILLS[EMPLOYEE SYS ID]), T_SKILL_LEVEL_EXP[SKILL LEVEL] <>"None", T_EMP_CURR[CURRENT EMPLOYEE STATUS]="Active") = BLANK(),0,
CALCULATE( DISTINCTCOUNT(T_EMP_SKILLS[EMPLOYEE SYS ID]),  T_SKILL_LEVEL_EXP[SKILL LEVEL] <>"None",T_EMP_CURR[CURRENT EMPLOYEE STATUS]="Active"))

- Underskilled Employees = 
IF ( CALCULATE( DISTINCTCOUNT(T_EMP_SKILLS[EMPLOYEE SYS ID]),T_EMP_SKILLS[Skilled]=0, T_EMP_CURR[CURRENT EMPLOYEE STATUS]="Active") = BLANK(),0,
CALCULATE( DISTINCTCOUNT(T_EMP_SKILLS[EMPLOYEE SYS ID]),T_EMP_SKILLS[Skilled]=0, T_EMP_CURR[CURRENT EMPLOYEE STATUS]="Active"))

- Underskilled Employee % = IFERROR(('Metric Library'[Underskilled Employees]/'Metric Library'[Skill Needed Employees]),"")

All the DAX measures calculated for this project have an objective meaning that helps monitor specific performance.
