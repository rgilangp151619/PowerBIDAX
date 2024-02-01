Color Format Allocation Cost = 
VAR var_1 = [Measure 1]
VAR var_2 = [Measure 2]
VAR Result = 
SWITCH( TRUE(),
var_1 < var_2, "#FFCC00",
var_1 > var_2, "#D40511")
Return
Result
