Rolling 6 month acceptance rate = CALCULATE([Acceptance Rate],DATESINPERIOD('Calendar'[Date],MAX('Calendar'[Date]),-6,MONTH),USERELATIONSHIP('Calendar'[Date],'Article key'[decision date]))
