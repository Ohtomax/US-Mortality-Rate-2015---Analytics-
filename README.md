# Death in the United States (2015)
## DATA Processing Using CLEAN Framework

---

## Conceptualize the Data

- Understanding first what every row represents
- Understanding what each code means
- Identify whether things are qualitative or categorical values

The dataset contains **77 columns** and **2.7 million rows**.

- The data is already cleaned and requires only little configuration
- The analyst decided not to use every column. The reasons are:

  - **Improved System Performance** — Processing millions of rows across 77 columns requires massive amounts of RAM and slows down development. By dropping unnecessary data, code runs faster, the dashboard stays responsive, and the project is optimized for lower-end hardware or web hosting.
  - **Elimination of Redundant Data** — The dataset contains multiple columns that repeat the same information in different formats, such as age being grouped in three different ways. Selecting one "Source of Truth" removes confusion and prevents charts from being cluttered with overlapping or repetitive statistics.
  - **Clearer Storytelling** — Too many variables can overwhelm a viewer and bury the actual insights. Narrowing focus to core columns ensures the visualization answers clear questions — like how education affects health — rather than getting lost in obscure technical flags.

### Columns Retained for Analysis

| Column Name | Description |
|---|---|
| `resident_status` | Residency classification of the decedent |
| `education_2003_revision` | Education level (2003 revision) |
| `month_of_death` | Month in which death occurred |
| `sex` | Biological sex of the decedent |
| `age_recode_12` | Age group (12-category recode) |
| `marital_status` | Marital status at time of death |
| `day_of_week_of_death` | Day of the week death occurred |
| `manner_of_death` | Classification of how death occurred |
| `113_cause_recode` | Cause of death (113-category recode) |
| `race` | Racial classification of the decedent |
| `place_of_death_and_decedent_status` | Location and status at time of death |

---

## CDC Mortality Data Dictionary (2015)

### 1. `resident_status`

| Code | Description |
|---|---|
| `1` | **RESIDENTS** — State and County of Occurrence and Residence are the same |
| `2` | **INTRASTATE NONRESIDENTS** — State of Occurrence and Residence are the same, but County is different |
| `3` | **INTERSTATE NONRESIDENTS** — State of Occurrence and Residence are different, but both are in the U.S. |
| `4` | **FOREIGN RESIDENTS** — State of Occurrence is one of the 50 States or D.C., but Residence is outside of the U.S. |

---

### 2. `education_2003_revision`

| Code | Description |
|---|---|
| `1` | 8th grade or less |
| `2` | 9–12th grade, no diploma |
| `3` | High school graduate or GED completed |
| `4` | Some college credit, but no degree |
| `5` | Associate degree (e.g., AA, AS) |
| `6` | Bachelor's degree (e.g., BA, AB, BS) |
| `7` | Master's degree (e.g., MA, MS, MEng, MEd, MSW, MBA) |
| `8` | Doctorate (e.g., PhD, EdD) or Professional degree (e.g., MD, DDS, DVM, LLB, JD) |
| `9` | Unknown |

---

### 3. `month_of_death`

| Code | Month |
|---|---|
| `01` | January |
| `02` | February |
| `03` | March |
| `04` | April |
| `05` | May |
| `06` | June |
| `07` | July |
| `08` | August |
| `09` | September |
| `10` | October |
| `11` | November |
| `12` | December |

---

### 4. `sex`

| Code | Description |
|---|---|
| `M` | Male |
| `F` | Female |

---

### 5. `age_recode_12`

| Code | Age Group |
|---|---|
| `01` | Under 1 year (includes all infant deaths) |
| `02` | 1–4 years |
| `03` | 5–14 years |
| `04` | 15–24 years |
| `05` | 25–34 years |
| `06` | 35–44 years |
| `07` | 45–54 years |
| `08` | 55–64 years |
| `09` | 65–74 years |
| `10` | 75–84 years |
| `11` | 85 years and over |
| `12` | Age not stated |

---

### 6. `marital_status`

| Code | Description |
|---|---|
| `S` | Never married, single |
| `M` | Married |
| `W` | Widowed |
| `D` | Divorced |
| `U` | Marital status unknown |

---

### 7. `day_of_week_of_death`

| Code | Day |
|---|---|
| `1` | Sunday |
| `2` | Monday |
| `3` | Tuesday |
| `4` | Wednesday |
| `5` | Thursday |
| `6` | Friday |
| `7` | Saturday |
| `9` | Unknown |

---

### 8. `manner_of_death`

| Code | Description |
|---|---|
| `1` | Natural |
| `2` | Accident |
| `3` | Suicide |
| `4` | Homicide |
| `5` | Pending investigation |
| `6` | Could not be determined |
| `7` | Self-Inflicted *(used in specific jurisdictions)* |

---

### 9. `113_cause_recode` — Categorized

| Code Range | Category |
|---|---|
| `001–018` | Infectious and parasitic diseases (includes Septicemia, HIV, Tuberculosis) |
| `019–044` | Neoplasms (019–043: Malignant/Cancer; 044: Benign) |
| `045` | Anemias |
| `046` | Diabetes mellitus |
| `047–049` | Nutritional deficiencies (includes Malnutrition) |
| `050–052` | Diseases of the nervous system (052: Alzheimer's; 051: Parkinson's) |
| `053–075` | Major cardiovascular diseases |
| `076–089` | Diseases of the respiratory system |
| `090–096` | Diseases of the digestive system (includes 093–095: Chronic liver disease & cirrhosis) |
| `097–104` | Diseases of the genitourinary system (includes 097–102: Kidney diseases/Nephritis) |
| `105–110` | Pregnancy, perinatal, congenital conditions, and abnormal clinical findings |
| `111` | All other diseases (Residual) |
| `112–135` | External causes of mortality |

---

### 10. `race`

| Code | Race |
|---|---|
| `01` | White |
| `02` | Black |
| `03` | American Indian (includes Aleuts and Eskimos) |
| `04` | Chinese |
| `05` | Japanese |
| `06` | Hawaiian (includes Part-Hawaiian) |
| `07` | Filipino |
| `18` | Asian Indian |
| `28` | Korean |
| `38` | Samoan |
| `48` | Vietnamese |
| `58` | Guamanian |
| `68` | Other Asian or Pacific Islander |
| `78` | Combined other Asian or Pacific Islander |

---

### 11. `place_of_death_and_decedent_status`

| Code | Description |
|---|---|
| `1` | Hospital, Clinic or Medical Center — Inpatient |
| `2` | Hospital, Clinic or Medical Center — Outpatient or admitted to Emergency Dept. |
| `3` | Hospital, Clinic or Medical Center — Dead on Arrival |
| `4` | Decedent's home |
| `5` | Hospice facility |
| `6` | Nursing home / Long term care facility |
| `7` | Other |
| `9` | Place of death unknown |

---

## Documentation

### Locate Solvable Issues

1. **Duplicating raw dataset and removing unnecessary columns** — The analyst duplicated the raw dataset and removed columns not needed in the analysis. Each column was also checked for missing or null values. Upon checking, `manner_of_death` and `education_2003_revision` were the only columns with null values.


2. **Replacing null values in `manner_of_death`** — Since in the CDC's original source code a blank entry means "not specified," the analyst added a new primary key `9 = Not Specified` for the `manner_of_death` table and used it to replace all null values. Similarly, null values in `education_2003_revision` were replaced with `9 = Unknown`.

---

### Evaluate Unsolvable Issues

A comprehensive analysis of the current dataset indicates that all anomalies and discrepancies have been rectified. No unresolvable structural or logical issues were encountered during the process, ensuring that the data is now fully optimized and accurate.

---

### Augment the Data

3. **Adding a unique ID** — After replacing null values, a `unique_id` column was added to the fact table.

4. **Creating dimension tables** — Separate tables were created for each categorical column, since columns contained numerical codes representing specific values. Duplicates were removed from each created table.

---

## Issues Log

| Column(s) Affected | Issue Description | Magnitude | Solvable | Resolution |
|---|---|---|---|---|
| 77 Original Columns | Redundant data and unnecessary columns slowing down the system | 66 columns dropped | ✅ Yes | Dropped the redundant columns |
| `manner_of_death` | Contains null/missing values but has a corresponding description | 12.93% of rows | ✅ Yes | Replaced null values with corresponding description |
| Fact table | No primary key to uniquely identify each row | 100% of rows | ✅ Yes | Added a new unique ID column |
| `education_2003_revision` | Null values present | 2.43% of rows | ✅ Yes | Replaced null values with `9 = Unknown` |
| Categorical columns | Numerical values need mapping to categorical meanings | 11 columns | ✅ Yes | Added descriptions to each corresponding categorical column |

---

## Exploratory Data Analysis (EDA)

### DAX Codes for Measures and KPIs

#### 1. Total Deaths
```dax
Total Deaths = COUNT(fact_table[Unique_id])
```
Counts the number of unique deaths in the dataset. Used as the baseline measure for mortality.

---

#### 2. Avg Deaths Per Month
```dax
Avg Deaths Per Month =
AVERAGEX(VALUES(fact_table[month_of_death]), [Total Deaths])
```
Calculates the average number of deaths per month.

---

#### 3. Avg Weekday Deaths
```dax
Avg Weekday Deaths =
AVERAGEX(
    FILTER(VALUES(fact_table[day_of_week_of_death]),
    fact_table[day_of_week_of_death] IN {2, 3, 4, 5, 6}),
    [Total Deaths]
)
```
Calculates the average number of deaths on weekdays (Monday to Friday).

---

#### 4. Avg Weekend Deaths
```dax
Avg Weekend Deaths =
AVERAGEX(
    FILTER(VALUES(fact_table[day_of_week_of_death]),
    fact_table[day_of_week_of_death] IN {1, 7}),
    [Total Deaths]
)
```
Calculates the average number of deaths on weekends (Saturday and Sunday).

---

#### 5. Facility Deaths
```dax
Facility Deaths =
CALCULATE(
    [Total Deaths],
    fact_table[place_of_death_and_decedents_status] IN {1, 2, 3}
)
```
Calculates total deaths that occurred in healthcare facilities (codes 1, 2, and 3).

---

#### 6. Healthcare Burden Index
```dax
Healthcare Burden Index = DIVIDE([Facility Deaths], [Total Deaths], 0)
```
Calculates the proportion of deaths that occurred in healthcare facilities relative to total deaths.

---

#### 7. Infant Deaths
```dax
Infant Deaths = CALCULATE([Total Deaths], fact_table[age_recode_12] = 1)
```
Calculates total infant deaths (age category 1).

---

#### 8. Infant Mortality Proportion
```dax
Infant Mortality Proportion = DIVIDE([Infant Deaths], [Total Deaths], 0)
```
Calculates the proportion of deaths that were infants relative to total deaths.

---

#### 9. Peak Season Variance
```dax
Peak Season Variance =
DIVIDE([Max Deaths In A Month] - [Avg Deaths Per Month], [Avg Deaths Per Month], 0)
```
Calculates the variance between peak monthly deaths and the average deaths per month.

---

#### 10. Preventable Deaths
```dax
Preventable Deaths =
CALCULATE(
    [Total Deaths],
    fact_table[manner_of_death] IN {2, 3, 4}
)
```
Calculates total preventable deaths based on manner of death (codes 2, 3, and 4).

---

#### 11. Preventable Death Proportion
```dax
Preventable Death Proportion = DIVIDE([Preventable Deaths], [Total Deaths], 0)
```
Calculates the proportion of preventable deaths relative to total deaths.

---

#### 12. Top Cause Deaths
```dax
Top Cause Deaths =
MAXX(VALUES('113_cause_recode'[Description]), [Total Deaths])
```
Calculates the top cause of death based on the highest total deaths.

---

#### 13. Top Cause Dominance
```dax
Top Cause Dominance = DIVIDE([Top Cause Deaths], [Total Deaths], 0)
```
Calculates the dominance of the top cause of death relative to total deaths.

---

#### 14. Premature Deaths
```dax
Premature Deaths = CALCULATE([Total Deaths], fact_table[age_recode_12] <= 8)
```
Calculates total deaths occurring in younger age brackets.

---

#### 15. Premature Mortality Ratio
```dax
Premature Mortality Ratio = DIVIDE([Premature Deaths], [Total Deaths], 0)
```
Calculates the proportion of total deaths that are considered premature.

---

### Classification of Measures and KPIs

#### Metrics
These are baseline DAX calculations providing raw quantitative counts and averages from the `fact_table`.

- **Measure 1:** Total Deaths *(the ultimate baseline metric)*
- **Measures 2, 3, 4:** Raw timeline averages — Avg Deaths Per Month, Avg Weekday Deaths, Avg Weekend Deaths
- **Measures 5, 7, 10, 12, 14:** Raw demographic and categorical counts — Facility Deaths, Infant Deaths, Preventable Deaths, Top Cause Deaths, Premature Deaths

#### KPIs
These measures divide and compare data, turning raw counts into rates, proportions, and variances.

- **Measure 6 — Healthcare Burden Index:** Tells hospital administrators what percentage of total mortality is happening inside their facilities vs. at home. If this index spikes, hospitals are overwhelmed.
- **Measure 8 — Infant Mortality Proportion:** A globally recognized public health indicator. Tracking proportion rather than raw count shows if maternal and infant care is improving relative to the general population.
- **Measure 9 — Peak Season Variance:** Measures hospital and systemic strain. A high variance percentage warns administrators of massive seasonal spikes (like winter flu season) so they can allocate staff and resources accordingly.
- **Measure 11 — Preventable Death Proportion:** The most actionable number for public health officials. It tells exactly what percentage of deaths could have been avoided with better policy, safety, or medical intervention.
- **Measure 13 — Top Cause Dominance:** Shows how heavily the leading cause of death (e.g., Cancer) outweighs everything else.
- **Measure 15 — Premature Mortality Ratio:** Tracks the societal and economic loss of life before retirement age, highlighting systemic issues in community health or accident prevention.

#### OKRs

- Improve community safety and well-being by targeting the root causes of non-natural mortality.
- Relieve pressure on inpatient healthcare facilities by expanding end-of-life care options outside the hospital.
- Flatten the mortality curve during the high-risk winter months.

---

## Data Modeling Analytics

Data modeling is the process of organizing and structuring data to improve storage, retrieval, and analytical processing. In this study, the group used a **Star Schema** data model to efficiently organize the mortality dataset for descriptive analytics and reporting purposes. The Fact Table is connected to multiple Dimension Tables using primary and foreign key relationships, forming a Star Schema structure.

### Data Preparation

Before the data modeling process, the dataset underwent a preparation phase to ensure accuracy, consistency, and reliability. The original dataset contained approximately **2.7 million rows** and **77 columns**. Since not all fields were necessary for the analytical objectives, only the relevant columns required for the star schema design and descriptive analytics were selected. Columns considered unnecessary, redundant, or unrelated to the study were removed to simplify the dataset and improve processing efficiency.

Additionally, the dataset was checked for null or missing values. Special attention was given to the `manner_of_death` column, where blank entries — per the CDC's original source — mean "not specified." All null values in this field were replaced with **`9 = Not Specified`** to maintain data consistency and avoid empty entries during modeling.

---

### Star Schema

The Star Schema was selected because it:

- Improves data organization and reduces redundancy
- Simplifies database relationships for easier analysis and reporting
- Enhances query performance and supports efficient handling of large datasets
- Makes dashboard visualization more manageable
- Improves maintainability by allowing descriptive information to be updated within dimension tables without affecting the entire dataset

The Star Schema was successfully designed to organize the mortality dataset into a structured and optimized analytical database. Through data cleaning, fact table creation, dimension table development, and relationship mapping, the dataset became easier to manage and analyze.

---

### Descriptive vs. Predictive Analytics

The study used **descriptive analytics** instead of predictive analytics because the main objective was to analyze, summarize, and present existing mortality data patterns. The analysis focused on:

- Identifying trends, distributions, frequencies, and relationships among variables such as age, sex, race, education level, manner of death, and causes of mortality
- Answering questions such as *"What happened?"* and *"What patterns can be observed in the dataset?"*

Descriptive analytics was appropriate because the dataset contains historical and categorized records gathered from CDC mortality data. The group used statistical summaries, Power BI visualizations, KPIs, charts, and measures such as Total Deaths, Average Age, Preventable Deaths, and Total Deaths by Age Group.

**Predictive analytics was not applied** because the study did not involve machine learning models, forecasting techniques, regression models, or AI algorithms. The purpose was to provide a clear interpretation and visualization of existing mortality records — not to predict future outcomes.

---

## Visualization and Dashboard

The dashboard design follows the **DASH** framework:

- **D — Decision:** The dashboard helps health officials identify which health issues and population groups need the most attention to reduce preventable deaths. It supports better decision-making by showing important mortality trends and healthcare burdens.

- **A — Audience:** Intended for **Public Health Officials** and **Hospital Managers** who require both high-level summaries and detailed analytical views of mortality data. These users need quick access to important indicators such as total deaths and preventable death proportions, while also being able to explore deeper details involving age groups, education levels, race, causes of death, and place of death.

- **S — Signal:** The dashboard emphasizes the most critical health indicators that immediately communicate the overall mortality situation. Key metrics — **Total Deaths, Preventable Deaths, Premature Deaths, Infant Deaths**, and leading causes of death — serve as the primary signals guiding user attention.

- **H — Hierarchy:** The dashboard begins with high-level summary cards, followed by demographic and comparative charts showing patterns across sex, age groups, education levels, race, and manner of death. It then transitions into more detailed visualizations such as monthly trends, specific causes of death, and place of death records.

---

### Dashboard Wireframes

#### Page 1
- **SLICERS** (top bar)
- **Big Number** cards: Total Deaths, Number Index, Percentages
- **Charts:** Sex, Leading Manner of Death, Age Group, Education, Race

#### Page 2
- **SLICERS** (side panel)
- **Big Number** cards (3)
- **Chart:** Age Group and Manner of Death
- **Chart:** Cause of Deaths

#### Page 3
- **SLICERS** (side panel)
- **Big Number** cards (3)
- **Chart:** Deaths per Month
- **Charts:** Place of Death and Decedents Status, Resident Status

---

## Insights and Recommendations

### 1. The Burden of Chronic Illness
The dashboard reveals that natural causes account for the vast majority of mortality, exceeding **2 million cases** and significantly outpacing accidents, homicides, and suicides. This indicates that chronic illnesses and age-related diseases remain the primary burden on the healthcare system. Healthcare networks must prioritize preventive care programs, routine screenings, and long-term disease management to mitigate mortality from preventable natural causes.

---

### 2. Aging Population and Geriatric Care
Mortality rates surge among older age groups — particularly individuals aged **65 and above** — with the highest concentration in the *"85 years and over"* category. This underscores the critical need for robust geriatric care, accessible medical services, and targeted elderly wellness programs. Government agencies and healthcare providers must expand investments in senior healthcare facilities, home care support networks, and active chronic disease monitoring.

---

### 3. Addressing Preventable and Premature Mortality
The data highlights a critical area for intervention: approximately **65.6K preventable deaths** and **701K premature deaths**. Many of these outcomes could be avoided through:

- Promotion of healthier lifestyles
- Expanded vaccination programs
- Routine check-ups
- More equitable access to care

Policymakers should strengthen community-based health initiatives and education to directly minimize this avoidable mortality.

---

### 4. Predictive Operations for Seasonal Spikes
A clear temporal trend emerges with mortality peaking during **January** and **December**. These seasonal surges are likely associated with colder weather complications, respiratory disease outbreaks (such as the flu), and strain on healthcare access during the holidays. To counter this, hospitals and medical networks must:

- Proactively increase staffing
- Reinforce emergency department readiness
- Stockpile essential medical supplies prior to high-risk winter months

---

### 5. Optimizing the Center of Care
The majority of deaths occur in **clinical settings**, specifically hospital inpatient facilities, with state residents comprising the largest portion of cases. Improving operational efficiency, patient monitoring, and overall accessibility is vital to managing these high patient volumes. Additionally, expanding **outpatient community healthcare** and early intervention programs could divert high-risk patients, reducing the burden of critical, late-stage hospital admissions.


### CSV File - https://drive.google.com/drive/folders/17h8-FiHdMFRS1kvdC81et0m0W8YxuW1V?usp=sharing
