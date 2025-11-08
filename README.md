<div class="project-card" markdown="1">

## Project 1

**Title:** Charity Insight Hub  

**Tools Used:** Power BI Desktop, DAX, Power Query, Data Modeling, Text File/Data Cleaning & Transformation  

**Project Description:**  
The Charity Insight Hub is an interactive Power BI dashboard designed to analyze charity performance data across England and Wales. It integrates multiple datasets, including charity registrations, financial statements, classifications, trustees, and geographic data, to deliver a single source of truth for monitoring financial health, governance, and sector trends. The project demonstrates advanced Power BI capabilities such as data modeling between seven relational tables, DAX calculations for KPIs, custom visuals for income/expenditure analysis, and decomposition trees for root-cause exploration. It also simulates real-world reporting tasks aligned with a Data Analyst role within an NGO (charity organisation), focusing on income insights, donor segmentation, and transparency in operations.

**Key findings:**

- Over 394K charities were analyzed, with 185K currently registered and 209K removed.  
- Total reported charity income exceeded £100 billion, with £95 billion in expenditure.  
- The “Throughout England and Wales” region contributed the largest share of total income (~35%).  
- Top-performing charities such as Lloyd’s Register Foundation and The British Council generated incomes exceeding £1 billion each.  
- Several charities reported consistent net surpluses, indicating strong financial management and sustainability.  
- The most common charity purposes were Education/Training (35%) and General Charitable Purposes (33%).

**Dashboard Overview:**

- Top 10 Charities by Income & Expenditure  
- Top Region by Income Contribution (Decomposition Tree)  
- Top 10 Charities by Net Surplus  
- Age of Charities  
- Classification Analysis (Donut Chart)  
- KPI Cards for registered vs removed charities, trustees, and income/expenditure  
- Interactive Filters for charity name, status, geography, and financial year  

![Charity_Insight_Hub2](/Charity_Insight_Hub2.jpg)

</div>


<div class="project-card" markdown="1">
  
## Project 2

**Title:** 2018 – 2025 NHS Hospital Episode Statistics in England  

**Tools Used:** Power BI Desktop, DAX, Power Query, Data Modeling, Excel/CSV Data Cleaning & Transformation  

**Project Description:**  
The NHS Hospital Episode Statistics (HES) is an interactive Power BI report built to analyze hospital activity across 2018–2025. It combines multiple HES tables (age groups, treatment specialty, provider and region). The first dashboard page focuses on age-based insights for episodes, appointments and non-attendance.

In Power Query, extensive cleaning was performed, including:

- Splitting and cleaning the `Age_Band` field (e.g. `01. 0 - 4` → code `1`, label `0 - 4`) and creating a numeric `AgeBand_Code` used to sort age bands correctly.  
- Converting `Date` to a true date datatype and deriving a `Year` column (while deliberately not using a separate Date dimension).  
- Removing redundant columns, non-numeric characters and duplicate records where Age_Band/Date combinations were repeated.  
- Ensuring all activity fields (`FCE`, `FAE`, appointments, DNA, emergency, etc.) were typed as whole numbers.

DAX measures were created for:

- Total FCE, Total Appointments, Emergency Episodes, Non-Emergency Episodes  
- DNA Count, DNA Rate %, A&E %, and other KPIs that drive all visuals.

**Key findings:**

- Across 2018–2025 there are ~939M total appointments, 151M FCEs and 123M FAEs.  
- Roughly 57M appointments were DNAs, giving an overall DNA rate of ~6%.  
- Emergency episodes account for ~38% of all FAEs, showing the burden of unplanned care.  
- Demand is highest in older working-age and early older-age groups (60–79).  
- DNA volumes peak in younger adults (c. 25–44), then decline in older ages.  
- 2020 shows a clear COVID-related dip, with activity exceeding pre-pandemic levels by 2023–2024.  
- The emergency share of episodes rises sharply from age 70+, indicating higher acuity in older patients.  
- A small but persistent “Unknown” age band highlights data-quality issues.

**Dashboard Overview:**

- **KPI Cards:** Total appointments, DNAs, FCEs, FAEs, DNA %, and A&E %.  
- **Total DNAs by Age_Band (Column Chart):** Ranks age bands by missed appointments.  
- **Total Appointments by Age Band (Column Chart):** Shows the life-course profile of demand.  
- **2018–2025 Appointments, A&E and Non-A&E (Stacked Area Chart):** Reveals COVID dip and recovery.  
- **Acuity and Case-mix by Age Band (100% Stacked Columns):** Compares emergency vs non-emergency episodes.  
- **Interactive Slicers (Year & Age_Band):** Allow scenario-based analysis, e.g. DNAs for 20–24 year-olds in 2024.

![2018_2025_NHS_HES_by_Age_Group](/2018_2025_NHS_HES_by_Age_Group.jpg)

</div>
