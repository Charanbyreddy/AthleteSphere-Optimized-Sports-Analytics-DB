# AthleteSphere-Optimized-Sports-Analytics-DB
AthleteSphere is an advanced sports data platform that streamlines performance tracking and predictive analytics using optimized indexing and relational database design. It enhances data integrity and retrieval speed, empowering coaches, analysts, and researchers with actionable insights for strategic sports management

---

## 📚 **About the Data**

- **Source**: The dataset is sourced from [Kaggle - Olympics Legacy 1896-2020](https://www.kaggle.com/datasets/krishd123/olympics-legacy-1896-2020).
  
- **Description**: This dataset covers over a century of Olympic events from 1896 to 2020, containing detailed records on athletes, events, teams, venues, and medals. It provides a rich source for **data exploration**, **statistical analysis**, and **predictive modeling**.

---

## 🔍 **Data Analysis and Insights**

### **1. Exploratory Data Analysis (EDA)**

- **Demographic Analysis**: Explored athlete demographics (age, gender distribution) across different Olympic seasons.
- **Performance Trends**: Identified trends in medal distributions across countries, sports, and time.
- **Event Popularity**: Analyzed which sports have grown in popularity over time based on participation rates.

### **2. Predictive Modeling**

Applied **machine learning** techniques to predict medal outcomes based on athlete and event characteristics.

- **Modeling Techniques Used**:
  - **Logistic Regression**: To predict the likelihood of an athlete winning a medal.
  - **Random Forest Classifier**: To classify medal types (Gold, Silver, Bronze) based on event and athlete data.
  - **Clustering (K-Means)**: Grouped athletes by performance metrics to identify hidden patterns.

- **Feature Engineering**:
  - Created new features such as **age groups**, **season-based participation rates**, and **historical performance metrics**.

### **3. Data Visualization**

Utilized **Matplotlib**, **Seaborn**, and **Plotly** for dynamic, interactive visualizations:

- **Medal Distribution Heatmaps**: Visualizing country-wise performance over time.
- **Trend Lines**: Showing growth in athlete participation by gender across Olympic years.
- **Correlation Matrices**: Identifying relationships between age, gender, and medal wins.

---

## 🗂️ **Database Tables and Schema**

*The project uses a normalized relational database structure to ensure data integrity and efficient querying.*

### **1. Athletes Table**
Stores individual athlete information.

| Column Name | Data Type | Description                           |
|-------------|------------|---------------------------------------|
| `AthleteID` | INT        | Unique identifier for each athlete    |
| `Name`      | CHAR(255)  | Athlete's full name                  |
| `Gender`    | CHAR(10)   | Gender of the athlete (`Male`, `Female`, `Other`) |
| `Age`       | INT        | Age of the athlete (must be > 0)     |

---

### **2. Teams Table**
Holds team-related data and links them to their countries.

| Column Name | Data Type   | Description                           |
|-------------|--------------|---------------------------------------|
| `TeamID`    | INT          | Unique identifier for each team       |
| `TeamName`  | VARCHAR(255) | Name of the team                     |
| `NOC`       | CHAR(3)      | National Olympic Committee code      |

---

### **3. Sports Table**
Contains information on various sports categories.

| Column Name | Data Type   | Description                           |
|-------------|--------------|---------------------------------------|
| `SportID`   | INT          | Unique identifier for each sport      |
| `SportName` | VARCHAR(255) | Name of the sport (e.g., Swimming)    |

---

### **4. Venues Table**
Stores venue details where events are conducted.

| Column Name | Data Type   | Description                           |
|-------------|--------------|---------------------------------------|
| `VenueID`   | INT          | Unique identifier for each venue      |
| `City`      | CHAR(100)    | City where the venue is located       |
| `Country`   | CHAR(100)    | Country of the venue                 |

---

### **5. Events Table**
Details of individual Olympic events.

| Column Name | Data Type   | Description                                     |
|-------------|--------------|-------------------------------------------------|
| `EventID`   | INT          | Unique identifier for each event               |
| `SportID`   | INT          | Foreign key linking to **Sports(SportID)**     |
| `VenueID`   | INT          | Foreign key linking to **Venues(VenueID)**     |
| `EventName` | VARCHAR(255) | Name of the event (e.g., 100m Sprint)          |
| `Year`      | INT          | Year the event took place                      |
| `Season`    | CHAR(10)     | `Summer` or `Winter`                           |

---

### **6. Medals Table**
Defines types of medals awarded.

| Column Name | Data Type   | Description                           |
|-------------|--------------|---------------------------------------|
| `MedalID`   | INT          | Unique identifier for each medal type |
| `MedalType` | CHAR(10)     | Type of medal (`Gold`, `Silver`, `Bronze`, `None`) |

---

### **7. AthleteEvents Table**
Tracks athlete participation and medals in events.

| Column Name | Data Type | Description                                           |
|-------------|------------|-------------------------------------------------------|
| `AthleteID` | INT        | Foreign key linking to **Athletes(AthleteID)**        |
| `EventID`   | INT        | Foreign key linking to **Events(EventID)**            |
| `MedalID`   | INT        | Foreign key linking to **Medals(MedalID)**            |

**Composite Primary Key**: (`AthleteID`, `EventID`, `MedalID`)

---

### **8. TeamEvents Table**
Manages team participation and medal achievements.

| Column Name | Data Type | Description                                           |
|-------------|------------|-------------------------------------------------------|
| `TeamID`    | INT        | Foreign key linking to **Teams(TeamID)**              |
| `EventID`   | INT        | Foreign key linking to **Events(EventID)**            |
| `MedalID`   | INT        | Foreign key linking to **Medals(MedalID)**            |

**Composite Primary Key**: (`TeamID`, `EventID`)

---

## 🚀 **How to Use This Repository**

### 1. **Clone the Repository**
```bash
git clone https://github.com/YourUsername/AthleteSphere-Sports-Data-Management.git
cd AthleteSphere-Sports-Data-Management

