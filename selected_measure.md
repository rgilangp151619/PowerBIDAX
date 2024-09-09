3_Selected Measure = 
SWITCH(
    SELECTEDVALUE('Measure Sel'[Measure Name]),
    "New Followers", [1_New Followers],
    "Total Engagements", [1_Total Engagements],
    "Total Impressions", [1_Total Impressions])
