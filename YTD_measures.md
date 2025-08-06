Date max for YTD measures = date(2025,08,01) // Month plus one

Date min for YTD measures = date(2017,1,1) // Start date

YTD Article Budget = 
VAR date_min = [Date min for YTD measures]
VAR date_max = [Date max for YTD measures]
VAR val = CALCULATE([Base measure], DATESYTD('Calendar'[Date]))
VAR date_viewing = max('Calendar'[Date])
RETURN if((date_viewing>=date_min), val, BLANK())

% Variance to YTD Article Budget (Accepted) = Divide(([YTD Accepted] - [YTD Article Budget]), [YTD Article Budget], blank())

YTD ELM Articles Budget = CALCULATE([YTD Article Budget],DATEADD('Calendar'[Date],-1,Month))
