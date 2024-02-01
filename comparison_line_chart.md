Measure Name = 
VAR _costvsrev = 
CALCULATE(
    [Measure to be compared],
    ALL(Table with distinct category), 
    [Table with distinct category + baseline]  IN ALLSELECTED(table with distinct category but not related to other table)
)
VAR _Result = 
IF(
    SELECTEDVALUE(Table with distinct category + baseline) = "Baseline", 
    _costvsrev,
    [Measure to be compared]
)
RETURN
_Result
