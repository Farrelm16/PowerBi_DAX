Calendar = 
// This script automatically creates a full DimDate table based on the data provided
ADDCOLUMNS (
CALENDAR (MINX('Prepublication dates v1','Prepublication dates v1'[submitted]), "31/12/"&YEAR(TODAY())),   // Could use MAXX of date instead of "31/12/"&YEAR(TODAY())
"DateAsInteger", FORMAT ( [Date], "YYYYMMDD" ),   // Use for sorting
"Year", YEAR ( [Date] ),
"Monthnumber", FORMAT ( [Date], "MM" ),
"YearMonthnumber", FORMAT ( [Date], "YYYYMM" ),  // Use for sorting
"Year Month",format([Date],"YYYY mmm"),
"Month Year", FORMAT ( [Date], "mmm YYYY" ),
"Month", FORMAT ( [Date], "mmm" ),
"MonthNameLong", FORMAT ( [Date], "mmmm" ),
"DayOfWeekNumber", WEEKDAY ( [Date],2 ),
"DayOfWeek", FORMAT ( [Date], "dddd" ),
"DayOfWeekShort", FORMAT ( [Date], "ddd" ),
"Quarter", "Q" & FORMAT ( [Date], "Q" ),
"Year Quarter", FORMAT ( [Date], "YYYY" ) & "/Q" & FORMAT ( [Date], "Q" ),
"Week", weeknum([Date],2) ,
"Year Week", format([Date], "YYYY") & ":" & format(weeknum([Date],2),"00")
) 
