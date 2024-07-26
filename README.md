### Executive summary
Using SQL, I performed some audit tests to assess the integrity of financial transactions processed through a fictional company's platform. I visualized the results using Power BI and provided some recommendations.

### Audit tests
#### 1. Test for outliers in transaction amount
- I tested for outliers using the inter-quartile range approach. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/1.%20outlier%20detection%20using%20IQR.png).
- I tested with a different approach by outputting amounts that were more than 3 standard deviations from the mean. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/2.%20outlier%20detection%20using%20mean_std.png).

**Result:** No outliers.

#### 2. Test for transaction timing
- I wrote queries to compare total vs fraudulent transactions by
  - hour [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/6.%20fraud_by_hour.png).
  - day of week [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/7.%20fraud_by_day.png).

**Result:** The hour with the highest proportion of fraud (6.6%) was 2am. The day with the highest proportion of fraud was Tuesday (5.8%).

#### 3. Test for hours with higher fraud proportions above the entire day
- I queried the database to return the hours where the proportion of fraud per hour is greater than the proportion of fraud per day. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/4.%20fraud_hour_gt_day.png).
- Then I wrapped the result in a view called **VIEW_pct_fraudulent_TX_hour_gt_day** and queried this view to return the number of occurrences per hour. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/5.%20occurrences_fraud_hour_gt_day.png).

**Result:** I discovered that 12am, 1am, 2am and 10pm are the hours with the most number of occurrences where their proportion of fraud is greater than the proportion of fraud for the entire day.

#### 4. High value transaction test
- I calculated the proportion of fraud for transactions above 900 (High) and below 900 (Low). [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/3.%20high%20value%20TX%20test.png).

**Result:** I discovered that low-value transactions had a higher proportion of fraud (4.7%) compared to high-value transactions (4.5%). 

### Data visualization
<img width="589" alt="visualization" src="https://github.com/user-attachments/assets/b7aa3dd2-af01-4322-8c17-4805f677b938">

### Recommendations

#### 1. Enhanced Monitoring During High-Risk Hours
Since the highest proportion of fraud occurs between 12am and 2am and at 10pm:
- Increase Surveillance: Implement more rigorous transaction monitoring and fraud detection rules during these high-risk hours.
- Real-Time Alerts: Set up real-time alerts for any suspicious activities during these times.
- Staffing Adjustments: Consider scheduling more fraud prevention staff or increasing automated monitoring during these peak fraud hours.

#### 2. Targeted Fraud Detection for Specific Days
Since Tuesday has the highest proportion of fraud (5.8%):
- Daily Analysis: Perform detailed fraud pattern analysis specific to Tuesdays to understand if there are recurring patterns or specific triggers.
- Preventive Measures: Apply stricter fraud prevention measures or enhanced verification steps for transactions processed on Tuesdays.

#### 3. Focused Attention on Low-Value Transactions
Since low-value transactions have a higher proportion of fraud (4.7%) compared to high-value transactions (4.5%):
- Risk-Based Authentication: Implement additional authentication or verification steps for low-value transactions.
- Fraud Detection Algorithms: Refine fraud detection algorithms to give more weight to low-value transactions.
