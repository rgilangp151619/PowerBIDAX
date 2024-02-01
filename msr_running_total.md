[Measure Name] = 
CALCULATE(
    [Measure to be Calculate],
    DATESINPERIOD(
        'Calendar'[Date],
        MAX(
            'Calendar'[Date]
        ),
        [-How many period based on max calendar date],
    MONTH)
)
