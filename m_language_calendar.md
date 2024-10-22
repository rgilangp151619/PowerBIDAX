let
    StartDate = #date(2024,1,1),
    EndDate = #date(2024,12,31),
    NumberOfDays = Duration.Days( EndDate - StartDate ),
    Dates = List.Dates(StartDate, NumberOfDays+1, #duration(1,0,0,0)),
    #"Converted to Table" = Table.FromList(Dates, Splitter.SplitByNothing(), null, null, ExtraValues.Error),
    #"Changed Type" = Table.TransformColumnTypes(#"Converted to Table",{{"Column1", type date}}),
    #"Renamed Columns" = Table.RenameColumns(#"Changed Type",{{"Column1", "Date"}}),
    #"Inserted Year" = Table.AddColumn(#"Renamed Columns", "Year", each Date.Year([Date]), Int64.Type),
    #"Inserted Quarter" = Table.AddColumn(#"Inserted Year", "Quarter", each Date.QuarterOfYear([Date]), Int64.Type),
    #"Inserted Month" = Table.AddColumn(#"Inserted Quarter", "Month", each Date.Month([Date]), Int64.Type),
    #"Inserted Month Name" = Table.AddColumn(#"Inserted Month", "Month Name", each Date.MonthName([Date]), type text),
    #"Inserted Day Name" = Table.AddColumn(#"Inserted Month Name", "Day Name", each Date.DayOfWeekName([Date]), type text),
    #"Inserted Day of Week" = Table.AddColumn(#"Inserted Day Name", "Day of Week", each Date.DayOfWeek([Date]), Int64.Type),
    #"Added Custom" = Table.AddColumn(#"Inserted Day of Week", "Quarter.1", each "Q" & [Quarter] & "-" & [Year]),
    #"Removed Columns" = Table.RemoveColumns(#"Added Custom",{"Quarter.1"}),
    #"Added Custom1" = Table.AddColumn(#"Removed Columns", "Custom", each "Q" & Number.ToText([Quarter])),
    #"Renamed Columns1" = Table.RenameColumns(#"Added Custom1",{{"Custom", "Quarter.1"}}),
    #"Added Custom2" = Table.AddColumn(#"Renamed Columns1", "Year Quarter", each [Quarter.1] &"-" & Number.ToText([Year])),
    #"Added Custom3" = Table.AddColumn(#"Added Custom2", "Year Month", each [Month Name] & " " & Number.ToText([Year]))
in
    #"Added Custom3"
