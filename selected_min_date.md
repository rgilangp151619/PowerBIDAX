3_Selected Min Date = 
Var MaxDate = [2_MaxDate] +1
VAR MinDate = [2_MinDate] -1
RETURN

SWITCH([3_Selected Dates],
    "1W",MaxDate -7,
    "1M",EDATE(MaxDate, -1),
    "3M",EDATE(MaxDate, -3),
    "TY",DATE(YEAR(MaxDate), 1, 1),
    "1Y",EDATE(MaxDate, -12),
    "ALL",MinDate )
