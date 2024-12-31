Lag1 = 
VAR PreviousRow =
    CALCULATE(
        MAX('MHE Utilization'[Hours Meter]),
        FILTER(
            'MHE Utilization',
            'MHE Utilization'[Index] = EARLIER('MHE Utilization'[Index]) - 1
        )
    )
RETURN
    PreviousRow
