### Audit report
<img width="587" alt="visualization" src="https://github.com/user-attachments/assets/92389f48-939f-429e-a0f3-6f90f5b4b35b">

#### Test for outliers in transaction amount
- I tested for outliers using the inter-quartile range approach and discovered no outliers. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/1.%20outlier%20detection%20using%20IQR.png).
- I tested with a different approach by outputting amounts that were more than 3 standard deviations from the mean, and still discovered no outliers. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/2.%20outlier%20detection%20using%20mean_std.png).

#### Test for transaction timing
- I wrote queries to compare total vs fraudulent transactions by
  - hour 
  - day of week. 

#### Test for fraudulent hours 
- I queried the database to return the hours where the proportion of fraud per hour is greater than the proportion of fraud per day. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/4.%20fraud_hour_gt_day.png).
- Then I wrapped the result in a view called **VIEW_pct_fraudulent_TX_hour_gt_day**.
- I queried this view to return the number of occurrences per hour and I discovered that 12am, 1am, 2am and 10pm are the hours with the most number of occurrences where their proportion of fraud is greater than the proportion of fraud for the entire day. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/5.%20occurrences_fraud_hour_gt_day.png).

#### High value transaction test
- I calculated the proportion of fraud for transactions above 900 (High) and below 900 (Low).
- I discovered that low-value transactions had a higher proportion of fraud (4.7%) compared to high-value transactions (4.5%). [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/3.%20high%20value%20TX%20test.png).
