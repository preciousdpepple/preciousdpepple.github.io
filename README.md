
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

- Across 2018–2025 there are ~939M appointments, 211M DNAs (DNA % ~22.5%), 233M first-time visits, 151M FCEs, 123M FAEs, and 47M A&E episodes (A&E % ~37.8%).  
- Emergency episodes account for ~38% of all FAEs, showing the burden of unplanned care.  
- Demand for appointment is highest in older working-age and early older-age groups (60–79).  
- DNA volumes peak in younger adults (35–39, 30–34, 40–44, and 25–29), then decline in older ages.  
- 2020 shows a clear COVID-related dip, with activity exceeding pre-pandemic levels by 2023–2024.  
- The emergency share of episodes rises sharply from age 70+, indicating higher acuity in older patients. Meanwhile, Non-emergency episodes are concentrated in older working-age to early-older bands (55–79).
- There is a small but persistent “Unknown” age band which highlights data-quality issues to be addressed by the NHS in future publications.

**Dashboard Overview:**

- **KPI Cards:** Total appointments, DNAs, FCEs, FAEs, DNA %, and A&E %.  
- **Total DNAs by Age_Band (Column Chart):** Ranks age bands by missed appointments.  
- **Total Appointments by Age Band (Column Chart):** Shows the life-course profile of demand.  
- **2018–2025 Appointments, A&E and Non-A&E (Stacked Area Chart):** Reveals COVID dip and recovery.  
- **Acuity and Case-mix by Age Band (100% Stacked Columns):** Compares emergency vs non-emergency episodes.
- **Non-Emergency Episodes by Age Band (donut):** contribution of each age band.
- **Emergency Episodes by Age Band (treemap):** age bands driving urgent workload.
- **Interactive Slicers (Year & Age_Band):** Allow scenario-based analysis, e.g. DNAs for 20–24 year-olds in 2024.

![2018_2025_NHS_HES_by_Age_Group3](/2018_2025_NHS_HES_by_Age_Group3.jpg)

</div>

<div class="project-card" markdown="1">
  
## Project 3

**Title:** 2018–2025 NHS Hospital Episode Statistics — by Treatment Specialty (England)

**Tools Used:** Power BI Desktop, Power Query, DAX, Data Modeling, Excel/CSV Cleaning & Transformation

**Project Description**

Interactive Power BI report analysing 2018–2025 HES activity by Treatment Specialty (England). It brings together appointments, attendance (DNAs vs Attended), A&E episodes, FCEs and FAEs to show where demand and acuity sit by specialty and how they trend over time.

**Data Preparation and Cleaning (Power Query)**

Standardised Treatment_Specialty_Name (trim/case, fix “&” → “&”), unified column names across files.

Coerced activity fields to Whole Number; replaced */—/blanks with 0 where valid.

Kept a single Date column (no Dim Date); used Date instead.

Attended_Appointments (if not supplied) = [Total_Appointments] - [DNA_Appointments].

Removed duplicates on [Date],[Treatment_Specialty_Name].

Row-level checks to ensure Attended + DNA = Total_Appointments and A&E + NonEmergency = FAE.

**Core DAX Measures**
Appointments = SUM('2018–2025 Treatment_SPEC'[Total_Appointments])
Attended     = SUM('2018–2025 Treatment_SPEC'[Attended_Appointments])
DNA          = SUM('2018–2025 Treatment_SPEC'[DNA_Appointments])
FCEs         = SUM('2018–2025 Treatment_SPEC'[FCE])
FAEs         = SUM('2018–2025 Treatment_SPEC'[FAE])
A&E Episodes = SUM('2018–2025 Treatment_SPEC'[A&E_Episodes])
Attendance % = DIVIDE([Attended], [Appointments])
DNA %        = DIVIDE([DNA], [Appointments])
A&E %        = DIVIDE([A&E Episodes], [FAEs])

**KPI Cards:** Appointments, Attended, DNA, A&E, A&E %, FCEs, FAEs.
– The analysis shows that, overall attendance runs ~77.5% (gauge) with ~211M DNAs across the period.

- Total DNA’s by Specialty (bar): ranks specialties by missed appointments.

- % Appointment Attendance (gauge): gives a quick read of access effectiveness.

- Total Appointments & DNA by Year (clustered columns): highlights volume vs non-attendance trend (COVID dip in 2020, recovery by 2023–24).

- Top Appointments / Attendance / DNA by Specialty (bar with three measures): presents side-by-side workload vs non-attendance.

- Top A&E Episodes by Specialty (donut): General Internal Medicine dominates emergency care; General Surgery and Trauma & Orthopaedics follow; outpatient-heavy specialties (e.g., Ophthalmology) have comparatively small A&E share.

- FAE leaderboard (table): Here, the specialties are ranked by FAE.

- Total A&E, FAE, FCE by Year (line/column): showing acuity and admitted activity over time.

- Total Appointments & A&E by Year (stacked columns): shows relationship between demand and urgent pressure.

**Slicers:** Date (supports single year or multi-year range) and Treatment_Specialty_Name (multi-select). Everything is measure-driven for consistent aggregation.

**Key Findings:**

- Scale of activity: Approximately 939M appointments with 727M attendance and 211M DNAs. The overall attendance rate is around 77.48%, aligned with the gauge card, indicating nearly one in five appointments result in non-attendance.

- Emergency pressure is specialty-skewed. About 47M emergency FAEs; A&E share around 37.8% suggests a substantial proportion of first episodes are unplanned, highlighting pressure on urgent care. General Internal Medicine carries the largest A&E burden (biggest slice in the donut), indicating where urgent pathways and bed capacity matter most.

- Episode dynamics: FCEs (151M) exceed FAEs (123M), consistent with multiple consultant episodes per admission. Day case activity vs ordinary admissions reveals procedural intensity and shifting care models toward same-day treatment in several specialties.

- Elective & outpatient workload sits elsewhere. High-demand specialties include Ophthalmology, Trauma & Orthopaedics, Diagnostics, Physiotherapy, Urology, Cardiology, Dermatology, Gynaecology, Obstetrics, and Midwifery. These specialties also contribute to a large DNA volume, making it the prime candidate for targeted non-attendance interventions (SMS reminders, fast rebooking, virtual pre-ops).

- The “Total DNAs by Specialty” chart shows wide variation (roughly 15M down to 4M), indicating targeted specialties for attendance improvement programs.

- Surgical front door.  General Internal Medicine Service, General Surgery and Trauma & Orthopaedics show high A&E and FAE activity, reflecting trauma and acute surgical inflow—useful for theatre and bed planning.

- Attendance vs DNA gap. With ~77% attendance, reducing DNA by even 1 percentage point at high-volume specialties (Ophthalmology, Trauma & Orthopaedics, Diagnostics, Physiotherapy & Urology Services) yields outsized capacity gains.

- Time trends for A&E, FAE and FCE. Shows a clear 2020 dip during the pandemic, with sustained recovery by 2023–2024 across appointments, FCEs and FAEs. A&E remains comparatively resilient.

- Operational cue. The specialties that dominate FAEs (inpatient/overnight episodes) differ from those that dominate appointments—resource allocation should mirror this split (beds vs clinics).

**Suggested Actions:**

- DNA reduction playbook in Ophthalmology & other high-DNA specialties: automated reminders, digital check-in, short-notice fill lists, cohort-specific messaging should be deployed to improve attendance levels.

- Emergency flow: prioritise Same-Day Emergency Care in General Medicine and standardised pathways in General Surgery / T&O to reduce conversion to admission.

- Capacity planning: align theatre/bed capacity with FAE leaders; align clinic staffing with appointment leaders.

- Quality flags: keep monitoring residual Unknown categories and any non-numeric values introduced in future refreshes.

![2018_2025_NHS_HES_by_Treatment SPEC](/2018_2025_NHS_HES_by_Treatment SPEC.jpg)

</div>

<div class="project-card" markdown="1">
  
##Project 4
**Title:** 2018–2025 NHS Hospital Episode Statistics — by Providers in England
**Tools Used:** Power BI Desktop, Power Query, DAX, Data Modeling, Excel/CSV Cleaning & Transformation

**Project Description**
This Power BI dashboard presents an interactive analysis of NHS Hospital Episode Statistics (HES) across England, in 2025, with a focus on performance by individual healthcare providers and CCGs. It integrates total episodes, first attendances, DNAs, elective and non-elective splits, and supports drill-down by date, CCG, and provider. The aim is to illuminate where acute care demand and non-attendance rates are concentrated, reveal month-on-month and provider-level variation, and inform resource optimization.​

**Data Preparation and Cleaning (Power Query)**
Provider and CCG names were standardized (case, spelling, symbol consistency), and numeric fields representing activity (appointments, attendances, DNAs) were coerced to valid integers.

Null, blank, or missing activity data was replaced with zeroes only where logically valid, preventing spurious aggregations.

Retained a single Date field for temporal analysis and deduplicated records by date and provider.

Validated row-level sums for attendance and DNA against totals, and checked for consistency between acute ordinary and non-elective reporting.

**Core DAX Measures**
Appointments, First Seen, Subsequent Seen, and DNAs: summed using provider-level and CCG-level grouping.

Proportion metrics: Calculated DNA % = DIVIDE([DNA],[Seen]), and elective/non-elective distributions per period.

Funnel metrics: staged through referrals to first/subsequent attendances, with DNA attrition visualized at each stage.

Monthly time series and provider/CCG segmentation implemented to visualize trends in attendance, DNA, and acute performance.

**KPI Highlights and Chart Insights**
System Scale: Across England, 65.5K providers contributed to 22.6M subspecialty attendances, with a 6.6% DNA rate, 11M first attendances, and ~1.5M DNAs.​

Elective vs Non-Elective: 2.9M elective and 2.5M non-elective activities are tracked, with visual breakdowns by provider (bar chart), showing large site-to-site variation (Manchester University NHS FT and University Hospitals Birmingham NHS FT are key contributors to both streams).

DNA Funnel & Specialty/CCG Outliers: Funnel visualization shows 15M subsequent attendances after 8M first attendances, with 2M lost as DNAs—over 10% attrition at this stage. Donut and column charts further surface high-DNA CCGs and specialties.

Temporal Patterns: Month-on-month, there is a summer decline in both acute elective and non-elective episodes (July 2025 shows lower activity vs April–June 2025), consistent with operational seasonality or reduced demand.​

Top Providers & Segmentation: The report allows instant identification of high-throughput providers in both elective and non-elective domains. Specialty performance can also be isolated.

GP vs Other Referrals: Acute case line chart splits GP and other referral sources, showing a substantial drop to 0.6M total cases in July after a consistent 1.1M–1.4M per month earlier in 2025.

Acute/Elective Mix Insight: Monthly stacked columns display the elective/non-elective mix, with elective activity composing about 39% and non-elective about 54% each month in the sample period.

**Key Findings**
Persistent non-attendance (DNA) rates (~6.6%) and substantial volume of subsequent DNAs (up to 80K in worst-case CCGs) indicate a need for targeted attendance-improvement strategies.

The clear summer dip signals an opportunity for seasonal resourcing or flexible planning.

Providers delivering the highest workloads (Manchester, Birmingham, Sheffield, Newcastle) experience both significant elective and emergency demand, validating dual-approach resource models.

Funnel drop-offs show where attrition is highest (post-referral, post-initial attendance), essential for focusing operational improvements.

Acute care remains a substantial share of workload, especially notable in specialty and provider breakdowns.

Suggested Actions
Deploy reminder and rebooking strategies, particularly for specialties and CCGs with highest DNAs.

Seasonally adapt elective and acute care capacity, aligning resources with observed summer dips and provider-specific trends.

Use top provider and CCG lists to prioritize pilot interventions and diffusions of successful attendance strategies.

Routinely validate incoming data for residual quality issues as per cleaned fields (avoid future contamination from blanks/non-numeric values).

This dashboard delivers data-driven visibility and actionable intelligence for NHS planners and provider management teams, supporting operational efficiency and improved patient flow.

![2018_2025_NHS_HES_by_Provider](/2018_2025_NHS_HES_by_Provider.jpg)

</div>
