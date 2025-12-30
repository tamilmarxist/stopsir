# Analysis on SIR Deletion

Tamil Nadu Electoral Roll Deletion Analysis - A comprehensive examination of voter deletions from the Special Intensive Revision (SIR) process across all 234 Assembly Constituencies.

## 📊 Overview

This repository contains an in-depth analysis of voter deletions from the Tamil Nadu electoral rolls, examining patterns and statistics across all 234 Assembly Constituencies (ACs). The analysis focuses on the **Special Intensive Revision (SIR)** deletion process that occurred between January 2025 and December 2025 electoral roll updates.

### Key Features

- **Interactive Dashboard** (`index.html`) - State-level visualization with 20+ chart types
- **234 AC-specific Reports** (`ac_reports/`) - Individual detailed HTML reports for each constituency with 18+ chart types
- **Visual Analytics** - Color-coded heatmaps, bar charts, and pie charts
- **Sortable Data Tables** - Interactive tables for detailed data exploration

## 🗂️ Repository Structure

```
├── index.html              # Main dashboard with state-wide analysis
└── ac_reports/             # Individual constituency reports
    ├── ac_1_report.html   # கும்மிடிபூண்டி (Gummidipoondi)
    ├── ac_2_report.html   # பொன்னேரி (Ponneri)
    ├── ...
    └── ac_234_report.html # விளாத்திகுளம் (Vilathikulam)
```

---

## 📈 DASHBOARD CHARTS (`index.html`)

The main dashboard provides state-level analysis across all 234 constituencies. All charts use data from `ac_summary_ac_wise_full.csv`.

### Data Source
**File**: `ac_summary_ac_wise_full.csv`  
**Description**: Aggregated summary statistics for all 234 ACs including deletion counts, percentages, demographic breakdowns, and reason classifications.

---

### 1. **Constituency Navigation Grid**
**Chart Type**: Color-coded grid of clickable links  
**X-axis**: None (grid layout)  
**Y-axis**: None (grid layout)  
**Color Scale**: Gold (#FFD700) to Dark Red (#CD0000) based on `Total_Deleted_Pct`

**Data Used**:
- `AC_Number` - Assembly constituency number
- `AC_Name` - Name in Tamil
- `Total_Deleted_Pct` - Percentage of deleted voters

**What You Can Understand**:
- Visual heatmap of deletion intensity across the state
- Quick identification of high-deletion constituencies
- Geographic patterns in voter roll maintenance
- Outlier constituencies requiring investigation

**How to Use**: Click any constituency box to view its detailed AC report. Color intensity shows deletion severity.

---

### 2. **Total Deletions**
**Chart Type**: Bar chart with heatmap coloring  
**X-axis**: AC Number (1-234)  
**Y-axis**: Total Deleted Count  
**Color Scale**: Gold to Dark Red based on `Total_Deleted_Pct`

**Data Used**:
- `AC_Number_Str` - AC number as string for categorical axis
- `Total_Deleted` - Total number of deleted voters per AC
- `Total_Deleted_Pct` - Deletion percentage for color coding
- `AC_Name` - Displayed on hover
- `Total_Considered` - Context on hover

**What You Can Understand**:
- Absolute deletion counts across all constituencies
- Which ACs had the highest raw deletion numbers
- Correlation between deletion count and deletion percentage
- Urban vs rural deletion patterns (high bars often indicate larger urban ACs)

---

### 3. **Net Deviation**
**Chart Type**: Bar chart with diverging color scale  
**X-axis**: AC Number  
**Y-axis**: Deviation Count  
**Color Scale**: RdBu (Red-Blue diverging) based on `Deviation_Pct`

**Data Used**:
- `Deviation` - Calculated as: (Dec_2025_Electors + Deleted) - Jan_2025_Electors
- `Deviation_Pct` - Deviation as percentage of Total_Considered
- Formula shows net change after accounting for additions and deletions

**What You Can Understand**:
- Whether deletions were balanced by additions (new registrations)
- Net growth or shrinkage of electoral roll per AC
- Data integrity issues (large deviations may indicate discrepancies)
- Electoral roll dynamics beyond just deletions

**Example Insight**: Negative deviation means deletions exceeded additions; positive means roll grew despite deletions.

---

### 4-6. **Gender Deleted Charts** (Male, Female, Transgender)
**Chart Type**: Bar chart with heatmap (3 separate charts)  
**X-axis**: AC Number  
**Y-axis**: Gender-specific deletion count  
**Color Scale**: Gold to Dark Red based on gender-specific percentage

**Data Used** (for each gender):
- `Gender_Male` / `Gender_Female` / `Gender_Transgender` - Deletion counts
- `Gender_{Gender}_Heatmap_Pct` - Calculated as (Gender_Count / Total_Considered * 100)
- Shows deletion intensity relative to total AC population

**What You Can Understand**:
- Gender-specific deletion patterns
- Whether one gender is disproportionately affected
- Regional variations in gender-based deletions
- Demographic impacts of roll maintenance

**Sub-charts (2x2 Grid per Gender)**: For each gender, there are 4 reason-based breakdowns:
- Gender-Deceased
- Gender-Shifted  
- Gender-Missing
- Gender-Duplicate

**Data for Sub-charts**:
- `Gender_{G}_{Reason}` - Count (e.g., `Gender_Male_Deceased`)
- `Gender_{G}_{Reason}_Pct` - Percentage relative to Total_Considered

**What Sub-charts Show**: Granular intersection of gender and deletion reason, revealing specific patterns like "Female-Shifted" being high due to post-marriage relocation.

---

### 7-8. **Mortality Rate Charts** (Male & Female)
**Chart Type**: Bar chart with heatmap  
**X-axis**: AC Number  
**Y-axis**: Mortality Rate (%)  
**Color Scale**: Gold to Dark Red

**Data Used**:
- `Male_Mortality_Rate` - Percentage of males deleted due to death
- `Female_Mortality_Rate` - Percentage of females deleted due to death
- Calculated as: (Gender_Deceased_Count / Total_Gender_Considered * 100)

**What You Can Understand**:
- Death rates captured in electoral roll maintenance
- Validation of deletion reasonableness (mortality should correlate with general health statistics)
- Gender-specific mortality trends
- Outlier ACs with unusual death rates (possible data errors or unique demographics)

**Use Case**: Cross-reference with state mortality data to validate deletion authenticity.

---

### 9. **Mortality Percentage Difference**
**Chart Type**: Bar chart with heatmap  
**X-axis**: AC Number  
**Y-axis**: Percentage Difference  
**Color Scale**: Gold to Dark Red

**Data Used**:
- `Mortality_Percentage_Difference` - Calculated as: ((Male_Rate - Female_Rate) / Female_Rate) * 100
- Shows proportional difference in mortality rates between genders

**What You Can Understand**:
- Gender mortality gap in deletions
- Whether male deaths are recorded  more/less than females
- Demographic anomalies requiring investigation
- Consistency of deletion processes across genders

**Example**: +50% difference means male mortality rate is 50% higher than female.

---

### 10-14. **Age Group Deleted Charts** (5 age brackets)
**Chart Type**: Bar chart with heatmap (5 separate charts)  
**X-axis**: AC Number  
**Y-axis**: Age-specific deletion count  
**Color Scale**: Gold to Dark Red

**Age Groups**:
1. 18-22 (First Time voters)
2. 23-40 (Young adults)
3. 41-65 (Middle-aged)
4. 65-75 (Senior citizens)
5. 75+ (Elderly)

**Data Used** (for each age group):
- `Age_{AgeGroup}` - Deletion count (e.g., `Age_18-22`, `Age_75_Plus`)
- `Age_{AgeGroup}_Pct` - Percentage relative to Total_Considered

**What You Can Understand**:
- Life-stage deletion patterns
- Migration trends (high 23-40 deletions suggest job/education mobility)
- Mortality trends (high 75+ deletions expected)
- First-time voter deletion rates (data quality for young voters)

**Sub-charts (2x2 Grid per Age Group)**: Each age group has 4 reason breakdowns:
- Age-Deceased
- Age-Shifted
- Age-Missing
- Age-Duplicate

**Data for Sub-charts**:
- `Age_{A}_{Reason}` - Count (e.g., `Age_23-40_Shifted`)
- `Age_{A}_{Reason}_Pct` - Percentage relative to Total_Considered

**Example Insights**:
- 18-22 with high "Duplicate" suggests registration cleanup
- 23-40 with high "Shifted" indicates economic migration
- 75+ with high "Deceased" is expected mortality pattern

---

### 15-18. **Reason-Based Deletion Charts** (4 reasons)
**Chart Type**: Bar chart with heatmap (4 separate charts)  
**X-axis**: AC Number  
**Y-axis**: Reason-specific deletion count  
**Color Scale**: Gold to Dark Red

**Deletion Reasons**:
1. **Deceased**: Voters who passed away
2. **Shifted**: Voters who moved to different locations
3. **Missing**: Voters who couldn't be located/verified
4. **Duplicate**: Duplicate entries in the electoral roll

**Data Used** (for each reason):
- `Reason_{Reason}_Count` - Count (e.g., `Reason_Deceased_Count`)
- `Reason_{Reason}_Pct` - Percentage relative to Total_Considered

**What You Can Understand**:
- Primary drivers of deletions in each AC
- Administrative vs. natural causes of deletions
- Migration patterns (high "Shifted")
- Data quality issues (high "Duplicate" or "Missing")

**Policy Implications**:
- High "Shifted" → Population mobility, urban migration
- High "Deceased" → Aging demographics
- High "Duplicate" → Past registration inefficiencies
- High "Missing" → Verification challenges, possible fraud detection

---

### 19. **Shifted + Missing Combined**
**Chart Type**: Bar chart with heatmap  
**X-axis**: AC Number  
**Y-axis**: Combined count  
**Color Scale**: Gold to Dark Red

**Data Used**:
- `Reason_Shifted_Missing_Count` - Sum of Shifted and Missing counts
- `Reason_Shifted_Missing_Pct` - Combined percentage
- Rationale: Both represent mobility-related removals

**What You Can Understand**:
- Total mobility-driven deletions
- Migration intensity per constituency
- Urban development impact (high in redevelopment zones)
- Electoral roll fluidity due to population movement

---

### 20. **Data Details Table**
**Table Type**: Interactive sortable table with heatmap styling  
**Columns**: 60+ columns including:
- General: AC_Number, AC_Name, Total_Deleted, Total_Deleted_Pct
- Integrity: Invalid_Names, Missing entries
- Roll Stats: Electors_Jan_2025, Electors_Dec_2025, Deviation
- Reasons: All deletion reasons with counts and percentages
- Gender: All gender breakdowns with counts and percentages
- Age: All age groups with counts and percentages

**Styling**: YlOrRd (Yellow-Orange-Red) gradient applied to numeric columns

**Features**:
- Click any column header to sort ascending/descending
- Sticky headers for easy navigation
- Color intensity shows relative values

**What You Can Understand**:
- Complete raw data behind all visualizations
- Cross-constituency comparisons
- Identify patterns not visible in charts
- Data export capability for further analysis

---

## 🏛️ ASSEMBLY CONSTITUENCY REPORTS (`ac_reports/ac_*.html`)

Each AC report provides granular analysis for a single constituency. All data comes from individual AC CSV files located at `E:/ac_wise_output/ac{number}.csv`.

### Data Source
**Files**: `E:/ac_wise_output/ac1.csv` through `ac234.csv`  
**Description**: Detailed deletion records for each AC including: Name, Age, Gender, Relationship, Reason, Part_Number (polling station), AC_Name  

**Additional Data**:
- `ac_summary_2025.csv` - January 2025 elector counts
- `ac_summary_2025_12.csv` - December 2025 elector counts  

---

### AC Report Chart 1: **Executive Summary**
**Type**: Text-based statistics  
**Data Used**:
- Total deleted records (row count)
- AC_Name (Tamil name)
- Parts affected (unique Part_Numbers)
- Missing Reason, Gender, Age counts
- Invalid Names count
- Electors_Jan_2025, Electors_Dec_2025 from summary CSVs
- Calculated deviation and gender breakdowns

**What You Can Understand**:
- Overall deletion scale for this AC
- Data quality assessment
- Roll size changes over the year
- Gender distribution of deletions

---

### AC Report Chart 2: **Deletion Reasons**
**Chart Type**: Donut pie chart  
**Data Used**: `Reason_Class` column value counts

**Categories** (mapped from Tamil text):
- Deceased (இறந்தவர்)
- Shifted (குடிபெயர்ந்தவர்கள்)
- Missing (வசிக்காதவர்கள்)
- Duplicate (பதிவு செய்யப்பட்டவர்கள்)
- Other

**What You Can Understand**:
- Main cause of deletions in this AC
- Whether deletions are legitimate (death, migration) vs administrative (duplicates)
- Percentage breakdown with both deleted-relative and total-considered percentages
- Validation of deletion authenticity

---

### AC Report Chart 3: **Gender Demographics**
**Chart Type**: Donut pie chart  
**Data Used**: `Gender_Class` column value counts  
**Mapping**: ஆண் →Male, பெண்→Female, திருநங்கை→Transgender

**What You Can Understand**:
- Gender balance of deletions
- Whether deletions disproportionately affect males or females
- Percentage relative to total gender population
- Demographic impact assessment

---

### AC Report Chart 4: **Gender vs. Reason Analysis**
**Chart Type**: Donut pie chart (visual) + Textual breakdown  
**Data Used**: Cross-tabulation of `Gender_Class` and `Reason_Class`

**What You Can Understand**:
 - How deletion reasons vary by gender
- E.g., Are women more likely deleted as "Shifted"? Are men more likely "Deceased"?
- Gender-specific migration and mortality patterns
- Allows validation of deletion patterns against expected demographic behaviors

**Example**: If 60% of female deletions are "Shifted" vs 35% for males, suggests post-marriage relocation pattern.

---

### AC Report Chart 5: **Female Deletions: Relationship Analysis**
**Chart Type**: Donut pie chart + Textual breakdown  
**Data Used**: For `Gender_Class='Female'`, cross-tabulate `Reason_Class` with `Relationship_Class`

**Relationship Mapping**:
- தந்தை → Father (unmarried/young women)
- கணவர் → Husband (married women)
- தாய் → Mother
- Other

**What You Can Understand**:
- Marital status of deleted women
- Whether married women (Husband relation) are more affected
- Mortality vs migration patterns by marital status
- Life-stage transitions and electoral roll changes

**Critical Insight**: High "Husband-Shifted" deletions may indicate women moving after marriage; high "Husband-Deceased" may indicate widows being removed.

---

### AC Report Chart 6: **Age Profile**
**Chart Type**: Donut pie chart  
**Data Used**: `Age_Group` column (binned from`Age`)

**Age Bins**:
- 17-22: 18-22 (First Time)
- 23-40
- 41-65
- 65-75
- 75+

**What You Can Understand**:
- Age distribution of deletions
- Which life stages are most affected
- Validation against expected patterns:
  - Young: Migration for education/work
  - Middle: Stable (fewer deletions expected)
  - Elderly: Mortality-driven deletions
- Data quality for age recording

**Textual Details**: Includes male vs female counts per age group with percentages.

---

### AC Report Chart 7: **Age & Gender Distribution**
**Chart Type**: Grouped bar chart  
**X-axis**: Age Groups  
**Y-axis**: Count  
**Bars**: Male (side-by-side) Female

**Data Used**: Cross-tabulation of `Age_Group` and `Gender_Class`

**What You Can Understand**:
- Gender disparities within specific age brackets
- Example: Do young women (23-40) get deleted more than young men?
- Mortality rate differences by gender across ages
- Whether deletion patterns match expected demographic transitions

**Example Analysis**: If Female bars exceed Male in 23-40, investigate for post-marriage migration. If Male bars exceed Female in 75+, reflects known gender mortality gap.

---

### AC Report Charts 8-10: **Reason by Age Group** (Overall, Male, Female)
**Chart Type**: Grouped/stacked bar chart (3 separate charts)  
**X-axis**: Age Groups  
**Y-axis**: Count  
**Bars/Colors**: Different deletion reasons

**Data Used**:
- **Overall**: Groupby `Age_Group` and `Reason_Class`
- **Male**: Filter `Gender_Class='Male'`, then groupby Age and Reason
- **Female**: Filter `Gender_Class='Female'`, then groupby Age and Reason

**What You Can Understand**:
- **Overall**: Life-stage deletion patterns
  - 18-22: Expected high "Duplicate" (registration cleanup)
  - 23-40: Expected high "Shifted" (migration)
  - 75+: Expected high "Deceased" (mortality)
- **Male-specific**: Allows validation that elderly males have high mortality deletions
- **Female-specific**: Reveals if young women have high "Shifted" (marriage migration)

**Validation Use**: Compare reason distribution across ages to expected norms. Outliers indicate data issues or unique local factors.

---

### AC Report Chart 11: **Female (Husband Relation) Analysis**
**Chart Type**: Grouped bar chart  
**X-axis**: Age Groups  
**Y-axis**: Count  
**Bars/Colors**: Deletion reasons

**Data Used**: Filter for `Gender_Class='Female'` AND `Relationship_Class='Husband'`, then groupby `Age_Group` and `Reason_Class`

**What You Can Understand**:
- Age-specific deletion patterns for married women
- Whether young married women (23-40) are deleted due to relocation
- Mortality among married women across age groups
- Widow removal patterns (Deceased deletions for elderly married women)

**Critical Analysis**: High "Shifted" for 23-40 married women confirms post-marriage relocation hypothesis.

---

### AC Report Chart 12: **Female (Father Relation) Analysis**
**Chart Type**: Grouped bar chart  
**X-axis**: Age Groups  
**Y-axis**: Count  
**Bars/Colors**: Deletion reasons

**Data Used**: Filter for `Gender_Class='Female'` AND `Relationship_Class='Father'`, then groupby `Age_Group` and `Reason_Class`

**What You Can Understand**:
- Age-specific deletion patterns for unmarried/young women
- Migration patterns for single women (education, employment)
- Mortality among unmarried women (should be rare except in older single women)
- Age distribution validation (should be concentrated in 18-40)

**Expected Pattern**: Most deletions in 18-40 range; high "Shifted" indicates migration for education/work.

---

### AC Report Chart 13: **Female Relationship Multi-Factor**
**Chart Type**: Complex faceted histogram (800px height)  
**X-axis**: Age Groups  
**Y-axis**: Count  
**Color**: Deletion Reason  
**Facets (rows)**: Top 3 relationship types

**Data Used**: Filter for `Gender_Class='Female'` and top 3 `Relationship_Class` values, plot as faceted histogram with `Age_Group` on X, colored by `Reason_Class`

**What You Can Understand**:
- Complete intersection of Age × Reason × Relationship for women
- Comprehensive view of female deletion patterns across all dimensions
- Enables complex demographic insights like:
  - "Married women aged 23-40 mostly deleted due to Shifted"
  - "Unmarried women aged 18-22 mostly deleted due to Duplicate"
  - "Elderly married women mostly deleted due to Deceased"

**Use Case**: Final validation chart showing the complete story of female deletions.

---

### AC Report Chart 14: **High Deletion Polling Stations (Top 20)**
**Chart Type**: Bar chart  
**X-axis**: Part_Number (polling station)  
**Y-axis**: Deletion Count  
**Color**: Blues color scale by count

**Data Used**: `Part_Number` column value counts, top 20

**What You Can Understand**:
- Which polling stations had highest deletions
- Localized deletion hotspots within the AC
- Possible issues at specific polling locations
- Targeted areas for ground verification

**Textual Details**: For each top station:
- Part_Number and Part_Name
- Total deletion count
- Gender breakdown with percentages
- Reason breakdown within each gender

**Investigation Tool**: Use this to identify specific booths requiring audit.

---

### AC Report Chart 15: **Detailed Station Analysis (Top 20)**
**Chart Type**: Mini card grid (2 columns × 10 rows)  
**Per Card**:
- Small bar chart: Reason × Gender for that station
- Textual stats: Gender and reason breakdowns

**Data Used**: For each of top 20 Part_Numbers, create cross-tab of `Reason_Class` and `Gender_Class`

**What You Can Understand**:
- Granular view of each high-deletion polling station
- Whether deletions at a station are concentrated in specific gender-reason combinations
- Enables station-level auditing
- Identifies unusual patterns (e.g., one station with 90% Female-Shifted deletions)

---

### AC Report Charts 16-21: **Reason-wise Top Stations** (6 sections)

Each section shows top 20 polling stations for a specific subset of deletions:

**16. Reason-wise Top 20 (Shifted + Missing Combined)**
- **Data**: `Reason_Class` replaced with 'Missing/Shifted' for both Missing/Shifted entries
- **Purpose**: Identify stations with high mobility-driven deletions

**17. Top Stations: Male Deletions**
- **Data**: Filter `Gender_Class='Male'`
- **Purpose**: Male-specific hotspot identification

**18. Top Stations: Female Deletions**
- **Data**: Filter `Gender_Class='Female'`
- **Purpose**: Female-specific hotspot identification

**19. Top Stations: Female (Husband)**
- **Data**: Filter `Gender_Class='Female'` AND `Relationship_Class='Husband'`
- **Purpose**: Married women deletion hotspots

**20. Top Stations: Female (Father)**
- **Data**: Filter `Gender_Class='Female'` AND `Relationship_Class='Father'`
- **Purpose**: Unmarried women deletion hotspots

**21. Reason-wise Top 20 Stations**
- **Data**: Overall `Reason_Class`, shown as separate cards per reason
- **Purpose**: Comprehensive reason-based station analysis

**Chart Format** (for each section):
- Bar chart showing top 20 stations
- Detailed textual breakdown per station:
  - Station name and total count
  - Gender breakdown with percentages
  - Reason breakdown within each gender

**What You Can Understand**:
- Targeted analysis for specific demographic or reason categories
- Enables focused ground investigations
- Identifies pattern consistency across station types
- Validates whether high deletions are localized or constituency-wide

---

## 📊 Data Interpretation Guide

### Understanding Deletion Percentages

| Deletion Rate | Interpretation | Action Required |
|--------------|----------------|-----------------|
| **0-10%** | Normal roll maintenance | Routine monitoring |
| **10-20%** | Active population movement or administrative cleanup | Review for patterns |
| **20-30%** | Significant deletion activity | Investigation recommended |
| **30%+** 🚨 | Unusual patterns | Immediate scrutiny required |

### Top 5 Constituencies with Highest Deletion Rates

Based on statewide analysis:

1. **AC 21 - அண்ணா நகர் (Anna Nagar)**: 42.18%
2. **AC 20 - ஆயிரம் விளக்கு (Thousand Lights)**: 40.68%
3. **AC 14 - வில்லிவாக்கம் (Villivakkam)**: 40.65%
4. **AC 18 - துறைமுகம் (Harbour)**: 38.64%
5. **AC 16 - எழும்பூர் (Egmore)**: 37.91%

**Pattern**: High deletion rates concentrated in Chennai urban constituencies, likely due to high mobility, redevelopment, and registration cleanup.

---

## 🚀 Usage Instructions

### Viewing the Dashboard

**Online Deployment**:
This repository can be deployed to GitHub Pages:
1. Enable GitHub Pages in repository settings
2. Set source to main branch
3. Access at: `https://[username].github.io/[repo-name]`

**Local Viewing**:
```bash
# Clone the repository
git clone https://github.com/tamilmarxist/stopsir.git

# Navigate to directory
cd stopsir

# Open dashboard in browser
start index.html  # Windows
open index.html   # macOS
xdg-open index.html  # Linux
```

### Navigating the Analysis

1. **Start Here**: Open `index.html` for state-wide overview
2. **Explore ACs**: Click any constituency in the navigation grid
3. **Sort Data**: Use the sortable table to filter by specific metrics
4. **Deep Dive**: Review individual AC reports for granular insights
5. **Cross-Reference**: Compare multiple ACs to identify regional patterns

---

## 💡 How to Use This Analysis

### For Researchers
- **Data Export**: Extract data from tables using browser developer tools
- **Pattern Analysis**: Compare deletion rates across urban vs rural areas
- **Correlation Studies**: Cross-reference with census data, migration statistics
- **Validation**: Use mortality rates to verify deletion authenticity
- **Academic Study**: Cite this analysis for electoral roll research

### For Citizens
- **Your Constituency**: Find your AC's report to understand local deletions
- **Comparison**: Compare your AC's deletion rate with state average
- **Verification**: Check if deletion patterns match your local experience
- **Civic Engagement**: Use insights for RTI requests or electoral reform advocacy

### For Administrators
- **Quality Control**: Identify ACs with unusual deletion patterns for audit
- **Resource Allocation**: Direct verification resources to high-deletion areas
- **Process Improvement**: Use age/reason patterns to improve roll maintenance
- **Transparency**: Share this analysis to demonstrate electoral roll integrity

### For Journalists/Activists
- **Story Leads**: Investigate high-deletion constituencies
- **Data Journalism**: Create additional visualizations from the data
- **Ground Verification**: Visit top-deletion polling stations for on-ground reporting
- **Policy Questions**: Use patterns to question electoral authorities

---

## ⚠️ Important Disclaimers

- **Data Source**: Analysis based on publicly available electoral roll deletion data
- **Deletion Context**: High deletion rates don't automatically indicate malfeasance; legitimate causes include:
  - Urban redevelopment causing mass relocations
  - Aging demographics in certain areas
  - Historical data quality issues being corrected
- **Verification**: Ground truth verification recommended for anomalous patterns
- **Methodology Transparency**: All calculations and data transformations documented in generation scripts

---

## 🔍 Methodology

### Data Processing Pipeline

1. **Data Collection**: Electoral roll snapshots (January 2025, December 2025)
2. **Deletion Identification**: Compare rolls to identify deleted records
3. **Classification**: Map Tamil text to English categories:
   - Reasons: Deceased, Shifted, Missing, Duplicate
   - Gender: Male, Female, Transgender
   - Age: Binned into 5 life-stage groups
   - Relationship: Father, Husband, Mother, Other
4. **Aggregation**: AC-level and state-level summaries
5. **Visualization**: Interactive Plotly charts embedded in HTML

### Key Calculations

**Deletion Percentage**:
```
Total_Deleted_Pct = (Total_Deleted / Total_Considered) × 100
Total_Considered = Total_Deleted + Electors_Dec_2025
```

**Deviation**:
```
Deviation = (Electors_Dec_2025 + Total_Deleted) - Electors_Jan_2025
```
*Positive deviation indicates net roll growth despite deletions*

**Mortality Rate** (per gender):
```
Gender_Mortality_Rate = (Gender_Deceased_Count / Total_Gender_Considered) × 100
```

### Data Integrity Checks

Each AC report includes:
- Missing Reason count
- Missing Gender count
- Missing Age count
- Invalid Name count

Low values (<1%) indicate good data quality.

---

## 📝 Technical Details

### Technologies
- **Visualization**: Plotly.js (interactive charts)
- **Styling**: Custom CSS with responsive design
- **Interactivity**: JavaScript for table sorting and navigation
- **Data Format**: HTML embedded with JSON (no external dependencies for viewing)

### Browser Compatibility
- ✅ Chrome/Edge (Recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers (responsive design)

### Offline Usage
All visualization files are self-contained. Once downloaded, internet connection not required to view charts.

---

## 📧 Contact & Contributions

**Repository**: `https://github.com/tamilmarxist/stopsir.git`

For questions, additional analysis requests, or collaboration:
- Open an issue on GitHub
- Contributions welcome via pull requests
- Data corrections or updates can be submitted through issues

---

## 📜 License

This analysis is provided for public interest and research purposes.  
Data sourced from [official electoral roll sources].  
Visualizations and analysis methodology are open for reuse with attribution.

---

**Last Updated**: December 2025  
**Data Coverage**: All 234 Assembly Constituencies, Tamil Nadu  
**Analysis Period**: January 2025 → December 2025 Electoral Rolls  
**Dashboard Charts**: 20+ interactive visualizations  
**AC Report Charts**: 18+ visualizations per constituency  
**Total Reports**: 1 Dashboard + 234 AC Reports = 235 HTML files
