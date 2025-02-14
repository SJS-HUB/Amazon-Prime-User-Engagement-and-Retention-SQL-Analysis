
# Amazon Prime User Engagement and Retention Analysis

## Objective
The primary goal of this project is to analyze Amazon Prime user engagement and retention data using SQL. This analysis aims to uncover key trends and insights that can inform business decisions, enhance user experience, and improve marketing strategies.

## Introduction
In this project, I explored various aspects of Amazon Prime user behavior, including device usage, subscription renewals, customer support satisfaction, user engagement, and feedback distribution. By examining these areas, we aim to understand customer behavior and preferences better.

## Device Usage Analysis

### Query
```sql
SELECT `Devices Used`, COUNT(*) AS `Number of Users`
FROM `updated_amazon_prime_users`
GROUP BY `Devices Used`
ORDER BY `Number of Users` DESC;
```

### Insights
- Smartphones are the most commonly used devices, followed by tablets and smart TVs.
- It is essential to optimize the mobile UI/UX to enhance user satisfaction.
- Investigating low laptop usage could uncover opportunities for improvement.

## Subscription Plan Renewal Analysis

### Query
```sql
SELECT `Subscription Plan`, `Renewal Status`, COUNT(*) AS `Number of Renewals`
FROM `updated_amazon_prime_users`
GROUP BY `Subscription Plan`, `Renewal Status`
ORDER BY `Number of Renewals` DESC;
```

### Insights
- Annual plans with manual renewals have the highest renewal rates, indicating a preference for long-term commitments.
- Offering incentives for manual renewals could boost retention.
- Auto-renewal is convenient for monthly users, slightly surpassing manual renewals.

## Customer Support Satisfaction Analysis

### Query
```sql
SELECT `User ID`, `Feedback/Ratings`, COUNT(`Customer Support Interactions`) AS `Support Interactions`
FROM `updated_amazon_prime_users`
WHERE `Feedback/Ratings` < 3
GROUP BY `User ID`, `Feedback/Ratings`;
```

### Insights
- Users with lower feedback ratings tend to have more support interactions.
- Improving support quality could enhance overall user satisfaction.
- Segmenting users based on feedback ratings and support interactions can help identify specific user groups requiring more attention.

## User Engagement and Churn Risk Analysis

### Query
```sql
SELECT `User ID`, `Username`, `Usage Frequency`, `Engagement Metrics`
FROM `updated_amazon_prime_users`
WHERE `Usage Frequency` < 2 AND `Engagement Metrics` < 3;
```

### Insights
- Users with low usage frequency and engagement metrics are at higher risk of churn.
- Targeted engagement strategies could help retain these users.

## Popular Subscription Plan Analysis

### Query
```sql
SELECT `Subscription Plan`, COUNT(*) AS `Total Users`
FROM `updated_amazon_prime_users`
GROUP BY `Subscription Plan`
ORDER BY `Total Users` DESC;
```

### Insights
- Both annual and monthly subscription plans have an equal number of users (1275 each), indicating a balanced preference among users for flexibility and long-term commitment.

## Feedback Ratings Distribution

### Query
```sql
SELECT `Feedback/Ratings`, COUNT(*) AS `Number of Users`
FROM `updated_amazon_prime_users`
GROUP BY `Feedback/Ratings`
ORDER BY `Number of Users` DESC;
```

### Insights
- Most users provide positive feedback, but there is a notable segment with lower ratings that requires attention.

## Location-Based Feedback Analysis

### Query
```sql
SELECT `Location`, `Feedback/Ratings`, COUNT(*) AS `Number of Users`
FROM `updated_amazon_prime_users`
GROUP BY `Location`, `Feedback/Ratings`
ORDER BY `Number of Users` DESC;
```

### Insights
- Regional differences in feedback can point to localized service issues or satisfaction levels.
- Amazon could use this data to launch targeted improvements or marketing campaigns in specific regions.

## Payment Method Preferences

### Query
```sql
SELECT `Payment Information`, COUNT(`User ID`) AS `Users`
FROM `updated_amazon_prime_users`
GROUP BY `Payment Information`
ORDER BY `Users` DESC;
```

### Insights
- Mastercard is the preferred payment method among most users.
- Offering discounts for Visa or Amex users can encourage more users to choose these options.
- Partnering with Mastercard to offer exclusive benefits could be beneficial.

## Correlation Between Engagement and Feedback

### Query
```sql
SELECT `Engagement Metrics`, AVG(`Feedback/Ratings`) AS `Average Rating`
FROM `updated_amazon_prime_users`
GROUP BY `Engagement Metrics`
ORDER BY `Engagement Metrics` DESC;
```

### Insights
- Insights from the correlation can inform content strategies tailored to different user segments based on their engagement and feedback.
- These insights can help Amazon Prime continuously refine its engagement strategies and enhance overall user satisfaction.

## Finding Users with Expired Memberships

### Query
```sql
SELECT `User ID`, `Username`, `Membership End Date`
FROM `updated_amazon_prime_users`
WHERE `Membership End Date` < CURDATE() AND `Renewal Status` != `Renewed`;
```

### Insights
- This query helps identify users whose membership has ended but have not renewed it yet.
- Amazon can target these users with renewal reminders or special offers.

## Key Insights
1. Most users access Prime via smartphones. Enhancing mobile UI/UX is critical.
2. Users prefer annual plans, indicating a trend toward long-term commitment.
3. Low satisfaction correlates with frequent support interactions. Improve support quality.
4. Low engagement signals higher churn risk. Focus on targeted engagement strategies.
5. Equal preference for annual and monthly plans suggests offering both remains important.
6. Majority of feedback is positive, but negative feedback needs attention.
7. Regional feedback differences highlight the need for localized improvements.
8. Mastercard is preferred. Incentives for Visa/Amex could diversify payment methods.
9. Tailor content strategies based on engagement and feedback correlation.

---
