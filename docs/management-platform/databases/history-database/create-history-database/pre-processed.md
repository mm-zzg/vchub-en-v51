# Pre-Processed

 The history database  has the option to enable "Pre-Processed". When it is enabled, history will be stored in two different sets of partitions: a **normal partition** and a summarized **"pre-processed" partition**.

 In summary, the "pre-processed" partitions summarize the data stored in the normal partitions and put it into additional tables in the database. Although this takes up more space in the database, it can significantly improve query speed by reducing the number of data points generated. When enabled, tag history queries will use the pre-processed table if data is requested at intervals greater than the specified "pre-processing window size(min)"setting. 
 
 For example, suppose you select an aggregate (max, min, average) query with a sampling interval of 90 seconds in Controls: Historical Data Table, and if you set the "pre-processing window size (min)" to be less than 90 seconds (e.g., the default value of 1 minute), the query will use the pre-processed table in the "pre-processing partitions" query. 

 On the other hand, if the same conditions are used and the sampling interval is set to a value less than the size of the "pre-processing w indow size (min)", the original table will be used. 
 
 Both examples will retrieve data from the historical database, but the result set of the first query will be less accurate than the query of the second example.

 When pre-processed is enabled, a new partitioned table will be created to store the preprocessed records. The preprocessing partition will store data as one table per natural month.

**Note**: When InfluxDB is selected , there is no configuration for partitioning, pre-processing, and data cleaning (InfluxDB itself has the above configurations,  VC Hub does not provide this configuration). 

**Configuration Description**

| **Configuration Item** | **Description**   |
|-----------------------|--------------|
| Enable Pre-processed  | Enables or disables preprocessing.   |
| Pre-Processing Window Size(min)    | The interval of time window when preprocessing historical data. <br>For example, if the time is set to 1 min, the preprocessing table will summarize the raw data of 1min, calculate the maximum, minimum and average values within this 1 min,and store them to the preprocessing partition. |

