7_SM Past Period Reference Label = 


var _Current = [4_SM Date Param]
var _LY = [4_SM Date Param Past Period]
var _Growth = DIVIDE(_Current - _LY, _LY)
VAR NumOfDigits =
    IFERROR(
            LEN( 
                CONVERT( 
                        INT( 
                           [4_SM Date Param])
                        , STRING ))
            ,0)
VAR Suffix =
    ".0" &
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
return
IF (_Growth <> 0, 
    
"" &FORMAT(_Current-_LY, _Format)
    &  
        FORMAT(_Growth," | 0.0% ▲; | 0.0% ▼;")& ""," ")
