# Bikeshare Demand Assessment and Ridership Growth Strategies: Washington, DC 🚲🇺🇸

## Overview

This project is an exploratory analysis of bikeshare ridership patterns in Washington, DC, using daily rental data from 2011–2012. I successfully identified opportunities to increase casual bikeshare ridership and develop strategies to encourage more frequent use of the system.

### The Opportunity in Casual Riders ‼️

I'm particularly interested in casual riders because they represent a potential opportunity for long-term ridership growth. If we can attract more casual riders and encourage them to ride more frequently, we may also be able to convert more casual riders into registered members.

By understanding when people use bikeshare and what might encourage them to ride more often, we can develop strategies that support both ridership growth and the adoption of cycling as an everyday mode of transportation.

## Data & Methods 💻
### Data
This project uses the [Bike Sharing Dataset from the UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset).

The analysis uses `day.csv`, which contains daily bikeshare rental records from Washington, DC, for 2011–2012. The dataset distinguishes between casual and registered rentals and includes weather, seasonal, and calendar variables.

### Methods 
To identify ridership growth opportunities, I compared average daily rentals across three dimensions:

#### 🗓️ Day of the Week:
```python
week = df.groupby("weekday",sort=False)[["casual", "registered", "cnt"]].mean().reset_index().round(2)
day_order = ["Sunday", "Monday", "Tuesday", "Wednesday",
             "Thursday", "Friday", "Saturday"]

week = week.set_index("weekday").loc[day_order].reset_index()
```

#### 🍂 Season
```python
season = df.groupby("season")[["casual","registered"]].mean().reset_index().round(2)
season_order = ["Winter", "Spring", "Summer", "Fall"]
season = season.set_index("season").loc[season_order].reset_index()
```

#### 💭 Day of the Week Within Each Season
```python
winter_weekday = df.groupby(["season","weekday"])[["casual","registered"]].mean().reset_index().round(2)

day_order = ["Sunday", "Monday", "Tuesday", "Wednesday",
             "Thursday", "Friday", "Saturday"]
winter_weekday = winter_weekday.set_index("weekday").loc[day_order].reset_index()

season_order = ["Winter", "Spring", "Summer", "Fall"]
winter_weekday = winter_weekday.set_index("season").loc[season_order].reset_index()
```

Throughout the analysis, I was looking to find when casual ridership is higher or lower and how casual demand patterns differ from registered demand. 






