# Superstore Power BI Dashboard

### Overview
This project is a comprehensive Power BI dashboard created using the **Superstore dataset**. The dashboard covers various analysis aspects, allowing users to interact with different features of Power BI, such as visualizations, filters, and drilldowns. Additionally, it demonstrates several key **DAX functions** to showcase advanced analytical calculations in Power BI.

The primary goal of this dashboard is to help users explore Power BI's functionality by providing an interactive and intuitive experience. Users can download the `.pbix` file and get hands-on experience with Power BI and DAX queries.

---

### Features
- **Sales Analysis**: Explore sales trends by categories, sub-categories, and regions.
- **Profit Analysis**: Understand profit margins and how different regions or products contribute to profitability.
- **Salesperson Performance**: Dive into individual salesperson performance across various metrics.
- **Shipping Modes**: Analyze the performance and costs associated with different shipping methods.
- **Visualizations**: The dashboard includes diverse visuals like **tree maps**, **waterfall charts**, and more.

---

### Dashboard Pages

1. **Salesperson Dashboard**
   - Provides insights into individual salesperson performance.
   - <img width="671" alt="Capture1" src="https://github.com/user-attachments/assets/63340bf1-d444-4ba3-aefb-468c7b7863c6">


2. **Profit Analysis**
   - Offers detailed analysis of profits by category, sub-category, and region.
   - <img width="670" alt="Capture2" src="https://github.com/user-attachments/assets/8d1e614d-7843-4a80-9706-a1bf6deabf66">


3. **Shipping Mode Analysis**
   - Visualizes the cost and efficiency of different shipping methods.
   - <img width="669" alt="Capture3" src="https://github.com/user-attachments/assets/3d03fda5-eec1-4da5-ba9f-1ad7dd23cfbc">


4. **Salesperson Performance**
   - Deep dive into individual sales performance with ranking and comparisons.
   - <img width="670" alt="Capture7" src="https://github.com/user-attachments/assets/57abdf5d-aaa1-4e5a-b713-1e6227d7decb">


5. **Tree Chart**
   - A hierarchical view of categories and sub-categories showing sales and profit contributions.
   - <img width="669" alt="Capture4" src="https://github.com/user-attachments/assets/44ce761e-7162-4fa6-97c9-a827b40e9108">



6. **Waterfall Chart**
   - Displays cumulative sales performance over time with profit/loss breakdown.
   - <img width="669" alt="Capture5" src="https://github.com/user-attachments/assets/b291965b-6763-46c0-b595-ab8882b5b159">

7. **Relationship Diagram**
   - <img width="626" alt="Capture6" src="https://github.com/user-attachments/assets/34bea3be-8bf6-4638-89d1-70a089d411e2">



---

### DAX Functions

This dashboard incorporates several important DAX functions to perform complex calculations. Some examples of the DAX queries used in this project are listed below:

1. **Average Profit per Quantity**:
    ```dax
    DEFINE
    MEASURE Orders[Average profit per Quantity] = 
    AVERAGEx(Orders, DIVIDE(Orders[Profit], Orders[Quantity], 0))
    ```

2. **Profit Ranking**:
    ```dax
    DEFINE
    MEASURE Orders[Sum of Profits] = SUM(Orders[Profit])
    MEASURE Orders[Profit Based Ranking] = RANKX(ALL(Orders[Sub-Category]), [Sum of Profits])
    ```

3. **Sales in 2016 Q2**:
    ```dax
    DEFINE
    MEASURE Orders[Sales in 2016 Q2] = CALCULATE(sum(Orders[Sales]), DATESBETWEEN('Calendar'[Date], DATE(2016, 4, 1), DATE(2016, 8, 30)))
    ```

4. **Sales Till Date**:
    ```dax
    DEFINE
    MEASURE Orders[Sales till date] = CALCULATE(sum(Orders[Sales]), DATESBETWEEN('Calendar'[Date], TODAY()-365, TODAY()))
    ```

5. **Month-to-Date (MTD) Sales**:
    ```dax
    DEFINE
    MEASURE Orders[MTD Sales] = TOTALMTD(SUM(Orders[Sales]), DATESMTD('Calendar'[Date]))
    ```

6. **Year-to-Date (YTD) Sales**:
    ```dax
    DEFINE
    MEASURE Orders[YTD Sales] = TOTALYTD(SUM(Orders[Sales]), DATESYTD('Calendar'[Date]))
    ```

7. **Same Period Last Year Sales**:
    ```dax
    DEFINE
    MEASURE Orders[same period last year sales] = 
    CALCULATE(
        SUM(Orders[Sales]), 
        SAMEPERIODLASTYEAR('Calendar'[Date])
    )
    ```

8. **Same Period Last Month Sales**:
    ```dax
    DEFINE
    MEASURE Orders[same period last month sales] = CALCULATE(sum(Orders[Sales]), PARALLELPERIOD('Calendar'[Date], -1, MONTH))
    ```

---

### How to Use

1. **Download the Power BI file**: 
   - You can download the Power BI file (`.pbix`) from this repository.
   - https://github.com/Ganesh-VG/PowerBI_Sample_Dashboard_1/raw/main/Power%20BI%20sample1.pbix

2. **Open with Power BI Desktop**:
   - Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) if you haven't already.
   - Open the downloaded `.pbix` file in Power BI Desktop.

3. **Explore the Dashboard**:
   - Navigate through different pages to explore sales, profit analysis, and various Power BI features.
   - Interact with slicers, filters, and visual elements to get a better understanding of how Power BI dashboards work.

4. **Play with DAX Functions**:
   - Open the **Data** and **Modeling** views to explore the DAX functions used in this dashboard.
   - Feel free to modify and experiment with the DAX queries to learn more about how they work.

---

### Requirements

- Power BI Desktop (latest version)
- Basic understanding of Power BI (navigation, visuals, etc.)

