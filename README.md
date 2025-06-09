
# Optimizing Employee Performance & Well-being: A Holistic View

## Project Overview

Welcome to my Optimizing Employee Performance & Well-being project! This repository showcases a comprehensive people analytics initiative aimed at understanding and enhancing the human capital within an organization. By applying principles of Industrial-Organizational (I/O) Psychology and advanced data science techniques, this project delves into the intricate connections between various HR metrics to derive actionable insights and drive strategic decision-making.

## Project Goal

The primary goal of this project is to leverage a real-world HR dataset to uncover the underlying dynamics of employee satisfaction, engagement, absenteeism, and performance. Through robust data analysis and modeling, we aim to:

- **Identify Key Drivers**: Pinpoint which specific factors significantly influence employee well-being and performance outcomes.

- **Segment Employee Archetypes**: Discover distinct groups of employees based on their unique profiles of satisfaction, engagement, and performance, allowing for tailored interventions.

- **Propose Data-Driven Interventions**: Develop concrete, holistic recommendations for HR strategies and policies that can proactively improve individual employee well-being and contribute to overall organizational success.

## Table of Contents

- **Project Overview**

- **Project Goal**

- **Dataset**

- **Technologies Used**

- **Project Phases**

    - **Phase 1**: Data Acquisition & Preparation

    - **Phase 2:** Exploratory Data Analysis (EDA)

    - **Phase 3**: In-depth Analysis & Modeling

    - **Phase 4**: Interpretation, Recommendations & Presentation

- **Key Insights & Preliminary Findings** (Placeholder)

- **How to Run the Project**

- **Expected Outcomes & Business Value**

- **Future Enhancements**

- **Contributing**

- **License**

- **Contact**

## Dataset

The core of this project utilizes the `HRDataset_v14.csv` file, a rich dataset containing various human resources attributes. The selection of relevant columns is crucial for exploring employee well-being and performance:

 - `EmpID`: Unique identifier for each employee.
 - `Employee_Name`: Employee's full name.
 - `Department`: The department an employee belongs to, crucial for analyzing departmental differences.
 - `Position`: Employee's job role, enabling role-specific insights.
 - `Salary`: Employee's annual compensation, a potential factor in satisfaction and performance.
 - `DOB`: Date of Birth, used for calculating employee age.
 - `DateofHire`: Date of hiring, essential for determining tenure.
 - `DateofTermination`: Date of termination (if applicable), used for calculating employment duration and identifying turnover patterns.
 - `Termd`: A binary flag (1 = terminated, 0 = active), indicating employment status.
 - `TermReason`: The reason for an employee's termination.
 - `EmploymentStatus`: Current employment status (e.g., Active, Voluntarily Terminated).
 - `ManagerName`: The name of the employee's direct manager, vital for managerial impact analysis.
 - `PerformanceScore`: Employee's performance rating (e.g., Exceeds, Fully Meets, Needs Improvement, PIP).
 - `EngagementSurvey`: Score from an employee engagement survey, indicating connection to the organization.
 - `EmpSatisfaction`: Employee satisfaction rating, reflecting overall job contentment.
 - `SpecialProjectsCount`: Number of special projects an employee has undertaken, potentially linked to performance or development.
 - `LastPerformanceReview_Date`: Date of the most recent performance review.
 - `DaysLateLast30`: Number of times an employee was late in the last 30 days, an indicator of attendance.
 - `Absences`: Total number of absences, another key attendance metric.
 - `RaceDesc, GenderID/Sex, MaritalDesc/MaritalStatusID`: Demographic information used for diversity and inclusion analysis, and understanding subgroup differences.
 - `RecruitmentSource`: The channel through which the employee was recruited, useful for evaluating source effectiveness.

## Technologies Used

This project is built using the following open-source tools and libraries:

  - **Python 3.x**: The primary programming language.
  - **Pandas**: v1.x or higher, for robust data loading, cleaning, and manipulation.
  - **NumPy**: v1.x or higher, for efficient numerical operations.
  - **Matplotlib**: v3.x or higher, for static data visualization.
  - **Seaborn**: v0.11.x or higher, for creating aesthetically pleasing statistical graphics.
  - **Scikit-learn**: v0.24.x or higher, for machine learning tasks, including clustering (K-Means) and potentially predictive modeling.
  - **SciPy**: For advanced statistical tests (e.g., ANOVA, t-tests).
  - **Jupyter Notebooks / Google Colab**: For interactive development, analysis, and presenting the findings.

## Project Phases

This project follows a structured methodology, progressing through distinct phases to ensure a comprehensive and rigorous analysis.

### Phase 1: Data Acquisition & Preparation
This foundational phase focuses on gathering and transforming raw data into a clean, usable format suitable for analysis.

  - **Data Loading**:
       - Load the `HRDataset_v14.csv` file into a pandas DataFrame.
  - **Initial Data Inspection**:
       - Examine the first 5 rows `(df.head())` to quickly grasp the data structure.
       - Inspect column names, data types, and identify non-null counts using `df.info()` and `df.dtypes`.
       - Confirm the overall dimensions of the dataset (number of rows and columns).
   - **Data Cleaning & Preprocessing**:
       - Handle Missing Values: Systematically identify columns containing NaN (Not a Number) values, specifically `DateofTermination` and `ManagerID`. Implement appropriate strategies: for `DateofTermination`, consider filling active employees' records with a placeholder or the current date; for `ManagerID`, assess if imputation is feasible.
       - Data Type Conversion: Convert relevant date columns (`DOB`, `DateofHire`, `DateofTermination`, `LastPerformanceReview_Date`) into datetime objects.
   - **Feature Engineering**:
       - `Tenure`: Calculate the length of an employee's service.
       - `Age`: Compute the employee's age from DOB.
       - High-Absence Flag: Create a new binary categorical variable (e.g., `is_high_absent`) for employees whose Absences or `DaysLateLast30` exceed a defined threshold.
       - Performance Score Numerical Mapping: Transform the categorical `PerformanceScore` into a numerical scale (e.g., 4, 3, 2, 1).
   - **Categorical Variable Encoding**:
       - Prepare nominal categorical variables (e.g., `Department`, `Position`, `RaceDesc`) for machine learning models using One-Hot Encoding.

### Phase 2: Exploratory Data Analysis (EDA)
This phase involves a deep dive into the dataset's characteristics, using visualizations and summary statistics to uncover initial patterns.

   - **Descriptive Statistics**:
       - Generate summary statistics (`.describe()`) for all numerical columns.
       - Obtain frequency counts (`.value_counts()`) for all categorical variables.
   - **Distribution Analysis**:
       - Visualize the distributions of key numerical variables (`Salary`, `EmpSatisfaction`, `EngagementSurvey`, `Absences`) using Histograms, Box Plots, and Density Plots.
   - **Relationship Exploration**:
       - **Bivariate Analysis**:
            - Numerical vs. Numerical: Create scatter plots (e.g., EngagementSurvey vs. EmpSatisfaction) and calculate correlation coefficients.
            - Categorical vs. Numerical: Utilize Box Plots or Violin Plots (e.g., EmpSatisfaction by Department).
       - **Multivariate Analysis**: Generate a correlation heatmap of all numerical features.
   - **Identify Initial Insights**:
       - Document any strong correlations, unexpected distributions, or nascent trends observed.

### Phase 3: In-depth Analysis & Modeling

This phase applies more advanced statistical and machine learning techniques to validate hypotheses and build models.

   - **Correlation and Impact Analysis**:
       - Perform rigorous statistical hypothesis tests like ANOVA (e.g., is there a significant difference in `EmpSatisfaction` across Departments?) and T-tests.
   - **Employee Segmentation (Clustering**):
       - Feature Selection: Select and scale numerical features representing well-being and performance (`EmpSatisfaction`, `EngagementSurvey`, `Absences`, numerical `PerformanceScore`).
       - Apply Clustering Algorithm: Implement K-Means Clustering to group employees.
       - Determine Optimal Clusters: Employ the Elbow Method and Silhouette Score to find the optimal number of clusters (K).
       - Characterize Clusters: Analyze and assign meaningful labels to each cluster archetype (e.g., "Highly Engaged High Performers," "Disengaged with High Absences").
   - **Managerial Impact Analysis**:
       - Aggregate metrics like `PerformanceScore` and `EngagementSurvey` at the `ManagerName` level.
       - Conduct statistical comparisons (e.g., ANOVA) to identify managers whose teams exhibit significantly different outcomes.
   - Predictive Modeling for Performance:
       - Objective: Develop a model to predict PerformanceScore.
       - Model Selection: Choose an appropriate classification model (e.g., Logistic Regression, Random Forest Classifier).
       - Model Training & Evaluation: Split the data, train the model, and evaluate its performance using metrics like Accuracy, Precision, Recall, F1-score, and a Confusion Matrix.

### Phase 4: Interpretation, Recommendations & Presentation

This phase focuses on translating analytical findings into clear, actionable insights.

   - **Synthesize Findings**:
       - Consolidate all key insights from EDA, correlation analysis, and clustering.
       - Clearly articulate the most significant factors influencing employee well-being and performance.
   - **Develop Actionable Recommendations (Prescriptive)**:
       - Targeted Interventions: For each employee archetype, propose specific interventions (e.g., for "Burned Out High Achievers," suggest stress management workshops).
       - Manager Development Programs: Recommend leadership development for managers based on impact analysis.
       - Policy & Strategy Adjustments: Suggest broader changes to HR policies or compensation structures.
   - **Quantify Potential Impact (if possible)**:
       - Estimate the potential benefits and ROI of implementing recommendations (e.g., "A 10% increase in engagement could lead to a 5% reduction in absenteeism.").
   - **Create a Compelling Presentation**:
       - Executive Summary: A concise summary of the project's purpose, findings, and recommendations.
       - Visualizations: Clear, professional charts and graphs.
       - Narrative: A compelling story connecting the analysis to business value.
       - Technical Details (Appendix): Include methodology, algorithms, and code snippets for transparency.


## Key Insights & Preliminary Findings (Placeholder)

(This section will be populated with a summary of the project's most significant findings after the analysis is complete. Examples might include:)

   - Correlation between employee engagement and a reduction in absenteeism.
   - Identification of 3-4 distinct employee segments with unique well-being and performance profiles.
   - Identification of top-performing managers based on team engagement and satisfaction scores.
   - Factors most predictive of higher performance scores.

## Expected Outcomes & Business Value

This project is designed to deliver tangible value by providing:

   - A deeper, evidence-based understanding of the factors influencing employee performance and engagement.
   - Identified segments of employees, enabling more personalized HR interventions.
   - Actionable insights into the impact of managerial effectiveness on team outcomes.
   - Concrete, data-driven recommendations for targeted HR interventions and policy adjustments.
   - Quantifiable estimates of the potential business value (e.g., improved productivity, reduced absenteeism, enhanced retention).

## Future Enhancements

We envision several potential enhancements to expand this project:

   - Integration with External Data: Incorporate external economic indicators or industry benchmarks.
   - Interactive Dashboard Development: Create a dynamic dashboard using tools like Tableau, Power BI, or Dash.
   - A/B Testing Framework: Design a framework to scientifically measure the impact of proposed HR interventions.
   - Advanced Text Analytics (NLP): Apply NLP to qualitative data from survey responses or exit interviews.
   - Time-Series Analysis for Performance: Model performance trends over time to predict future shifts.
   - Prescriptive Model Development: Develop models that not only predict outcomes but also recommend optimal actions.

## Contributing

**This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

    Cristian Cevallos, East Carolina University
    Email: cevallosc23@students.ecu.edu
    LinkedIn: https://www.linkedin.com/in/cristian-g-cevallos/

**Feel free to connect or ask any questions!**



Thanks for checking out my learning journey! 🚀
