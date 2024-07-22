# audit-analytics

#### Test for outliers in transaction amount
I tested for outliers using the inter-quartile range approach and discovered no outliers.
I tested with a different approach by outputting amounts that were more than 3 standard deviations from the mean, and still discovered no outliers.

#### High value transaction test
I calculated the proportion of fraud for transactions above 900 (High) and below 900 (Low).
I discovered that low-value transactions had a higher proportion of fraud (4.7%) compared to high-value transactions (4.5%).
