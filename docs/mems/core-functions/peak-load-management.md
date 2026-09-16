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
| Grid Power                | The actual power currently drawn from the grid. 
| Remaining Headroom        | The available power remaining before reaching the peak Setpoint. |
| 15-Minute Grid Power Forecase | The system's predicted average grid power for the next 15 minutes, used for proactive decision-making. |
| Control Stage             | The current control stage the system is in.|
| SoC Battery Storages      | The average State of Charge (SoC) percentage of all connected controllable battery storage.|

### 3.2 Real-time Trend Chart
The chart displays the trends of power parameters over time:

### 3.3 Legend

## 4. Configuration Settings page

## 5. Configuration Settings page