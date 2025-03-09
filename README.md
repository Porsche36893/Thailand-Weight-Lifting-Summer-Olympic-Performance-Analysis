# Weightlifting Data Analysis: Summer Olympics 2012-2024

This project focuses on extracting and analyzing weightlifting data for four specific events in the Summer Olympics from 2012 to 2024. The goal is to track and compare Thailand’s performance in the following categories:

- **Women 49kg**
- **Women +81kg**
- **Men 61kg**
- **Men 73kg**

The following steps outline the data collection and transformation process to prepare the dataset for analysis.

## Data Collection Process

1. **Obtain Weightlifting Data (2012-2024)**  
   - Visit the official Summer Olympics website for each Olympic year (2012 to 2024).
   - Copy and paste the weightlifting data for the four events into an Excel file.

2. **Collect Comparative Data (2012-2024)**  
   - Navigate to the Wikipedia page for each Summer Olympics year.
   - Click on the arrow icon to select the previous Olympics year to obtain comparative data.
   - Repeat the process for every Olympic year from 2012 to 2024 to gather the complete dataset.

## Data Cleaning & Transformation

### 1. **Remove Unnecessary Columns**
   - **For 2012 to 2020:** Remove the following columns:
     - Group (A)
     - Bodyweight (numeric values with floating points)

### 2. **Manually Extract Country Information (2012 Only)**
   - **For 2012:** 
     - Manually extract the country name from the flag image and the country’s three-letter abbreviation next to the player’s name.
     - Remove the flag image from all cells.

### 3. **Modify Rank Column**
   - Replace images for the medals (Gold, Silver, and Bronze) in the **Rank** column with numeric values:
     - Gold medal = 1
     - Silver medal = 2
     - Bronze medal = 3

### 4. **Keep Only Relevant Columns (2012-2024)**
   - Remove all Snatch (kg) and Clean & Jerk (kg) sub-columns except for the **Result** sub-column, which records the best weight lifted by each athlete.
   - If the string "OR" (Olympic Record) appears in any of the cells, remove it.

### 5. **Remove Hyperlinks**
   - Remove all hyperlinks from the dataset to clean the data.

### 6. **Clean Country Name Format (2016-2024)**
   - **For 2016-2024:** The country names include special characters displayed as a space. Use the following formula to clean the country names:
     ```excel
     =TRIM(SUBSTITUTE(A1, CHAR(160), ""))
     ```

### 7. **Clean Player Name Format (2012 Only)**
   - **For 2012:** Players' names include the country's three-letter abbreviation (e.g., "Zhou Lulu (CHN)"). Use the following formula to extract the player's name:
     ```excel
     =TRIM(SUBSTITUTE(LEFT(A1, LEN(A1)-6), CHAR(160), ""))
     ```

### 8. **Create Medal Column**
   - Add a new **Medal** column, where the values are:
     - **Gold** if Rank = 1
     - **Silver** if Rank = 2
     - **Bronze** if Rank = 3
     - **Participant** for all other players
   - Use the following formula to generate the medal classification:
     ```excel
     =IF(B2=1,"Gold",IF(B2=2,"Silver",IF(B2=3,"Bronze","Participant")))
     ```

## Final Dataset Structure

After completing the data cleaning and transformation steps, the final dataset will include the following columns:

- **Name**: The player's name (cleaned)
- **Country**: The country name (cleaned)
- **Rank**: Numeric value representing the athlete's rank (1 = Gold, 2 = Silver, 3 = Bronze)
- **Result**: The best weight lifted (in kg)
- **Medal**: The medal type (Gold, Silver, Bronze, or Participant)

---

## Tools and Technologies Used

- **Excel**: For data cleaning, transformation, and manipulation
- **R**: For plotting the result and analysis


---

## Conclusion

This dataset will provide valuable insights into Thailand’s performance in weightlifting events over the past four Olympic years, showcasing the evolution of athletes' performances and helping identify trends, strengths, and areas for improvement.

---

Feel free to explore, analyze, and visualize the data to derive further insights. Enjoy the process!

--- 

This version is formatted with headings, bullet points, and code blocks to make it easier for users to follow the project steps and understand the methodology.
