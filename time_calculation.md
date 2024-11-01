AVERAGE Lead Time = 
VAR TotalSeconds = 
    AVERAGEX(
        'Table',
        HOUR('Table'[Column]) * 3600 + 
        MINUTE('Table'[Column]) * 60 + 
        SECOND('Table'[Column])
    )
RETURN
    TIME(
        INT(TotalSeconds / 3600),            // Hours
        INT(MOD(TotalSeconds, 3600) / 60),   // Minutes
        MOD(TotalSeconds, 60)                // Seconds
    )
