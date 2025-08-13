# Hotel-Booking-Analsyis


## Overview:
This project explores hotel booking patterns, lead times, and cancellation trends using Python.
The analysis aims to uncover actionable insights for hotel revenue optimization and operational efficiency.


## Dataset
The dataset contains booking information for both a City Hotel and a Resort Hotel, with the following features:

```
- hotel: Type ( City or Resort)
- is_canceled: Whether the booking is canceled or not (0 for no canceled and 1 for canceled)
- lead_time: time (in days) between booking transaction and actual arrival.
- arrival_date_year: Year of arrival
- arrival_date_month: month of arrival
- arrival_date_week_number: week number of arrival date.
- arrival_date_day_of_month: Day of month of arrival date
- stays_in_weekend_nights: No. of weekend nights spent in a hotel
- stays_in_week_nights: No. of weeknights spent in a hotel
- adults: No. of adults in single booking record.
- children: No. of children in single booking record.
- babies: No. of babies in single booking record. 
- meal: Type of meal chosen 
- country: Country of origin of customers (as mentioned by them)
- market_segment: What segment via booking was made and for what purpose.
- distribution_channel: Via which medium booking was made.
- is_repeated_guest: Whether the customer has made any booking before(0 for No and 1 for Yes)
- previous_cancellations: No. of previous canceled bookings.
- previous_bookings_not_canceled: No. of previous non-canceled bookings.
- reserved_room_type: Room type reserved by a customer.
- assigned_room_type: Room type assigned to the customer.
- booking_changes: No. of booking changes done by customers
- deposit_type: Type of deposit at the time of making a booking (No deposit/ Refundable/ No refund)
- agent: Id of agent for booking
- company: Id of the company making a booking
- days_in_waiting_list: No. of days on waiting list.
- customer_type: Type of customer(Transient, Group, etc.)
- adr: Average Daily rate.
- required_car_parking_spaces: No. of car parking asked in booking
- total_of_special_requests: total no. of special request.
- reservation_status: Whether a customer has checked out or canceled,or not showed 
- reservation_status_date: Date of making reservation status.
```

- Total number of rows in data: 119390
- Total number of columns: 32
## Data Cleaning and Feature Engineering

### (1) Removing Duplicate rows

### (2) Handling null values
- company and agent → replaced with 0 (no company/agent booking).
- country → replaced with "Others".
- children → replaced with 0 if missing.
- Rows with children = 0, adults = 0, and babies = 0 were removed.
  
### (3) Data Type Conversion

- children, company, and agent → converted to int64.
- reservation_status_date → converted to datetime.

### (4) New columns
- total_stay = stays_in_weekend_nights + stays_in_week_nights
- total_guests = adults + children + babies

## Exploratory Data Analysis
- Checked for correlation and created a heatmap
- One outlier was found in the `adr` column and was dropped

Performed correlation analysis, visualized trends, and answered the following questions:
```
 Q1) Which Agents had the highest number of bookings?
 Q2) What's the most booked room type?
 Q3) Which room types tend to have higher ADR?
 Q4) Which meal types are most commonly booked?
 Q5) What's the booking ratio for each hotel?
 Q6) What is the most common booking channel?
 Q7) What are the months with the highest bookings ?
 Q8) What are the top 10 nationalities ?
 Q9) what are the top Stay Lengths?
 Q10) What is the Hotel Revenue ditribution?
 Q11) What is the median lead time for bookings at each hotel?
 Q12) How does total stay vary between hotel types?
 Q13) Which hotel has higher cancellation rate?
 Q14) Which hotel has more repeating guests?
 Q15) Which distribution channel generates more revenue?
 Q16) What's the waiting period's effect on cancellation rate?
 Q17) Does allocating a different room type affect the cancellation rate?
 Q18) Does allocating a different room type affect the ADR?
 Q19) What type of guests do the hotels have?
 Q20) what's the cancellation rate by booking channel ?

```
Visualization Methods
- Bar Plot.
- Histogram.
- Scatter Plot.
- Line Plot.
- Heatmap.
- Box Plot
             
### Key Insights:

#### Customer Behavior
1. Most guests are from European countries, with the highest number from Portugal.
2. The most common stay length is ≤ 4 days. City Hotel is preferred for short stays, Resort Hotel for long stays.
3. Most bookings are made by couples (two adults).
4. Repeat guests are rare, though Resort Hotel has a slightly higher repeat percentage.
5. Arrivals increase on weekends, and ADR tends to rise at month-end.

#### Revenue Insights
1. Room type A is most in demand, but room types H and G generate higher ADR. Increasing A and H availability can maximize revenue.
2. City Hotel has a slightly higher ADR and more bookings, resulting in greater total revenue.
3. Receiving a different room type rarely causes cancellations but slightly reduces ADR.
4. July and August are the busiest months for both hotels..

#### Booking Channels & Lead Time
1. TA/TO is the most common booking channel.
2. TA/TO bookings have the highest cancellation rate (~30%).
3. Longer lead times do not increase cancellation likelihood.
4. City Hotel has a slightly higher median lead time; both hotels see early planning from customers.

#### Cancellations
1. Almost 30% of City Hotel bookings are canceled.
2. Receiving a different room type is not a major cause of cancellations.

#### Individual Contributors
1. Agent No. 9 has made the highest number of bookings.

## Challenges

(1)Large number of duplicate records.
(2)Incorrect data types for several columns.
(3)Significant missing values in multiple fields.
