### Executive summary
I carried out this project to assess the integrity of financial transactions processed through a fictional company's platform.

### Data visualization
<img width="589" alt="visualization" src="https://github.com/user-attachments/assets/b7aa3dd2-af01-4322-8c17-4805f677b938">

### Tests
#### 1. Test for outliers in transaction amount
- I tested for outliers using the inter-quartile range approach. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/1.%20outlier%20detection%20using%20IQR.png).
- I tested with a different approach by outputting amounts that were more than 3 standard deviations from the mean. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/2.%20outlier%20detection%20using%20mean_std.png).

**Result:** No outliers.

#### 2. Test for transaction timing
- I wrote queries to compare total vs fraudulent transactions by
  - hour [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/6.%20fraud_by_hour.png).
  - day of week [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/7.%20fraud_by_day.png).

**Result:** The hour with the highest proportion of fraud (6.6%) was 2am. The day with the highest proportion of fraud was Tuesday (5.8%).

#### 3. Test for fraudulent hours 
- I queried the database to return the hours where the proportion of fraud per hour is greater than the proportion of fraud per day. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/4.%20fraud_hour_gt_day.png).
- Then I wrapped the result in a view called **VIEW_pct_fraudulent_TX_hour_gt_day** and queried this view to return the number of occurrences per hour. [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/5.%20occurrences_fraud_hour_gt_day.png).

**Result:** I discovered that 12am, 1am, 2am and 10pm are the hours with the most number of occurrences where their proportion of fraud is greater than the proportion of fraud for the entire day.

#### 4. High value transaction test
- I calculated the proportion of fraud for transactions above 900 (High) and below 900 (Low). [Link here](https://github.com/johnuzoma/audit-analytics/blob/main/sql/3.%20high%20value%20TX%20test.png).

**Result:** I discovered that low-value transactions had a higher proportion of fraud (4.7%) compared to high-value transactions (4.5%). 
