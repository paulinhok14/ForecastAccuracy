# ForecastAccuracy
Forecast Accuracy QlikView dashboard

Internally developed Model.

Assumptions:

Forecast and Demand streams considered for each business unit is set by key-users in the dashboard criterias spreadsheet (Forecast Accuracy Parameters.xlsx), located in: ' & '$(vDashboardPath)' & '.

Also, the Forecast and Demand Streams table from Servigistics is also saved in the dashboard folder, in order to check the Stream Names.



First of all, the aggregated value presented in Main Tab is the calculation of the below method for each pair (Ecode & Location), and the aggregate method of them is a simple average. Every filter that is applied recalculates the value based on this method and respecting values filtered.

The calculation starts by treating exceptions, if:

A- Demand = Forecast:    												Accuracy 100
B- Demand 0 and Forecast different from 0: 							Accuracy 0
C- Demand different from 0 and Forecast 0:							Accuracy 0

After the exceptions, accuracy is calculated in a conditional way:

If Demand > Forecast:

| Demand - Forecast | / Demand

If Forecast > Demand:

| Demand - Forecast | / Forecast


Be aware that the value of Demand and Forecast is always summarized. e.g: If the selected period is 6 months, the total Demand and the total Forecast of these 6 months will be first summarized and then compared. And so on for another period filters.
