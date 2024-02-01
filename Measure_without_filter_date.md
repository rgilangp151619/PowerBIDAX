GP Remove Filter = 
CALCULATE(
    [Total GP], REMOVEFILTERS('Calendar'[Date].[Month]))
