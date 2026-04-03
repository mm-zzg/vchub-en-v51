# History

In the industrial world, in addition to monitoring the real-time status of a device, it is often necessary to record historical data, such as the energy consumption of a device, in order to analyze the production status and optimize the production efficiency.

In VC Hub, tags are an important medium for receiving device values and issuing commands. In order to make the storage of historical values more realistic and to reduce server hardware storage consumption, tags support various recording modes.

## **How to Enable**

In the editing popup window of the tag, there is a history switch at the top of the popup window, turn it on to set the history.

![alt text](9.png)

When you turn it on, the popup window will automatically display the history configuration items, users can set the history according to the actual needs, click **"** **OK** **"** button after finishing the settings.

![alt text](10.png)

| **Name**          | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mode              | There are 2 modes:  <br>- On Change: Store when the value of the tag changes. <br>- Periodic: Store the value of the tag according to the set storage period. <br>- Raw: Store using the original values.    |
| Compression Mode  | Only Integer and Double type tags can be configured. The compression rule reduces the amount of data actually stored in the database to reduce the load on the server hard disk while meeting the production requirements.  <br>There are two types of compression modes:  <br>- **Delta compression**: calculates the deadband by compressing the type and value, subtracting the current value from the last stored value of the tag, and if the difference is within the deadband, it will not be stored. <br>  ![alt text](11.png)  <br>- **Slope Compression**: Calculated using the value, mostly used for tags that need to observe historical values on chart-like controls. For example, slope compression can be used to make a trend chart appear smoother. The larger the value, the more pronounced the smoothing effect, but the higher the compression level.  <br> ![alt text](12.png)|
| Compression Type  | Configurable when the compression mode is Tag Compression, there are two types: Absolute, Percentage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Value             | The base number for the compression rule calculation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Storage Period    | Configurable when the compression mode is cycle storage, it can be used with the cycle unit, for example, if the cycle is set to "1" and the cycle unit is set to "minutes", then every 1 minute, take the latest value of the tag to judge whether to store it or not.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Timeout Fallback  | Whether to enable timeout value. You need to set the timeout interval. The system will judge whether a new value has been stored in the interval, if no new value is stored in the interval, the last stored value will be stored again in the database with the current time.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Fallback Interval | The time interval for timeout makeup, used in conjunction with the time unit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

## **Change Compression Calculation Rules**

#### **Compression type is absolute**

|new value - last stored value | is greater than the value, greater is stored, otherwise ignored.

![alt text](13.png)

#### **Compression type is percentage**

|new value - last stored value| is greater than deadband, greater is stored, otherwise ignored. Deadband = Value * (Engineering Upper Limit - Engineering Lower Limit) /100

![alt text](14.png)

## **Slope Compression Calculation Rules**

Every time the value of a tag is changed, the upper and lower slope values are calculated. These slope values are stored in memory and are ultimately used to determine when to store the new value. The calculations used are as follows:

**Upper Slope Rate**

(((new value + value in history configuration) - last stored value) / (new value timestamp - last value timestamp))

**Down slope rate**

(((new value - value in history log configuration) - last stored value) / (new value timestamp - previous value timestamp))

**How to judge**

The algorithm stores new values only under the following conditions:

- When using this method, the system always stores the first value on the tag because subsequent values require an initial value to calculate the slope.
- If the newly computed upper slope is less than the previously computed downslope rate value, the system stores the new value.
- If the newly calculated lower slope is greater than the previously calculated upper slope rate value, the system stores the new value.
- The system always stores a value when the mass on the tag changes.

If a new value is not stored, the system compares the newly calculated slope value to the previously calculated value:

- If the new lower slope is less than the previous upper slope, the new upper slope is used for future comparisons.
- If the new lower slope is greater than the previous lower slope, the new lower slope will be used for future comparisons.




