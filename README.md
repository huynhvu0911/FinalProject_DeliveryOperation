# 1. Introduction
With the rising demand for online food delivery services, companies like Zomato face increasing pressure to optimize logistics while maintaining high service standards. This project analyzes Zomato's delivery dataset, which contains detailed operational data including delivery timings, road and weather conditions, and performance metrics. The goal is to uncover operational inefficiencies, enhance route planning, and improve overall delivery performance through data analysis and machine learning.
<img src=zomato.png>
# 2. Purpose
The purpose of this project is to evaluate key factors affecting delivery time and customer experience in Zomato’s delivery operations. By applying data analytics and predictive modeling, the project seeks to understand how internal and external variables (e.g., traffic, vehicle condition, delivery personnel rating) influence delivery outcomes. The insights will help inform operational decisions and improve efficiency.
# 3 . Outcome
This project will provide a comprehensive, data-driven assessment of Zomato's delivery system. Expected outcomes include:

1. Identifying the variables most strongly correlated with delivery delays.
1. Planning and strategies for peak times, festivals, multiple deliveries, and delivery staff performance.
1. Recommendations to improve delivery quality, customer experience, and logistics management.
# 4. Dataset Information
### Source: Zomato Delivery Dataset
https://www.kaggle.com/datasets/saurabhbadole/zomato-delivery-operations-analytics-dataset
### Data Overview
|index|Delivery\_person\_ID|Delivery\_person\_Age|Delivery\_person\_Ratings|Restaurant\_latitude|Restaurant\_longitude|Delivery\_location\_latitude|Delivery\_location\_longitude|Order\_Date|Time\_Orderd|Time\_Order\_picked|Weather\_conditions|Road\_traffic\_density|Vehicle\_condition|Type\_of\_order|Type\_of\_vehicle|multiple\_deliveries|Festival|City|Time\_taken \(min\)|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|DEHRES17DEL01|36\.0|4\.2|30\.327968|78\.046106|30\.397968|78\.116106|2022-02-12 00:00:00|1900-01-01 21:55:00|1900-01-01 22:10:00|Fog|Jam|2|Snack|motorcycle|3\.0|No|Metropolitian|46|
|1|KOCRES16DEL01|21\.0|4\.7|10\.003064|76\.307589|10\.043064|76\.347589|2022-02-13 00:00:00|1900-01-01 14:55:00|1900-01-01 15:05:00|Stormy|High|1|Meal|motorcycle|1\.0|No|Metropolitian|23|
|2|PUNERES13DEL03|23\.0|4\.7|18\.56245|73\.916619|18\.65245|74\.006619|2022-03-04 00:00:00|1900-01-01 17:30:00|1900-01-01 17:40:00|Sandstorms|Medium|1|Drinks|scooter|1\.0|No|Metropolitian|21|
|3|LUDHRES15DEL02|34\.0|4\.3|30\.899584|75\.809346|30\.919584|75\.829346|2022-02-13 00:00:00|1900-01-01 09:20:00|1900-01-01 09:30:00|Sandstorms|Low|0|Buffet|motorcycle|0\.0|No|Metropolitian|20|
|4|KNPRES14DEL02|24\.0|4\.7|26\.463504|80\.372929|26\.593504|80\.502929|2022-02-14 00:00:00|1900-01-01 19:50:00|1900-01-01 20:05:00|Fog|Jam|1|Snack|scooter|1\.0|No|Metropolitian|41|

The dataset contains information about order placement time, pickup time, delivery time, weather information, traffic conditions, order type, vehicle status, providing insights into consumer behavior and delivery patterns. The attributes are categorized into five main parts: Delivery staff, vehicles, Order and delivery timing, Weather and traffic conditions, and finally, Area.
##### 4.1 Delivery staff
- Delivery_person_ID: Unique identifier of delivery personnel
- Delivery_person_Age: Age of delivery person
- Delivery_person_Ratings: Rating of the delivery person

##### 4.2 Vehicles
- Vehicle_condition: Condition of the delivery vehicle
- Type_of_vehicle: Vehicle used by delivery person
- Multiple_deliveries: Whether the trip includes multiple deliveries

##### 4.3 Order and Timing
- Order_Date: Date the order was placed
- Time_Ordered: Time order was created
- Time_Order_picked: Time when delivery person picked up the order
- Type_of_order: Type of service (e.g., delivery, takeaway)
- Festival: Whether the delivery occurred during a festival

##### 4.4 Weather and traffic conditions
- Weather_conditions: Weather at the time of delivery
- Road_traffic_density: Traffic conditions during delivery

##### 4.5 Area
- Restaurant_latitude/longitude: GPS coordinates of the restaurant
- Delivery_location_latitude/longitude: GPS coordinates of the customer
- City: Delivery city

# 5 . Tools & Technologies
- Python (Pandas, Matplotlib, Seaborn)
- Jupyter Notebook for analysis scripting
- Power BI for interactive visualizations and dashboards

# 6 . Analysis Plan
## 6.1 Data Preparation and Cleaning
### - Types fixing
<img src=info.png>
<img src=code_TypesFixing.png>

### - Handle missing values through imputation or removal.
<img src=info_After_TypesFixing.png>
<img src=code_HandleMissing.png>

### - Fixing Inconsistencies in Strings
<img src=info_After_HandleMissing.png>
<img src=code_FixingInconsistenciesInString.png>


