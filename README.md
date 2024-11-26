# Data Wrangling and Munging with SQL

## Project Description

This project demonstrates various SQL techniques for data wrangling and data munging, including reformatting, string manipulation, filtering, and numeric adjustments. These operations are essential for preparing raw data for analysis and ensuring its consistency, accuracy, and usability in downstream processes.

---

## Key Operations and Examples

### **1. Data Standardization**
- **Reformatting Character Data:**
  - Convert department names to uppercase:
    ```sql
    SELECT DISTINCT(UPPER(department))
    FROM staff
    ORDER BY 1;
    ```
  - Convert department names to lowercase:
    ```sql
    SELECT DISTINCT(LOWER(department))
    FROM staff
    ORDER BY 1;
    ```

- **Trimming Strings:**
  - Remove leading and trailing spaces:
    ```sql
    SELECT TRIM('    data science rocks !    ');
    ```

- **Concatenation:**
  - Combine job titles and departments into a single string:
    ```sql
    SELECT 
        last_name,
        job_title || ' - ' || department AS title_with_department
    FROM staff;
    ```

---

### **2. String Extraction and Replacement**
- **Extract Substrings:**
  - Extract specific parts of a string using `SUBSTRING`:
    ```sql
    SELECT 
        SUBSTRING('abcdefghikl' FROM 5 FOR 3) AS sub_string;
    ```

- **Filter Roles with Specific Patterns:**
  - List job titles starting with "Assistant":
    ```sql
    SELECT job_title
    FROM staff
    WHERE job_title LIKE 'Assistant%';
    ```

- **Replace Words:**
  - Replace "Assistant" with "Asst." in job titles:
    ```sql
    SELECT
        OVERLAY(job_title PLACING 'Asst.' FROM 1 FOR LENGTH('Assistant')) AS shorten_job_title
    FROM staff
    WHERE job_title LIKE 'Assistant%';
    ```

---

### **3. Advanced Filtering with Regular Expressions**
- **Find Specific Patterns:**
  - Filter job titles with "Assistant" and levels "III" or "IV":
    ```sql
    SELECT job_title
    FROM staff
    WHERE job_title SIMILAR TO '%Assistant%(III|IV)';
    ```

- **Complex Conditions:**
  - Find job titles starting with "E", "P", or "S":
    ```sql
    SELECT job_title
    FROM staff
    WHERE job_title SIMILAR TO '[EPS]%';
    ```

---

### **4. Numeric Formatting**
- **Rounding and Truncation:**
  - Perform numeric adjustments on average salaries:
    ```sql
    SELECT 
        department, 
        AVG(salary) AS avg_salary, 
        TRUNC(AVG(salary)) AS truncated_salary,
        ROUND(AVG(salary), 2) AS rounded_salary,
        CEIL(AVG(salary)) AS ceiling_salary,
        FLOOR(AVG(salary)) AS floor_salary
    FROM staff
    GROUP BY department;
    ```

---

## Tools and Environment
- **Database Management Systems:** MySQL, PostgreSQL
- **Setup Requirements:**
  - Load the `staff` dataset into your database.
  - Execute the SQL queries sequentially to explore and transform the data.

---

## Learning Outcomes
- Apply SQL for data preparation tasks, such as trimming, reformatting, and extracting strings.
- Leverage advanced techniques like regular expressions for filtering complex patterns.
- Use numeric functions like `TRUNC`, `ROUND`, `CEIL`, and `FLOOR` for precise calculations.

---

## Use Cases
- **Data Cleaning:** Prepare raw data for analysis by ensuring consistency in character and numeric fields.
- **Feature Engineering:** Extract meaningful information from raw strings, such as job categories or levels.
- **Data Validation:** Identify patterns and anomalies in datasets using regular expressions and advanced filters.

---

## Acknowledgments
This repository is designed to showcase essential SQL operations for data wrangling and munging in practical scenarios.
