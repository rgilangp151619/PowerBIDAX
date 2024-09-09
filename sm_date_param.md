4_SM Date Param = 
CALCULATE(
    [3_Selected Measure],
    KEEPFILTERS(
        DATESBETWEEN(
            'Date'[Date],                 
            [3_Selected Min Date],
            [2_MaxDate]
         ))
    )
