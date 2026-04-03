# Alarm Group

Alarm groups are used to categorize alarms with similar characteristics or relevance. For example, all alarms from the same production line or equipment can be grouped together into an alarm group, making management and monitoring more convenient.

In **Realtime Alarm control**, users can filter or sort alarms based on these alarm groups. For instance, the interface can be set to display alarms from only a specific alarm group. This is particularly important in large systems, as it reduces information overload and enhances the efficiency of operators.

![alt text](11.png)

## How to use？

#### Add

1. In the "Alarming" -> "Alarm Groups" page, click the "Add" button to create a new alarm group.
    ![alt text](12.png)
2. In the pop-up window, set the alarm group’s name, and click the "Add" button to add tags to the alarm group.
    ![alt text](13.png)

    | **Name**    | **Description** |
    |-------------|---------------|
    | Name        | The name of the alarm group. The name must be unique and is required. |
    | Description | Description of the alarm group. It is optional.   |
    | Tag         | Assign tags to this alarm group.    |
    
3.After completing the configuration, click the "OK" button to finish adding the item.

#### Search

By default, alarm groups are sorted in descending order based on the creation time. Users can customize the sorting as needed.

Users can use the search box in the upper right corner to search by alarm group name or tag path. When searching by tag path, the results will display all alarm groups associated with the tag.

#### Edit

Click the "Edit" button on any entry in the alarm group list to modify the alarm group information. In the edit pop-up window, all tag paths associated with the alarm group will be displayed.

**Note:** After modifying the alarm group name, the tags that were using this group will lose their group information. Please be cautious when modifying the name.

![alt text](14.png)

#### **Delete**

Click the delete button to remove an alarm group. 

**Note:** When an alarm group is deleted, the tags bound to this group will lose their group information. Please be cautious when deleting.