2_MaxDate = 
CALCULATE(
    MAX(Data[Date]),
    REMOVEFILTERS('Date'[Date]))
