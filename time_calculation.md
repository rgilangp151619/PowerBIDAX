Receipt Duration = 
IF(
    'Inbound'[START CHECKING DATE] = 'Inbound'[Complete Posting 1 Date_1],
    TIME(0,0,0),
    TIME(
        INT(
            ABS(DATEDIFF(
                'Inbound'[Complete Posting 1 Date_1],
                'Inbound'[START CHECKING DATE],
                SECOND
            )) / 3600
        ),
        INT(
            MOD(
                ABS(DATEDIFF(
                    'Inbound'[Complete Posting 1 Date_1],
                    'Inbound'[START CHECKING DATE],
                    SECOND
                )),
                3600
            ) / 60
        ),
        MOD(
            ABS(DATEDIFF(
                'Inbound'[Complete Posting 1 Date_1],
                'Inbound'[START CHECKING DATE],
                SECOND
            )),
            60
        )
    )
)
