# Smart City Bike Sharing Data Analysis

## 📌 Project Overview
This project features a global **Power BI dashboard** designed to track bike-sharing station availability across Europe, the Americas, and Japan. The goal is to provide actionable insights for city planners and operators to optimize fleet distribution and ensure a seamless experience for riders.

## 🎯 Objectives
*   **Rebalance Fleet:** Identify full vs. empty stations to move bikes to where they are needed most.
*   **Improve Service:** Ensure riders always have access to a bike or a vacant parking dock.
*   **Global Monitoring:** Track specific metrics for major networks, including specific tracking for Toyama, Japan.

## 📊 Key Insights
*   **Capacity Hubs:** Identification of major relief points like Devauxstraat, which serve as critical return spaces for the system.
*   **High Demand Indicators:** Tracking "Low" status areas where bikes are being rented out faster than they are being returned.
*   **Infrastructure Leaders:** Analysis of major networks, specifically focusing on the large-scale operations in Valence and Bruxelles-Capitale.

## 🛠️ Tools Used
*   **Power BI:** Data visualization and dashboard creation.
*   **Data Source:** Global bike-sharing station data (CSV/API).

## ⚙️ Technical Implementation

### 🧹 Data Cleaning (Power Query)
Before visualization, the raw data underwent the following transformations:
*   **Geocoding:** Standardized city and station names to ensure accurate plotting on the global map.
*   **Data Typing:** Converted capacity and availability counts into whole numbers for calculation.
*   **Status Logic:** Created a conditional column to flag stations as "Low" (high demand) or "High Capacity" (relief points) based on available docks.
*   **Regional Filtering:** Grouped contracts into specific focus areas: Europe, Americas, and Japan (Toyama).

### 📈 DAX Measures
The dashboard relies on several Key Performance Indicators (KPIs) calculated using DAX:
*   **Total Capacity** = `SUM('Bike Stations'[Total Stands])`
*   **Availability %** = `DIVIDE(SUM('Bike Stations'[Available Bikes]), SUM('Bike Stations'[Total Stands]), 0)`
*   **Station Health** = `IF([Available Bikes] < 5, "Low Status", "Stable")`
*   **Rebalance Priority** = A ranking measure that identifies stations with high free stands to prioritize them as return hubs.

## 📈 How to Use
To interact with this Power BI report:
1.  **Download the `.pbix` file** from this repository.
2.  Ensure you have **Power BI Desktop** installed.
3.  Open the file to view the interactive dashboard.
4.  Use the **Slicers** to filter by Region (Europe, Americas, Japan) or specific City.
5.  Hover over the **Map Visuals** to see real-time "Low" status alerts for specific urban hubs.

## 🗂️ Data Dictionary

| Field Name | Description |
| :--- | :--- |
| **Station Name** | Unique identifier for each bike-sharing dock location. |
| **City/Region** | Geographical location of the station (e.g., Brussels, Toyama). |
| **Total Stands** | The total number of docking points available at a station. |
| **Free Stands** | The current number of empty docks available for bike returns. |
| **Available Bikes** | The number of bikes currently docked and ready for rental. |
| **Status** | Categorical value (e.g., "Low", "Normal", "Full") based on bike availability. |
| **Contract Name** | The specific management network for the region. |

## 🚀 Future Enhancements
*   **Predictive Rebalancing:** Integrate machine learning to predict station depletion before it happens.
*   **Weather Integration:** Correlate bike usage with local weather APIs to adjust fleet maintenance.
*   **Real-time API Connection:** Replace static data with a live GBFS (General Bikeshare Feed Specification) feed.
*   **Route Optimization:** Add a layer to calculate efficient routes for trucks moving bikes between stations.

## 🏁 Conclusion
The analysis shows the system is growing fast but remains unbalanced. To improve service, operators should prioritize moving bikes from high-capacity stations to high-demand urban areas where bikes are running out.
