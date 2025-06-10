## **Data Cleaning and Preparation Report: HR Dataset**

---

### **Executive Summary**

This report details the data cleaning and preparation steps performed on the HRDataset\_v14.csv file. The primary goal was to enhance data quality, ensure consistency, and engineer new features to prepare the dataset for in-depth analysis and machine learning modeling. Key actions included standardizing date formats, addressing missing data in critical fields, and creating new, insightful variables such as **employee tenure**, **age**, and a **high-absence flag**. These transformations have resulted in a clean, robust dataset ready for analysis, which will allow us to better understand the employee lifecycle and key performance indicators.

### **Data Quality Issues and Actions Taken**

#### ---

The following outlines the specific data quality issues identified and the corrective actions taken.

**1\. Data Type Correction: Date Fields**

* **Issue:** The dataset contained several date-related columns (DOB, DateofHire, DateofTermination, LastPerformanceReview\_Date) that were initially stored as plain text. This format prevents accurate time-based calculations.  
* **Action Taken:** All date columns were converted to a standardized **datetime** format.  
* **Business Impact:** This change is fundamental for any time-based analysis, enabling us to accurately calculate critical metrics like employee age and tenure.

**2\. Missing Value Imputation**

* **Issue:** Missing data was identified in two key columns: ManagerID and DateofTermination.  
  * **ManagerID:** 8 employees, including the CEO, were missing a ManagerID.  
  * **DateofTermination:** This field was blank for all 207 active employees.  
* **Actions Taken:**  
  * For ManagerID, the missing values were filled with 0\.  
  * For DateofTermination, the missing values for active employees were filled with the current date (June 9, 2025).  
* **Business Impact:** Filling the ManagerID ensures that every employee record is complete for reporting and analysis. Populating the termination date for active employees was a necessary step to enable the accurate calculation of current employee tenure.

### **Feature Engineering**

---

To enrich the dataset for more powerful analysis, several new features were created from the existing data.

**1\. Employee Tenure**

* **Action Taken:** A new feature, **Tenure**, was created to calculate the total length of employment in years for each employee. This was calculated as the difference between their DateofHire and DateofTermination (or the current date for active employees).  
* **Business Impact:** Tenure is a critical variable for understanding employee retention, identifying turnover trends, and analyzing how experience correlates with performance and satisfaction.

**2\. Employee Age**

* **Action Taken:** A new feature, **Age**, was created by calculating the difference between an employee's DOB and the current date.  
* **Business Impact:** Age provides important demographic context and is essential for any analysis related to generational trends, career progression, and succession planning.

**3\. High-Absence Flag**

* **Action Taken:** A binary flag named **High\_Absence\_Flag** was created to easily identify employees with potential attendance issues. An employee is flagged (1) if they have **more than 15 absences** or were **late more than 3 times** in the last 30 days.  
  * Based on this rule, **27 employees** were flagged as having high absences.  
* **Business Impact:** This flag allows us to quickly segment the workforce to identify individuals who may need additional support or management attention, helping to proactively address issues that can affect productivity.

### **Data Transformation for Modeling**

* **Action Taken:** To prepare the data for use in predictive models, a separate, **one-hot encoded** version of the dataset was created. This process converts key categorical text fields (Department, Position, and RaceDesc) into a numerical format that machine learning algorithms can understand.  
* **Business Impact:** This step is crucial for leveraging advanced analytics and machine learning. It allows us to build models that can, for example, predict employee turnover or identify factors driving performance, while ensuring the integrity of our original data for reporting.

