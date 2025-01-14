# EdTech Analysis Power BI Dashboard

### Overview
This project is a comprehensive Power BI dashboard created using the **Online Courses dataset**. The dashboard covers various analysis aspects, allowing users to interact with different features of Power BI, such as visualizations, filters, and drilldowns. Additionally, it demonstrates several key **DAX functions** to showcase advanced analytical calculations in Power BI.

The primary goal of this dashboard is to help users explore Power BI's functionality by providing an interactive and intuitive experience. Users can download the `.pbix` file and get hands-on experience with Power BI and DAX queries.

---

### Features

- **Course Type Distribution**: Analyze course types across categories and sub-categories.
- **Viewer Engagement**: Calculate average views by category, sub-category, and language.
- **Skills Analysis**: Identify key skills taught within each category.
- **Language Distribution**: Examine course language preferences.
- **Top Categories by Preference**: Investigate language preferences for top 5 categories.
- **Subtitles Impact**: Analyze how subtitles affect course viewership.
- **Instructor Performance**: Identify top instructors by ratings for each category.
- **Course Duration vs. Views**: Explore the relationship between course length and viewership.
- **Skill Variety Impact**: Assess how skill variety influences viewership.
- **Visualizations**: Includes bar charts, pie charts, line charts etc.

---

### Dashboard Pages

1. **Course Type Popularity**  
   This chart shows the distribution of course types across categories and sub-categories, along with the count of courses. It helps identify trends and align course launches with learner demand.  
   ![Course Type Popularity](https://github.com/user-attachments/assets/0d55e126-8776-4c66-8355-60ad9d8f4882)

2. **Course per Language and Sub-category**  
   This chart calculates the average number of views for each category, sub-category, and language, providing insights into viewer engagement patterns and guiding content development strategies.  
   ![Course per Language and Sub-category](https://github.com/user-attachments/assets/b8feb8de-4829-4d5f-8fa4-7ee79a9df24a)

3. **Demanding Skills**  
   This word cloud displays the most commonly taught skills across categories, helping ensure course offerings are aligned with current job market demands.  
   ![Demanding Skills](https://github.com/user-attachments/assets/05bcd82d-0035-4af1-ae6e-305ed5e40b37)

4. **Most Prominent Language**  
   This pie chart visualizes the distribution of languages in which courses are offered, helping to understand language preferences and optimize course accessibility.  
   ![Most Prominent Language](https://github.com/user-attachments/assets/ad7ff48a-0c22-43f0-9c64-d99099083253)

5. **Top Categories by Average Views**  
   This table ranks the top 5 categories based on their average views, providing insights into the most engaging categories for strategic decision-making.  
   ![image](https://github.com/user-attachments/assets/c518a41e-8078-4274-8ae3-5acc165005f8)

6. **Number of Viewers as per Subtitle Count**  
   This chart shows the relationship between the number of subtitles and course views. It highlights how increasing subtitle availability is correlated with higher viewer engagement.  
   ![Number of Viewers as per Subtitle Count](https://github.com/user-attachments/assets/7d3590d4-bcff-4548-9b38-78a8a847ecbc)

7. **Top Instructors by Ratings**  
   The bar graph highlights the top-rated instructors, showcasing educators who consistently deliver high-quality content and effectively engage learners.  
   ![image](https://github.com/user-attachments/assets/2c6af1b4-b7fc-44fa-b51d-8a55992cd210)

8. **Course Duration vs. Viewer Engagement**  
   This visualization examines the relationship between course duration and the number of views, providing insights into how course length influences viewer preferences and engagement across categories and subcategories.  
   ![Course Duration vs. Viewer Engagement](https://github.com/user-attachments/assets/2c408851-b857-4098-a34a-024a7c21b304)

9. **Skill Variety and Duration Analysis**  
   This table presents the average number of skills offered and the average course duration (in hours) for each category, helping to analyze their impact on viewership and engagement.  
   ![Skill Variety and Duration Analysis](https://github.com/user-attachments/assets/4e3792d8-9913-470d-be17-73fad2073146)

---

### DAX Functions

This dashboard incorporates several important DAX functions to perform complex calculations. Some examples of the DAX queries used in this project are listed below:

**Average Views per Category**  
Calculates the average number of views for each category, aiding in viewer engagement analysis.
```dax
DEFINE
MEASURE Courses[Average Views per Category] = 
AVERAGEX(Courses, DIVIDE(Courses[Total Views], Courses[Count of Courses], 0))
```

**Top 5 Categories by Average Views**
Ranks categories based on their average views to highlight popular content areas.

```dax
DEFINE
MEASURE Courses[Category Rank by Avg Views] = 
RANKX(ALL(Courses[Category]), [Average Views per Category], , DESC)
```

**Subtitle Impact on Views**
Calculates the total number of views for courses with subtitles to assess accessibility impact.

```dax
DEFINE
MEASURE Courses[Views with Subtitles] = 
CALCULATE(SUM(Courses[Total Views]), Courses[Has Subtitles] = TRUE())
```   

**Top Instructors by Rating**
Ranks instructors based on their average ratings to identify top performers.

```dax
DEFINE
MEASURE Courses[Instructor Rank by Rating] = 
RANKX(ALL(Courses[Instructor]), [Instructor Average Rating], , DESC)
```   

**Category Duration Impact on Views**
Calculates the views per hour of content to examine the relationship between course duration and engagement.

```dax
DEFINE
MEASURE Courses[Views per Hour of Content] = 
DIVIDE(SUM(Courses[Total Views]), SUM(Courses[Duration in Hours]), 0)
```   

**Skill Variety Impact on Views**
Measures the impact of skill variety on viewership by calculating views per number of skills offered.

```dax
DEFINE
MEASURE Courses[Views per Skill Variety] = 
DIVIDE(SUM(Courses[Total Views]), SUM(Courses[Number of Skills Offered]),
```   

**Month-Specific Duration Calculation**
Computes the total course duration for the current month to support scheduling flexibility.

```dax
DEFINE
MEASURE Courses[Monthly Duration] = 
CALCULATE(SUM(Courses[Duration in Hours]), DATESINPERIOD('Calendar'[Date], TODAY(), -1, MONTH))
```  

**Language Preferences by Category**
Ranks languages based on their average views within categories to identify audience preferences.

```dax
DEFINE
MEASURE Courses[Language Preferences Rank] = 
RANKX(ALL(Courses[Language]), [Average Views per Language], , DESC)
```

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


