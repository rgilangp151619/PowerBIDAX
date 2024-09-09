2_MinDate = 
CALCULATE(
    MIN(Data[Date]),
    REMOVEFILTERS('Date'[Date]))
