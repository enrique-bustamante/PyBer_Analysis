# PyBer Analysis Report

## Background and Results

### Purpose

The purpose of this analysis is to determine how to better serve the
underserved portion of the population in order to make fares more affordable.

### Technical Analysis There were two items we created to analysize the
dataand make a determination: a summary table by city type and a chart showing
the weekly total fare by city type. To create the summary table, we first
merged the two existing city and rides dataframes. Next, we created Pandas
DataSeries to find total rides, total drivers, total fares, fares per ride,
and fares per driver. A dataframe was then created by combining these series
and we used the groupby() function to create this summary table by city type.
The summary table is displayed as figure 1 below in the Results section.

To create the data for the line chart, we took the pyber_data_df and renamed
the columns, set the index to "Date", made a copy using only the "City Type"
and "Fare", and changed index to Datetime. We then used groupby() and sum to
arrange by date, used pivot_table() to transform the dataframe into one
displaying the fares by date by city type. Finally, we filted the dataframe to
include on dates between January 1st to April 28th and used resample() to
change the index to a weekly date.

To create the chart itself, we used the object oriented approach to create the
figure. We imported matplotlib pyplot, used the fivethirtyeight style chart,
and plotted each city type within the figure on a weekly basis. The axis was
changed to reflect a monthly interval. The chart is displayed in Results as
Figure 2.

### Results

Figure 1: City Type Summary ![Summary Dataframe](/analysis/CitySummary.png)

Figure 2: Total Fares by City Type
![TotalRatesWeekly](/analysis/TotalRatesWeekly.png)

### Summary

Looking at the summary table, it is clear that there are more rides and
drivers in Urban areas than in Suburban and Rural areas. This resulted in more
total fares in Urban areas as well. The fare per ride and per driver are lower
in Urban areas as well. If we turn our attention to the total fare by city
type chart, week over week, Urban areas had more total fares than Suburban and
Rural areas as well. There seems to be a correlation between number of rides
and fare amount; as the number of rides increase, the fare average decreases.
The same goes for number of drivers.

## Challenges Encountered and Overcome

### Challenges and Difficulties Encountered

While no issues were encountered while programming, there are some potential
problem areas. When merging the data tables, the resulting "driver count"
column will have duplicates each time the city name comes up. We had to use
the city_data_df dataframe to find the true driver count.

While creating the line chart, it was difficult to set a monthly axis to a
weekly data set. This issue was overcome by importing DateFormatter and
MonthLocator, and setting them to the major format and locator for the x axis.


## Recommendations and Next Steps

Based on the data, it would seem that having more drivers my be the correct
approach in these other areas. We may have not looked at the data deep enough,
though. We should also look to see what days the fares may be lower in these
areas. We could use the resample function to get the daily fares then group
them by their appropriate day of the week. We could also look at the time of
day and compare the rates by resampling by hour and creating a line chart
comparing the City Types.


### Recommendations for Future Analysis

We may also be working from incomplete data. While it may appear that the
fares per ride and fares per driver are higher due to less rides and drivers,
but there may be other factors that we don't have available in this data set.
The rural and suburban rides could be longer than those in the Urban area. For
future analysis, it may be best to also see how many miles each trip is and to
compare the rates per mile per city type to get a better idea of where we can
make changes to make fares for Rural and Suburban areas more affordable.
