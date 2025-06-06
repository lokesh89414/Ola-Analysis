# Ola-Analysis
# 🚖 OLA Data Analyst Project

This project presents data-driven insights from Ola ride booking data using SQL queries. It explores booking patterns, customer preferences, ride statistics, and payment behavior to support business intelligence decisions.

---

## 📁 Dataset

- **File:** `Bookings-20000-Rows - July.csv`
- **Rows:** 20,000+
- **Key Columns:**
  - `Booking_ID`
  - `Customer_ID`
  - `Vehicle_Type`
  - `Booking_Status`
  - `Ride_Distance`
  - `Payment_Method`
  - `Booking_Value`
  - `Customer_Rating`
  - `Driver_Ratings`
  - `Incomplete_Rides`
  - `Incomplete_Rides_Reason`
  - `cancelled_Rides_by_Driver`

---

## 📊 Visual Insights Dashboard

1. **Ride Volume Over Time**  
   → Time-series chart showing daily/weekly ride counts.

2. **Booking Status Breakdown**  
   → Pie/doughnut chart for booking statuses (success, cancelled, etc.).

3. **Top 5 Vehicle Types by Ride Distance**  
   → Bar chart of vehicle types ranked by total distance.

4. **Average Customer Ratings by Vehicle Type**  
   → Column chart comparing ratings by vehicle type.

5. **Cancelled Rides Reasons**  
   → Bar chart of customer/driver cancellation reasons.

6. **Revenue by Payment Method**  
   → Stacked bar chart by payment types.

7. **Top 5 Customers by Total Booking Value**  
   → Leaderboard of high-spending customers.

8. **Ride Distance Distribution Per Day**  
   → Histogram/scatter plot of ride distance by date.

9. **Driver Rating Distribution**  
   → Box plot by vehicle type.

10. **Customer vs. Driver Ratings**  
    → Scatter plot showing rating correlation.

---

## 🛠️ SQL Setup

```sql
CREATE DATABASE Ola;
USE Ola;
```

---

## 📌 SQL View Creation & Explanation

1. ✅ **All Successful Bookings**
```sql
SELECT * FROM ola.bookings WHERE Booking_Status = 'Success';
```

2. 📏 **Average Ride Distance by Vehicle Type**
```sql
SELECT Vehicle_Type, AVG(Ride_Distance) AS avg_distance
FROM ola.bookings
GROUP BY Vehicle_Type;
```

3. ❌ **Total Cancelled Rides by Customers**
```sql
SELECT COUNT(*) FROM ola.bookings WHERE Booking_Status = 'cancelled by Customer';
```

4. 👑 **Top 5 Customers by Rides**
```sql
SELECT Customer_ID, COUNT(Booking_ID) AS total_rides
FROM ola.bookings
GROUP BY Customer_ID
ORDER BY total_rides DESC
LIMIT 5;
```

5. 🔧 **Rides Cancelled by Drivers for Personal/Car Issues**
```sql
SELECT COUNT(*) FROM ola.bookings WHERE Canceled_Rides_by_Driver = 'Personal & Car related issue';
```

6. ⭐ **Max & Min Driver Ratings for Prime Sedan**
```sql
SELECT MAX(Driver_Ratings) AS max_rating, MIN(Driver_Ratings) AS min_rating
FROM ola.bookings
WHERE Vehicle_Type = 'Prime Sedan';
```

7. 💸 **All Rides Paid via UPI**
```sql
SELECT * FROM ola.bookings WHERE Payment_Method = 'UPI';
```

8. 🌟 **Average Customer Rating by Vehicle Type**
```sql
SELECT Vehicle_Type, AVG(Customer_Rating) AS avg_customer_rating
FROM ola.bookings
GROUP BY Vehicle_Type;
```

9. 💰 **Total Booking Value for Successful Rides**
```sql
SELECT SUM(Booking_Value) AS total_successful_value
FROM ola.bookings
WHERE Booking_Status = 'Success';
```

10. 📝 **All Incomplete Rides & Reasons**
```sql
SELECT Booking_ID, Incomplete_Rides_Reason
FROM ola.bookings
WHERE Incomplete_Rides = 'Yes';
```

---

## 🔍 Summary

This project leverages SQL queries to analyze Ola ride data effectively. The visualizations and insights derived can aid in decision-making, improving customer experience, and optimizing operations.

---
