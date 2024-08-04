In Max Label = 
VAR _CUR = MAXX(ALLSELECTED('Calendar'[Date].[Month]), [Total Ticket Raised])
VAR _Last = MAXX(ALLSELECTED('Calendar'[Date].[Month]), [Total Ticket Solved])
RETURN
IF(_CUR > _Last, _CUR, _Last) * 1.1
