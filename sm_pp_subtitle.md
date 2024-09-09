7_SM Past Period subtitle = 
var _LY = [4_SM Date Param Past Period]
VAR NumOfDigits =
    IFERROR(
            LEN( 
                CONVERT( 
                        INT( 
                           _LY)
                        , STRING ))
            ,0)
VAR Suffix =
    ".00" &
    SWITCH(
        TRUE( ),
        NumOfDigits >= 13,  "T",
        NumOfDigits >= 10,  "B",
        NumOfDigits >= 7,   "M",
        NumOfDigits >= 4,   "K"
    )
VAR Commas =
    REPT(",",
        SWITCH(
            TRUE( ),
            NumOfDigits >= 13,  "4",
            NumOfDigits >= 10,  "3",
            NumOfDigits >= 7,   "2",
            NumOfDigits >= 4,   "1"
        )
    )
var _Format =     "#,##0" & Commas & Suffix & ";-#,##0" & Commas &Suffix 
var _Time = 
    SWITCH([3_Selected Dates],
    "1W", "Previous Week: ",
    "1M","Previous Month: ",
    "3M","Previous 3 Months: ",
    "TY","Previous Year Period: ",
    "1Y","Previous Year: ")
return
_Time  &FORMAT(_LY, _Format)
