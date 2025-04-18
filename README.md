# PwC-Switzerland-Power-BI-Diversity-and-Inclusion-Dashboard
# Background Information of task:
Human Resources at our telecom client is highly into diversity and inclusion. They’ve been working hard to improve gender balance at the executive management level, but they’re not seeing any progress. 
They’re reaching out to us for help.

At PwC Switzerland we are often approached by clients seeking support with diversity and inclusion. Companies need a workforce of diverse talents and backgrounds to succeed in an increasingly complex and heterogeneous world. 
To us, diversity and inclusion are business imperatives, not just nice-to-haves. We aim for all of our teams to feel welcome and appreciated. But actually achieving this and unlocking its potential involves a whole set of practical challenges.

# Why is this so:

-> Think about the importance of strategy, awareness and education, analytics and inspiration. 
   Here is a hint: Calculating the following measures could help to define proper KPIs:

1) Count of men
2) Count of women
3) Count of leavers
4) % employees promoted (FY21)
5) % of women promoted
6) % of hires men
7) % of hires women
8) % turnover 
9) Average performance rating: men
10) Average Performance rating: women

# Here is the task:

1. Define relevant KPIs in hiring, promotion, performance and turnover, and create a visualisation
2. Write what you think some root causes of their slow progress might be

# DAX commands used:
Total Women Promoted _2021 = 
VAR WomenPromoted = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[Promotion in FY21?] = "Yes",
        'Pharma Group AG'[Gender] = "Female"
    )
VAR TotalWomen = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[Gender] = "Female"
    )
RETURN 
    DIVIDE(WomenPromoted, TotalWomen, 0)

Count of Leavers = 
CALCULATE(
    COUNT('Pharma Group AG'[Employee ID]),
    'Pharma Group AG'[FY20 leaver?] = "Yes"
)

% Turnover = 
VAR TotalEmployees = COUNT('Pharma Group AG'[Employee ID])
VAR Leavers = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[FY20 leaver?] = "Yes"
    )
RETURN 
    DIVIDE(Leavers, TotalEmployees, 0)

Avg Performance Rating Men in FY19 = 
CALCULATE(
    AVERAGE('Pharma Group AG'[FY19 Performance Rating]),
    'Pharma Group AG'[Gender] = "Male"
)

Percentage of Hires Women = 
VAR HiredWomen = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[New hire FY20?] = "Yes",
        'Pharma Group AG'[Gender] = "Female"
    )
VAR TotalHires = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[New hire FY20?] = "Yes"
    )
RETURN 
    DIVIDE(HiredWomen, TotalHires, 0)

Percentage of Turnover = 
VAR TotalEmployees = COUNT('Pharma Group AG'[Employee ID])
VAR Leavers = 
    CALCULATE(
        COUNT('Pharma Group AG'[Employee ID]),
        'Pharma Group AG'[FY20 leaver?] = "Yes"
    )
RETURN 
    DIVIDE(Leavers, TotalEmployees, 0)
