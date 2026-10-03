FedEx Delivery Operations EDA 
Project 

Is solving following tasks
Project Understanding 
1. What is the objective of this EDA project? 
→ To analyze FedEx delivery data, understand operational patterns, identify causes of 
delays or high costs, and propose efficiency improvements. 
2. What file do we use for this project? 
→ A simulated dataset: fedex_deliveries.csv, with details like shipment IDs, cities, 
dates, weight, cost, status, and delays. 
3. What should the final submission include? 
Jupyter Notebook with visualizations 
Markdown cells explaining insights 
Cleaned dataset (optional) 
Code must be well-commented

 Data Cleaning & Preparation 
How do I handle missing values? 
→ First use: 
python 
CopyEdit 
df.isnull().sum() 

5. Then decide: 
○ Drop rows (df.dropna()) 
○ Fill with median/mean (e.g., for Cost_USD, Weight_KG) 
○ Fill with 'Unknown' or mode for categorical columns 
How do I convert pickup and delivery dates? 
python 
CopyEdit 
df['Pickup_Date'] = pd.to_datetime(df['Pickup_Date']) 
df['Delivery_Date'] = pd.to_datetime(df['Delivery_Date']) 

6.  How do I calculate delivery time in days? 
python 
CopyEdit 
df['Delivery_Time_Days'] = (df['Delivery_Date'] - 
df['Pickup_Date']).dt.days

7.  How do I detect outliers in cost or weight? 
→ Use boxplots: 
python 
CopyEdit 
sns.boxplot(df['Cost_USD']) 

8.   Exploratory Data Analysis (EDA) 
How do I check the average delivery time? 
python 
CopyEdit 
df['Delivery_Time_Days'].mean() 

9.  How do I visualize shipment volume by mode? 
python 
CopyEdit 
df['Shipment_Mode'].value_counts().plot(kind='bar') 
 
10. How do I compare shipping costs by customer segment? 
python 
CopyEdit 
df.groupby('Customer_Segment')['Cost_USD'].mean().plot(kind='bar')

11. How do I analyze delays by mode of shipment? 
→ Use: 
python 
CopyEdit 
pd.crosstab(df['Shipment_Mode'], 
df['Delivery_Status']).plot(kind='bar', stacked=True)

12. How do I find the most common origin-destination city pairs? 
python 
CopyEdit 
df.groupby(['Origin', 
'Destination']).size().sort_values(ascending=False).head(5) 
 Geographic & Operational Insights 

13. How do I find the most common delay reasons? 
python 
CopyEdit 
df['Delay_Reason'].value_counts() 

14. How do I compare delivery time across shipment modes? 
python 
CopyEdit 
df.groupby('Shipment_Mode')['Delivery_Time_Days'].mean().plot(kind='ba
r') 

15. How do I create a correlation heatmap? 
python 
CopyEdit 
sns.heatmap(df.corr(), annot=True) 

16. What kind of insights should I look for? 
● Which mode is most efficient? 
● Which cities face delays? 
● Which reasons lead to longest delivery time? 
● What segments cost the most? 

 Business Recommendation Section 
17. What is an example of an operational inefficiency? 
“Freight shipments are frequently delayed due to operational issues in urban 
areas.” 

18. How do I recommend a mode change? 
“Consider switching short-distance freight to ground mode to cut cost by 15%.”

20. How do I support my insight with data? 
→ Always include a plot or metric with explanation: 
● “As seen in the bar chart, air shipments have the highest delay frequency.”

22. What’s a good customer satisfaction recommendation? 
“Send proactive alerts to customers if expected delay reason is weather or 
customs, to improve trust.”

How do I recommend a mode change? “Consider switching short-distance freight to ground mode to cut cost by 15%.”

How do I support my insight with data? → Always include a plot or metric with explanation: ● “As seen in the bar chart, air shipments have the highest delay frequency.”

What’s a good customer satisfaction recommendation? “Send proactive alerts to customers if expected delay reason is weather or customs, to improve trust.”
