# Aggregation Modes for Historical Tags

For tags with historical storage enabled, historical data can be queried using aggregation modes.

**Aggregation mode** is a data processing method used for querying or displaying historical data. Typically, a time range is divided into multiple time intervals (based on time periods or a fixed number of points). Within each interval, data is processed according to the selected aggregation mode, enabling users to quickly extract valuable insights.

**VC Hub** supports the following aggregation modes:

- **Max**: The maximum value within the time interval.
- **Min**: The minimum value within the time interval.
- **Avg**: The average of all data points within the time interval.
- **First**: The first data point within the time interval.
- **Last**: The last data point within the time interval.
- **Count**: The number of data points within the time interval.
- **Range**: The difference between the maximum and minimum values within the time interval.
- **Count On**: The number of times the value changes from 0 to a non-zero value within the time interval.
- **Count Off**: The number of times the value changes from a non-zero value to 0 within the time interval.
- **Duration On**: The cumulative duration (in seconds) within the time interval when the value is non-zero.
- **Duration Off**: The cumulative duration (in seconds) within the time interval when the value is 0.
