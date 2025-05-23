# 1. Introduction
With the rising demand for online food delivery services, companies like Zomato face increasing pressure to optimize logistics while maintaining high service standards. This project analyzes Zomato's delivery dataset, which contains detailed operational data including delivery timings, road and weather conditions, and performance metrics. The goal is to uncover operational inefficiencies, enhance route planning, and improve overall delivery performance through data analysis and machine learning.
<img src=Image/zomato.png>
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
#### - Types fixing
<img src=Image/info.png>
<img src=Image/code_TypesFixing.png>

#### - Handle missing values through imputation or removal.
<img src=Image/info_After_TypesFixing.png>
<img src=Image/code_HandleMissing.png>

#### - Fixing Inconsistencies in Strings
<img src=Image/info_After_HandleMissing.png>
<img src=Image/code_FixingInconsistenciesInString.png>

## 6.2 Exploratory Data Analysis (EDA)
#### - Measures of central tendency
**Some code to Define a function:**
def compare_tip_dynamic_dimension(input_dimension):  
  df_agg_detail = df.groupby(input_dimension).agg(Time_taken_min = ('Time_taken (min)','min'),
                                    Time_taken_max= ('Time_taken (min)','max'),
                                    Time_taken_mean = ('Time_taken (min)','mean'),
                                    Time_taken_median = ('Time_taken (min)','median'),
                                    Time_taken_mode=('Time_taken (min)', lambda x: x.mode().iloc[0] if not x.mode().empty else None)
                                    )
  df_agg_detail = df_agg_detail.T
  df_agg_detail = df_agg_detail.reset_index()

  df_agg = df.agg(Time_taken_min = ('Time_taken (min)','min'),
                                    Time_taken_max= ('Time_taken (min)','max'),
                                    Time_taken_mean = ('Time_taken (min)','mean'),
                                    Time_taken_median = ('Time_taken (min)','median'),
                                    Time_taken_mode=('Time_taken (min)', lambda x: x.mode().iloc[0] if not x.mode().empty else None)
                                    )
  df_agg.columns = ["all"]
  df_agg = df_agg.reset_index()

  df_compare = df_agg.merge(df_agg_detail,"inner", on = "index")
  return df_compare

... and one of results

|level\_0|index|all|0\.0|1\.0|2\.0|3\.0|
|---|---|---|---|---|---|---|
|0|Time\_taken\_min|10\.0|10\.0|10\.0|31\.0|42\.0|
|1|Time\_taken\_max|54\.0|54\.0|54\.0|54\.0|54\.0|
|2|Time\_taken\_mean|26\.344451662100713|22\.907996717425004|26\.770861923945283|40\.36664544875875|47\.86785714285714|
|3|Time\_taken\_median|26\.0|22\.0|26\.0|40\.0|48\.0|
|4|Time\_taken\_mode|26\.0|15\.0|26\.0|39\.0|49\.0|

#### - Histogram
**Some code to build a Histogram:**

plt.figure(figsize=(20, 7))
sns.histplot(data=df, x='Time_taken (min)', hue='multiple_deliveries', bins=30, kde=True)
plt.title('Time Taken Distribution by Multiple_deliveries')
plt.show()


... and one of results
<img src=Image/Result_Histogram.png>

#### - Density Plot
**Some code to build a Density Plot:**


list_col_Density = ['Delivery_person_Age','Delivery_person_Ratings','Time_Orderd']

k = 0
plt.figure(figsize=(10, 6))
sns.kdeplot(data=df, x=list_col_Density[k], fill=True, color='skyblue')
sns.kdeplot(data=df_median_time_taken, x=list_col_Density[k], fill=True, color='red')
plt.title('Density Plot of ' + list_col_Density[k])
plt.xlabel(list_col_Density[k])
plt.grid(True)
plt.show()

... and one of results
<img src=Image/Result_DensityPlot.png>

#### - Box Plot
**Some code to build a Box Plot:**

plt.figure(figsize=(20, 6))
sns.boxplot(data=df, x='Festival', y='Time_taken (min)', hue='Type_of_order', palette='pastel')
plt.title('Delivery Time by Festival and Type_of_order')
plt.xlabel('Festival')
plt.ylabel('Time Taken (min)')
plt.legend(title='Type_of_order')
plt.grid(True)
plt.show()

... and one of results
<img src=Image/Result_BoxPlot.png>

#### - Regression Analysist
**Some code to build a Regression Analysist:**

df_encoded = pd.get_dummies(df, columns=['Weather_conditions', 'Road_traffic_density', 'Festival', 'Type_of_order', 'City'], drop_first=True)

from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_squared_error

X = df_encoded.drop(columns=['Time_taken (min)', 'Delivery_person_ID', 'Order_Date', 'Time_Orderd', 'Time_Order_picked','Vehicle_condition','Type_of_vehicle'])
y = df_encoded['Time_taken (min)']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = LinearRegression()
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
print(f"R2 Score: {r2_score(y_test, y_pred):.2f}")
print(f"MSE: {mean_squared_error(y_test, y_pred):.2f}")

coef = pd.Series(model.coef_, index=X.columns)
print(coef.sort_values(ascending=False).head(10))

... and one of results

<img src=Image/Result_Regression.png>

## 6.3 Visualization and Reporting
<img src=Image/visualize.png>

# 7. Conclusions

##### Delivery staff
1.   **Delivery_person_Age:** Employees aged 28 and under have a faster delivery time rate.
2.   **Delivery_person_Ratings:** Faster delivery times tend to receive higher ratings.

##### Vehicles
1.   **Vehicle_condition:** The condition of the vehicle affects the delivery time. A good vehicle condition ensures faster delivery. Regular maintenance plans for the vehicle are necessary.
2.   **multiple_deliveries:** Multiple deliveries affect the delivery time. It is necessary to calculate and adjust accordingly.

##### Order and Timing
1.   **Time_Orderd:** The time frame from 5 PM to 10 PM has a longer delivery rate than average. It is necessary to increase personnel during this period.
2.   **Festival:** Delivery times during the Festival are always higher. There is a need to plan for staffing for the Festival.

##### Weather and traffic conditions
1.   **Weather_conditions:** Weather conditions affect delivery time, sunny is the best.
2.   **Road_traffic_density:** Road Traffic affect delivery time. It is necessary to improve the routing application to avoid high traffic density routes.

##### Area
1.   **City:** Semi-Urban have Time - Taken is so high. Need to have a solution to fix.


### **👉 Top yếu tố làm tăng thời gian giao hàng (dựa theo hệ số hồi quy):**
| Biến                          | Hệ số ảnh hưởng | Giải thích                                                                       |
| ----------------------------- | --------------- | -------------------------------------------------------------------------------- |
| `Delivery_location_longitude` | **48.46**       | Khoảng cách địa lý xa hơn (toạ độ longitude lớn hơn) → tăng thời gian giao hàng. |
| `City_Semi-Urban`             | **11.31**       | Giao hàng tại vùng bán đô thị khiến thời gian giao hàng cao hơn đáng kể.         |
| `Festival_Yes`                | **10.60**       | Giao hàng trong dịp lễ tốn thời gian hơn do tắc nghẽn, thiếu nhân lực.           |
| `multiple_deliveries`         | **3.14**        | Mỗi lần thêm 1 đơn hàng trong cùng chuyến đi làm tăng thời gian.                 |
| `Delivery_person_Age`         | **0.38**        | Tuổi lớn hơn liên quan đến tốc độ giao hàng chậm hơn một chút.                   |
| `Road_traffic_density_Jam`    | **0.26**        | Khi giao hàng trong điều kiện "Jam" (kẹt xe), thời gian tăng lên đáng kể.        |

