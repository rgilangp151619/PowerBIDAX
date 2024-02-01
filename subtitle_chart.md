Subtitle Measure = 
VAR trendMoM = [% Measure]

VAR MOMLine = 
IF(trendMoM >0,
"Prev. Month ▲" & CONVERT(FORMAT([% Measure],"+#.0%;-#.0%"),STRING)& " | " &  CONVERT(FORMAT([Prev Month],"€ #,0"),STRING),
"Prev. Month ▼" & CONVERT(FORMAT([% Measure],"+#.0%;-#.0%"),STRING)& " | " &  CONVERT(FORMAT([Prev Month],"€ #,0"),STRING))

Return
MOMLine & UNICHAR(10)
