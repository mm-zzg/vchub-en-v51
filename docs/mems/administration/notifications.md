# Notifications


## 1. Message Notifications in MEMS


Message notifications indicate normal system events, successful operations, or automatic regulation activities, generally divided into three categories based on severity and display color:

![alt text](u9.png)

| Color | Severity | Meaning | Typical Operator Action |
| :--- | :--- | :--- | :--- |
| Yellow | Warning | A potential issue or abnormal condition that requires attention. | Monitor the condition and take preventive action if necessary. |
| Red | Error / Critical | A fault, failure, or critical condition that may affect system operation. | Immediate action is required. Follow the alarm handling procedure. |
| Black | Info | A normal event, status change, or successful operation. | No immediate action is required. Review if necessary. |


The following action will trigger info message on black icon:

1. VC Hub is successfully connected

2. Sync is started or completed

3. System trigger Peakload regulation

4. System trigger Avoid Peakload regulation

5. System trigger Reactivation regulation

6. System stop Reactivation regulation


The following action will trigger Error / Critical message on red icon:

1. VC Hub is disconnected

2. License expired

The following action will trigger Warning message on yellow icon:

1. Sync failed

2. No License is available

3. License almost expired

4. Surplus regulation failed


The count of unread messages is displayed at the top of the icon. Click the icon, and detailed messages will be shown in the list.

Click the 'Mark all read' button, and the system will automatically mark all unread messages as read; the number of unread messages will decrease to 0.

Click the 'Clear all' button, and the system will automatically delete all messages in the list.

![alt text](u1.png)

Error / Critical messages cannot be removed from the notification list until the user has explicitly acknowledged them. This prevents critical events from being missed, ignored, or deleted without review.

![alt text](u2.png)

![alt text](u3.png)

![alt text](u4.png)

When all Error / Critical or Warning messages are cleared, the relevant icon will disappear.

![alt text](u5.png)




### 2. Alerting Notifications from Grafana


#### 2.1 Notification configuration

Open Grafana website of MEMS enviornment

Click 'Alerting' sidebar button

Click Notification configuration> Contact points

![alt text](n1.png)

Click 'Add contact point' to add new notification email address


![alt text](n2.png)

Fill in Name; Select Email integration; Fill in Email address; Click 'Save contact point' 


![alt text](n3.png)


The page will turn to 'Contact points' tab, configurated Contact point will display nad marked as 'Unused'

![alt text](n4.png)



Click 'Edit' button, user can modify Notification configuration 

![alt text](n5.png)

Click 'Test' button, system will send email to test verify the configurated address can receive message from Grafana

![alt text](n6.png)

![alt text](n7.png)

Open website of receiving notifications, user can see the specific message of Alerting Notifications from Grafana

![alt text](n8.png)

#### 2.2 Alert rules

Click Notification configuration > Contact points > Audit Log Pipeline Health button

![alt text](n9.png)

When unable Third-party audit log while MEMS system is running, status of Audit Log Pipeline Health will turn to 'Firing' and be red



