# Batch Instantiate Models

You can batch instantiate models in the following way.

1. In the "Instance" tab, click the "Add" button and select "Instance."<br>
    ![alt text](21.png)
2. In the "Instance" tab, right-click on the folder and select "Add Instance" from the context menu.<br>
    ![alt text](22.png)
3. In the "Models" tab, right-click on the model and select "Add Instance" from the context menu.<br>
    ![alt text](23.png)


## Modify instance properties through the page

Click the setting button next to "Batch Generate", enter the number of instances to generate and the starting sequence number, and generate multiple instances.

![alt text](24.png)


In the custom list, display the generated instances along with their corresponding custom attributes. You can modify the cell content as needed.

![alt text](25.png)


When the number of instances or custom attributes is large, performing operations directly on the page may be inconvenient. Therefore, we also provide an export and import function. You can export the data, edit it in Excel, and then import it back.

## Modify instance attributes through the exported file

#### Export 

After generating instances, click the **Export** button to export the instances.

![alt text](26.png)


After the export is successful, edit the file in Excel according to the exported format. Each row represents an instance. The first column is the instance name, and the remaining columns are the custom parameters of the selected model.

![alt text](27.png)


**Notes:**  

1. Columns created manually in Excel will not appear in the custom list after import. 
2. If a custom property column is deleted in Excel, the corresponding values in the custom list will be empty after import. 


#### Import 

After modifying the file, click the "Import" button to import the file.

![alt text](28.png)


After the import is complete, click the "OK" button to generate multiple instances in the asset tree.


