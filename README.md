# Zomato Delivery Analysis
# 1. Introduction
With the rising demand for online food delivery services, companies like Zomato face increasing pressure to optimize logistics while maintaining high service standards. This project analyzes Zomato's delivery dataset, which contains detailed operational data including delivery timings, road and weather conditions, and performance metrics. The goal is to uncover operational inefficiencies, enhance route planning, and improve overall delivery performance through data analysis and machine learning.
<img src=Image/zomato.png>
# 2. Purpose
The purpose of this project is to evaluate key factors affecting delivery time and customer experience in Zomato’s delivery operations. By applying data analytics and predictive modeling, the project seeks to understand how internal and external variables (e.g., traffic, vehicle condition, delivery personnel rating) influence delivery outcomes. The insights will help inform operational decisions and improve efficiency.
# 3. Outcome
This project will provide a comprehensive, data-driven assessment of Zomato's delivery system. Expected outcomes include:

1. Identify key factors affecting delivery time and customer experience.
1. Analyze internal & external variables (traffic, vehicle, ratings) influencing outcomes.
1. Inform operational decisions and improve efficiency.

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

# 5. Tools - Technologies
- Python (Pandas, Matplotlib, Seaborn)
- Jupyter Notebook for analysis scripting
- Power BI for interactive visualizations and dashboards

# 6. Analysis Plan
## 6.1 Data Preparation and Cleaning
#### - Types fixing
- **'Delivery_person_ID','Weather_conditions','Vehicle_condition','Road_traffic_density','Type_of_vehicle','Type_of_order','Festival','City':** convert to string
- **'Time_Orderd', 'Time_Order_picked':** convert to Datetime

#### - Handle missing values through imputation or removal.
- **'Delivery_person_Ratings','Delivery_person_Age','multiple_deliveries':** replace with median value
- **'Weather_conditions','Road_traffic_density','City','Festival':** replace with Mode value
  
#### - Fixing Inconsistencies in Strings
- **'Weather_conditions','Vehicle_condition','Road_traffic_density','Type_of_vehicle','Type_of_order','Festival','City':** set to lower and then convert to Category

#### - Handling outliers (IQR)
- No data is outlier

## 6.2 Exploratory Data Analysis (EDA)

### 6.2.1 Delivery staff

**Delivery_person_Age:**

|level\_0|index|all|20\.0|21\.0|22\.0|23\.0|24\.0|25\.0|26\.0|27\.0|28\.0|29\.0|30\.0|31\.0|32\.0|33\.0|34\.0|35\.0|36\.0|37\.0|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|Time\_taken\_min|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|
|1|Time\_taken\_max|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|53\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|54\.0|
|2|Time\_taken\_mean|26\.344451662100713|23\.031884057971016|22\.898078043098426|23\.00670016750419|23\.049939831528278|23\.061651583710407|22\.798723897911835|22\.828701077708452|23\.06812933025404|23\.198403648802735|23\.028264556246466|29\.057956278596848|30\.0|29\.945930563460443|29\.397831050228312|29\.648085585585587|29\.743956043956043|29\.44068706387547|29\.297312122874384|
|3|Time\_taken\_median|26\.0|22\.0|22\.0|22\.0|22\.0|22\.0|22\.0|22\.0|22\.0|22\.0|22\.0|28\.0|29\.0|29\.0|28\.0|29\.0|29\.0|29\.0|28\.0|
|4|Time\_taken\_mode|26\.0|16\.0|19\.0|15\.0|15\.0|15\.0|16\.0|18\.0|18\.0|15\.0|17\.0|25\.0|25\.0|28\.0|25\.0|25\.0|26\.0|25\.0|27\.0|

<img src=Image/Delivery_Person_Age.png>

**>>>> Insight:** Employees aged 28 and under have a faster delivery time rate.

**Density Plot of Delivery_person_Ratings**

<img src=Image/Delivery_person_Ratings.png>

**>>>> Insight:** Faster delivery times tend to receive higher ratings.

### 6.2.2 Vehicles

**Time Taken Distribution by Vehicle_condition**

<img src=Image/Time_Taken_Distribution_by_Vehicle_condition.png>

**>>>> Insight:** The condition of the vehicle affects the delivery time. A good vehicle condition ensures faster delivery.

**Multiple_deliveries:**
|level\_0|index|all|0\.0|1\.0|2\.0|3\.0|
|---|---|---|---|---|---|---|
|0|Time\_taken\_min|10\.0|10\.0|10\.0|31\.0|42\.0|
|1|Time\_taken\_max|54\.0|54\.0|54\.0|54\.0|54\.0|
|2|Time\_taken\_mean|26\.344451662100713|22\.907996717425004|26\.770861923945283|40\.36664544875875|47\.86785714285714|
|3|Time\_taken\_median|26\.0|22\.0|26\.0|40\.0|48\.0|
|4|Time\_taken\_mode|26\.0|15\.0|26\.0|39\.0|49\.0|

**Time Taken Distribution by Multiple_deliveries**

<img src=Image/Time_Taken_Distribution_by_Multiple_deliveries.png>

**>>>> Insight:** Multiple deliveries affect the delivery time.

### 6.2.3 Order and Timing

**Time_Orderd**
|level\_0|index|all|08:00 - 08:59|09:00 - 09:59|10:00 - 10:59|11:00 - 11:59|12:00 - 12:59|13:00 - 13:59|14:00 - 14:59|15:00 - 15:59|16:00 - 16:59|17:00 - 17:59|18:00 - 18:59|19:00 - 19:59|20:00 - 20:59|21:00 - 21:59|22:00 - 22:59|23:00 - 23:59|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|Time\_taken\_min|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|10\.0|
|1|Time\_taken\_max|54\.0|34\.0|34\.0|34\.0|53\.0|53\.0|54\.0|54\.0|39\.0|39\.0|49\.0|49\.0|54\.0|54\.0|54\.0|44\.0|44\.0|
|2|Time\_taken\_mean|26\.293962793962795|19\.58062740781508|19\.521468926553673|19\.480898876404495|27\.165158371040725|26\.77524893314367|27\.451704545454547|27\.543933054393307|22\.880559085133417|23\.01219512195122|27\.477558774637853|27\.28991905813098|31\.17630127128808|31\.178527757397898|31\.126286248830684|22\.416826462128476|22\.435314257764734|
|3|Time\_taken\_median|26\.0|19\.0|19\.0|19\.0|27\.0|27\.0|27\.0|27\.0|23\.0|24\.0|27\.0|27\.0|31\.0|31\.0|31\.0|22\.0|22\.0|
|4|Time\_taken\_mode|26\.0|15\.0|15\.0|19\.0|28\.0|28\.0|26\.0|27\.0|26\.0|26\.0|26\.0|25\.0|27\.0|29\.0|26\.0|19\.0|24\.0|

<img src=Image/Time_Orderd.png>

**>>>> Insight:** The time frame from 5 PM to 10 PM has a longer delivery rate than average.

**Delivery Time by Festival and Type_of_order**

<img src=Image/Delivery_Time_by_Festival_and_Type_of_order.png>

**>>>> Insight:** Delivery times during the Festival are always higher.

### 6.2.4 Weather and traffic conditions

**Time Taken Distribution by Weather conditions**

<img src=Image/Time_Taken_Distribution_by_Weather_conditions.png>

**>>>> Insight:** Weather conditions affect delivery time, sunny is the best.

**Time Taken Distribution by Road traffic**

<img src=Image/Time_Taken_Distribution_by_Road_traffic.png>

**>>>> Insight:** Road Traffic affect delivery time.

### 6.2.5 Area
**Time Taken Distribution by City**

<img src=Image/Time_Taken_Distribution_by_City.png>

**>>>> Insight:** Semi-Urban have Time - Taken is so high.

### - Regression Analysist
*   R² Score = 0.57 → The model explains 57% of the variance in the delivery time (Time_taken (min)) based on the input variables. This is a relatively acceptable level given the noisy nature of real-world delivery data.

*   MSE = 88.44 → The Mean Squared Error (MSE) represents the average squared difference between the predicted and actual values, indicating the prediction error of the model.

**COEF**

<img src=Image/COEF.png>

**>>>> Insight:** ### **👉 Top factors that increase delivery time (based on regression coefficients):**
| Variable                          | Influence coefficient | Explain                                                                       |
| ----------------------------- | --------------- | -------------------------------------------------------------------------------- |
| `Delivery_location_longitude` | **48.46**       | A greater geographical distance (larger longitude coordinates) → increases delivery time. |
| `City_Semi-Urban`             | **11.31**       | Delivery in suburban areas results in significantly higher delivery times.         |
| `Festival_Yes`                | **10.60**       | Delivery during the holidays takes more time due to congestion and a lack of manpower.          |
| `multiple_deliveries`         | **3.14**        | Each time an additional order is added during the same trip, it increases the time.              |
| `Delivery_person_Age`         | **0.38**        | Older age is associated with slightly slower delivery speeds.                  |
| `Road_traffic_density_Jam`    | **0.26**        | When delivering in 'Jam' conditions (traffic jam), the time increases significantly.       |

## 6.3 Visualization and Reporting
<img src=Image/visualize.png>

# 7. Conclusions

### Delivery staff
1.   **Delivery_person_Age:** Employees aged 28 and under have a faster delivery time rate.
2.   **Delivery_person_Ratings:** Faster delivery times tend to receive higher ratings.

### Vehicles
1.   **Vehicle_condition:** The condition of the vehicle affects the delivery time. A good vehicle condition ensures faster delivery. 
2.   **multiple_deliveries:** Multiple deliveries affect the delivery time. 

### Order and Timing
1.   **Time_Orderd:** The time frame from 5 PM to 10 PM has a longer delivery rate than average. 
2.   **Festival:** Delivery times during the Festival are always higher. 

### Weather and traffic conditions
1.   **Weather_conditions:** Weather conditions affect delivery time, sunny is the best.
2.   **Road_traffic_density:** Road Traffic affect delivery time. 

### Area
1.   **City:** Semi-Urban have Time - Taken is so high. 


### **👉 Top factors that increase delivery time (based on regression coefficients):**
| Variable                          | Influence coefficient | Explain                                                                       |
| ----------------------------- | --------------- | -------------------------------------------------------------------------------- |
| `Delivery_location_longitude` | **48.46**       | A greater geographical distance (larger longitude coordinates) → increases delivery time. |
| `City_Semi-Urban`             | **11.31**       | Delivery in suburban areas results in significantly higher delivery times.         |
| `Festival_Yes`                | **10.60**       | Delivery during the holidays takes more time due to congestion and a lack of manpower.          |
| `multiple_deliveries`         | **3.14**        | Each time an additional order is added during the same trip, it increases the time.              |
| `Delivery_person_Age`         | **0.38**        | Older age is associated with slightly slower delivery speeds.                  |
| `Road_traffic_density_Jam`    | **0.26**        | When delivering in 'Jam' conditions (traffic jam), the time increases significantly.       |

# 8. Recommendations (Detailed and Actionable)
Based on the data analysis and insights obtained, the following are specific recommendations to improve Zomato’s delivery performance:

### Delivery staff
1.   **Delivery_person_Age:**
      Prioritize recruiting younger delivery personnel (under 28 years old) or conduct training programs focused on improving delivery speed for older staff.
2.   **Delivery_person_Ratings:** 
      Introduce performance-based incentives tied to high customer ratings.

### Vehicles
1.   **Vehicle_condition:**
      Implement mandatory regular maintenance for all delivery vehicles, particularly those with poor condition scores (0 or 1).
      Introduce incentive policies for drivers to use newer or better-maintained vehicles, boosting overall delivery performance.
2.   **multiple_deliveries:**
      Limit the number of orders per trip when route optimization is not feasible.
      Use smart order allocation algorithms to minimize average delivery time for multiple orders.

### Order and Timing
1.   **Time_Orderd:**
      Peak Hours (5 PM – 10 PM): Increase delivery personnel by at least 20–30% to mitigate delays during this time frame.
      Prioritize delivery of snacks or beverages during morning and midday slots, when delivery times are generally lower.
2.   **Festival:**
      There is a need to plan for staffing for the Festival.

### Weather and traffic conditions
1.   **Weather_conditions:**
      Monitor weather conditions to adjust staffing and routing strategies, especially during festival days.
2.   **Road_traffic_density:**
      Deploy real-time routing systems, integrating traffic and weather data to avoid congested or adverse areas (e.g., high traffic density or bad weather).
      Train delivery personnel on identified fast routes based on data analysis.

### Area
1.   **City:**
      Semi-Urban have Time - Taken is so high. Deploy more resources to Semi-Urban areas to improve delivery speed, as these regions show longer delivery times.

### Continuous Monitoring and Evaluation
      Implement Power BI dashboards to track delivery times by hour, region, and order type.

      Establish clear KPIs (e.g., reduce average delivery time by 15% during peak hours).

