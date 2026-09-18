# Peak Load Management
## 1. Introduction
Peak Load Management is designed to help users monitor and control power consumption within a microgrid. Its primary goal is to prevent power peaks from exceeding a defined threshold (Setpoint), thereby avoiding high demand charges or grid overloads. By integrating Battery Energy Storage, the system can automatically discharge power when a peak is imminent, achieving "peak shaving."

## 2. Interface Navigation & Layout
The main navigation menu is located on the left side of the screen, with "Peak Load Management" currently selected. This module contains three main tabs:

**Overview**: Displays real-time power status, forecasts, and system active control states

**Configuration Settings**: Used to display predefined limits, limits based on constraints, and different actions to avoid peak load

**Priority List**: Used to display the priority of various Charging Infrastructure(WALM) when peak load shedding is required.

![alt text](Peak_Load_Management.png)

## 3. Overview page
The Overview page is divided into four main areas: **Key Metrics Cards**, **Real-time Trend Chart**, **Legend**, and **Active Controls List**.

### 3.1 Key Metrics Cards
The five cards at the top of the page provide core operational data for the current system status:

| **Name**                  | **Description** |
|---------------------------|---------------------|
| Grid Power                | The actual power currently drawn from the grid. |
| Remaining Headroom        | The available power remaining before reaching the peak Setpoint. |
| 15-Minute Grid Power Forecast | The system's predicted average grid power for the next 15 minutes, used for proactive decision-making. |
| Control Stage             | The current control stage the system is in.|
| SoC Battery Storages      | The average State of Charge (SoC) percentage of all connected controllable battery storage.|

### 3.2 Real-time Trend Chart
The chart displays the trends of power parameters over time:


### 3.3 Legend


## 4. Configuration Settings page
This page is divided into two main areas: **Limits for Peak Load Detection** and **Actions to Avoid Peak Load**.

### 4.1 Limits for Peak Load Detection

Predefined Limits: 

The values are from Project Settings - General - Load Management settings.
Click the gear icon ⚙️ Limits, it navigates to Project settings page, and you can set values for Setpoint, Upper Threshold, Lower Threshold here.
![alt text](Limit.png)
![alt text](Project_setting.png)

Limits Based On Constraints:

If not configured, it displays as -kw.
![alt text](Not_configured_constraints.png)
If configured, the values are from Enabled Grid Setpoint Change constraint. 
Click the gear icon ⚙️ Constraints, it navigates to Constraints & Tasks page, and you can add new Constraints and Tasks here.
![alt text](Constraint.png)
![alt text](Constrints_Tasks.png)
If you want to add a new Grid Setpoint Change constraint, you can click "Add" button, then select "Grid Setpoint Change" Constraint Type and enter suitable values, then click "Add" button.
![alt text](Constraint_Add_1.png)
![alt text](Grid_setpoint_change_constraint.png)
![alt text](Enabled_grid_setpoint_change.png)
![alt text](Limits_based_on_constraints.png)
During Grid Setpoint Change type constraint enabled period, System's Setpoint, Upper Threshold, Lower Threshold of Predefined Limits are overwrite temporaryby Limits Based on Constraints.
![alt text](Peak_load_management_constraint_setponit_1.png)
![alt text](Peak_load_management_constraint_setponit_2.png)

Note: Grid Setpoint Change type Constraint needs to wait to next 15-Minute Time Frame.

### 4.2 Action to Avoid Peak Load
When the system meets the trigger condition, the system will execute actions defined here in the order of "Stages."

#### Stage configuration

•Add a new Stage 1 - Discharge all at once for Battery Storages

1. Click the green + Add Stage button

2. Select "Discharge Battery Storages" for "Action" field

3. Select "Dischage all at once" for "Discharge selection" field

4. Enter suitable value for "Reduce to Target SoC"

5. Select target battery storage for "Component" field

6. Click "Save" button, and Stage 1 is created successfully.
![alt text](Add_stage_1.png)
![alt text](Add_stage_2_1.png)
![alt text](Add_stage_3_1.png)

Notes：
1. If the battery storage's SoC is "Not Set", "Some components have no Minimum SoC. Please change in component settings." message is displayed, and you can click "Edit" button to set it.
![alt text](SOC_Not_set_1.png)
![alt text](SOC_Not_set_2.png)
    Steps:
    1. Click "Edit" button,there will open a new window, and navigate to "Microgrid Components - Components- Control Parameters" page.

    2. Click "Edit" button, enter suitable value for "Minimum State of Charge" field, click "Save" button.
    ![alt text](SOC_Not_set_3.png)
    ![alt text](SOC_Not_set_4.png)
    ![alt text](SOC_Not_set_5.png)
    3. Switch to the first window, the setted value is populated.
    ![alt text](SOC_Not_set_6.png)
2. If value of "Target SoC/Minimum SoC" is higher than value of "Reduce to Target SoC", "Minimum SoC of some components is higher than Target SoC. " message will display, you can still add the battery storage to the stage.
![alt text](SOC_mini.png)

3. If you want to add more Components on this stage, you can click "Add Component" button.
![alt text](Add_component.png)

4. If you want to delete added Component, you can click "Trash" button.
![alt text](Trash.png)

•Add a new Stage 2 - Discharge one after each other for Battery Storages.

1. Click the green + Add Stage button

2. Select "Discharge Battery Storages" for "Action" field

3. Select "Dischage one after each other" for "Discharge selection" field

4. Select target battery storage for "Component" field

5. Click "Save" button and Stage 2 is created successfully.
![alt text](Add_stage_1.png)
![alt text](Add_stage_2_2.png)
![alt text](Add_stage_3_2.png)

•Add a new Stage 3 - Decrease Consumption of Controllable Consumers

1. Turn on the toggles that you wanted.

2. Click "Save" button and Stage 3 is created successfully.
![alt text](Add_stage_1.png)
![alt text](Add_stage_2_3.png)
![alt text](Add_stage_3_3.png)

•Add a new Stage 4 - Turn Off Binary Controlled Consumer

1. Click the green + Add Stage button

2. Select "Turn off Binary Controlled Consumer" for "Action" field

3. Select target component for dropdown list for "Component" field

4. Click "Save" button, and Stage 4 is created Successfully.
![alt text](Add_stage_1.png)
![alt text](Add_stage_2_4.png)
![alt text](Add_stage_3_4.png)


•Edit a Stage

1. Click "Edit" button.
![alt text](Edit_icon.png)
2. Selected target values.
![alt text](Edit_stage.png)
3. Click "Sava" button.
![alt text](Edit_stage_save.png)

•Delete a Stage
1. Click "Delete" button
![alt text](Delete_1.png)
2. Click "Delete Anyway" button
![alt text](Delete_2.png)

•Notification of the User stage

This stage is default notification stage, this stage is entered when automatic control methods have been exhausted but the overload problem persists.
![alt text](Notification_default.png)
![alt text](Notification.png)

#### Explanation of Stage

**Discharge Battery Storages**

| **Name**                  | **Description**                      |
|---------------------------|--------------------------------------|
| Target                    | The desired state of charge (SoC) the battery storage is intended to discharge down to.                  |
| Actual                    | Real-time state of charge (SoC).                                                             |
| Blocked                   |                                      |

**Descrease Consumption of controllable Consumers**
| **Name**                  | **Description**                      |
|---------------------------|--------------------------------------|
| Low Priority              | Classification for Components that are minimal.                                                           |
| Mid Priority              | Classification for Components that are important, but not critical.                                       |
| High Priority             | Classification for Components that are critical.                                                          |
| Limit                     |                                      |
| Previous                  |                                      | 

**Turn Off Binary Controlled Consumer**
| **Name**                  | **Description**                      |
|---------------------------|--------------------------------------|
| Low Priority              | Classification for Components that are minimal.                                                           |
| Mid Priority              | Classification for Components that are important, but not critical.                                       |
| High Priority             | Classification for Components that are critical.                                                                                                                     


 ## 5. Priority List page