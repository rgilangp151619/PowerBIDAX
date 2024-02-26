Measure = 
VAR _KPI = [Actual]
VAR _Target = [Target]
VAR _Value = FORMAT(DIVIDE([Actual], [Target]) - 1,"#0.0%")
VAR _abovetext = "▲% Target"
VAR _belowtext = "▼% Target"
VAR _Space = REPT("‏‏‎ ‎",3)
VAR _Label = 
    IF(_KPI > _Target,
    _Space & _abovetext & _Space & _Value,
    _Space & _belowtext & _Space & _Value)
RETURN
    _Label
