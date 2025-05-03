# Credit-Card-Financial-dashboard.
To develop a comprehensive credit card weekly dashboard using Power Bi that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

Project Insights-

• Overall revenue is 55M
• Total interest is 7.8M
• Total transaction amount is 45M
• Male customers are contributing more in revenue 30M, female 25M
• Blue & Silver credit card are contributing to 93% of overall transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%

DAX queries used-

1-  AgeGroup = SWITCH(
    TRUE(),
    customer[Customer_Age] < 30, "20-30",
    customer[Customer_Age] >= 30 && customer[Customer_Age] < 40, "30-40",
    customer[Customer_Age] >= 40 && customer[Customer_Age] < 50, "40-50",
    customer[Customer_Age] >= 50 && customer[Customer_Age] < 60, "50-60",
    customer[Customer_Age]>=60, "60+",
    "unknown"
    )

2-  IncomeGroup = SWITCH(
    TRUE(),
    customer[Income] < 35000, "Low",
    customer[Income] >= 35000 && customer[Income] < 70000, "Med",
    customer[Income] >=70000, "High",
    "Unknown"
    ) 

3-  Week_num2 = WEEKNUM(credit_card[Week_Start_Date])

4-  Revenue = credit_card[Annual_Fees] + credit_card[Total_Trans_Amt] + credit_card[Interest_Earned]

5-  Current_Week_Revenue = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_num2] = MAX(credit_card[Week_num2]))
    )

6-  Current_Week_Revenue = CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_num2] = MAX(credit_card[Week_num2]))
    )

