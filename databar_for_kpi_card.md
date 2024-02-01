Data Bar - xx vs xx = 
VAR _NrIcons_Total = 10 --how long the bar
VAR _PCtOfTarget = MIN(DIVIDE([Actual], [Target]),1)
VAR _NrIcons_Fill = _PCtOfTarget * _NrIcons_Total
VAR _Nricons_Empty = _NrIcons_Total - _NrIcons_Fill

VAR _IconFill = "█"
VAR _IconEmpty = "░"

VAR _DataBar = 
    REPT(_IconFill, _NrIcons_Fill) & 
    REPT(_IconEmpty, _Nricons_Empty)

RETURN
    _DataBar
