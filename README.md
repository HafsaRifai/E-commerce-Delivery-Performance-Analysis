## Project README: E-commerce Delivery Performance Analysis

### Business Problem
A global e-commerce company faces inconsistent delivery performance, leading to late deliveries and unpredictable order profitability. Actual shipping times often deviate significantly from scheduled timelines.

### Desired Outcome
The goal of this project is to analyze delivery operations, identify bottlenecks, and build a predictive system to reduce delays, optimize shipping performance, and improve overall efficiency and profitability.

### Exploratory Data Analysis (EDA) Key Findings
*   **Data Overview**: The dataset contains 180,519 orders with 53 initial columns, which were later reduced to 21 relevant features after cleaning. There are no duplicate entries. Missing values were handled by dropping columns with excessive missing data or those deemed irrelevant.
*   **Delay Analysis**:
    *   Approximately 54.7% of orders experience late delivery.
    *   A significant portion of orders (31%) are delayed by 1 day.
    *   Orders with negative delays (arriving earlier than scheduled) also exist, constituting around 24% of orders.
*   **Profitability Analysis**:
    *   80.6% of orders are profitable, while 18.7% result in a loss.
    *   The total profit generated is approximately $7.9 million, but around $2.1 million in profit is lost due to delays.
    *   Mean profit per order shows some fluctuation with delay days, but total profit is highest for orders delayed by 1 day.
*   **Bottleneck Detection (Delay % by Category)**:
    *   **Shipping Mode**: 'First Class' shipping mode shows a 100% delay rate in some regions, indicating a critical bottleneck.
    *   **Order Status**: 'SUSPECTED_FRAUD', 'PAYMENT_REVIEW', 'PENDING', and 'CANCELED' order statuses frequently lead to high delay percentages, suggesting issues in order processing workflows.
    *   **Customer Segment, Department Name, Order Region, Type**: These categories also show varying delay percentages, highlighting specific segments or regions that contribute more to late deliveries.
*   **Time Series Analysis (Delay % by Time)**:
    *   **Month**: Delay percentages show minor fluctuations throughout the year, with December, August, and September having slightly higher delay rates.
    *   **Day of Week**: Mondays and Sundays tend to have slightly higher delay percentages compared to other days.
    *   **Hour of Day**: Peaks in delay percentage are observed around certain hours, particularly at 8 PM (20:00), 12 PM (12:00), and 2 PM (14:00), indicating potential operational strain during these times.

### Machine Learning Modeling
*   **Objective**: Predict `Late_delivery_risk` to proactively identify orders prone to delays.
*   **Features Used**: Categorical features like `Type`, `Category Name`, `Customer Segment`, `Department Name`, `Order Region`, `Shipping Mode`, and numerical features `Days for shipment (scheduled)`, `order_month`, `order_hour` were used.
*   **Feature Engineering**: Categorical features were transformed using frequency encoding to handle cardinality and make them suitable for the model.
*   **Data Splitting**: The dataset was split into training and testing sets (80/20 ratio) with stratification to maintain the class distribution of the target variable.
*   **Class Imbalance Handling**: SMOTE (Synthetic Minority Over-sampling Technique) was applied to the training data to balance the classes (`Late_delivery_risk`).
*   **Model**: A `RandomForestClassifier` was trained on the balanced training data.
*   **Performance**:
    *   **Accuracy**: 0.73
    *   **Precision**: 0.77
    *   **Recall**: 0.74
    *   The model demonstrates a reasonable ability to predict late deliveries, with balanced precision and recall for both classes, indicating it's not overly biased towards one class despite the initial imbalance.

### Conclusion and Recommendations
*   The analysis highlights critical areas for intervention, particularly concerning 'First Class' shipping mode and specific order statuses that are highly correlated with delays.
*   Operational improvements should focus on optimizing workflows for orders with high delay risk factors, especially during peak hours and certain days of the week.
*   The predictive model can be deployed to flag high-risk orders, enabling proactive measures to prevent late deliveries and mitigate potential profit losses.
