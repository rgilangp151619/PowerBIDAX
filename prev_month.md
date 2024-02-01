Prev Month = 
CALCULATE(
          [Measure], 
          DATEADD(
                  'Calendar'[Date],
                  -1,MONTH
                  )
        )
