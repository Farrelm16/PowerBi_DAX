% Article Budget (Proc) = divide([Processed Articles], [Article Budget],"")

Ratio of % Proc to % th month = DIVIDE('Processed Articles'[% Article Budget (Proc)], [% through month], blank())

% FY Article Budget Achieved (Proc) = divide([YTD Processed Articles],[FY Article Budget],blank())

Ratio of % FY Processed to % th year = DIVIDE([% FY Article Budget Achieved (Proc)], [% through year], blank())

Ratio formatting is then red if >= 0 and < 95%, orange if >= 95% and < 100% and green if >= 100%
