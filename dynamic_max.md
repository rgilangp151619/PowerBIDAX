In Max Axis Qty = 
VAR _CUR = MAXX(ALLSELECTED('Calendar'[Date].[Month]), [In Total Qty])
VAR _Last = MAXX(ALLSELECTED('Calendar'[Date].[Month]), [In Prev Year Total Qty])
RETURN
IF(_CUR > _Last, _CUR, _Last) * 1.1
