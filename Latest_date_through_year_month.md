latest_date = 
VAR latestdate = calculate(max('Subs and Acc for OACT'[Original Submission Date]), All())
RETURN latestdate - WEEKDAY(latestdate,2) + 1

EO Last Full month updated to = EOMONTH(CALCULATE('Latest date run'[latest_date]),-1) // shows the latest full month updated to

EO Month Last Full Month no filter = CALCULATE([EO Last Full month updated to], all('Calendar'))

% through month = VAR curr_day_no = day([latest_date])
VAR days_in_month = day(eomonth([latest_date],0))
VAR pct = divide(curr_day_no, days_in_month)

VAR pct_fixed = if(Max('Calendar'[Date]) > [EO Month Last Full Month no filter], pct, 1)
RETURN pct_fixed


% through year = YEARFRAC("Jan 1 2025", 'Latest date run'[latest_date],3)


Latest date run query = let
    Source = Table.Combine({#"Latest Invoiced OA",  #"Latest Dove Article Level"}), // combines 2 queries that take latest date from the tables 
    #"Sorted Rows" = Table.Sort(Source,{{"Date", Order.Descending}})
in
    #"Sorted Rows"
