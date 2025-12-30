# Analysis on SIR Deletion

Tamil Nadu Electoral Roll Deletion Analysis - An in-depth examination of voter deletions from the Special Intensive Revision (SIR) process across all 234 Assembly Constituencies.

## 📊 Overview

This repository contains a comprehensive analysis of voter deletions from the Tamil Nadu electoral rolls, examining patterns and statistics across all 234 Assembly Constituencies (ACs). The analysis focuses on the **Special Intensive Revision (SIR)** deletion process that occurred between electoral roll updates.

### Key Features

- **Interactive Dashboard** (`index.html`) - Main visualization dashboard with summary statistics and charts
- **234 AC-specific Reports** (`ac_reports/`) - Detailed HTML reports for each Assembly Constituency
- **Visual Analytics** - Color-coded heatmaps showing deletion percentages across constituencies
- **Sortable Data Tables** - Interactive tables for detailed data exploration

## 🗂️ Repository Structure

```
├── index.html              # Main dashboard with statewide analysis
└── ac_reports/             # Individual constituency reports
    ├── ac_1_report.html   # கும்மிடிபூண்டி (Gummidipoondi)
    ├── ac_2_report.html   # பொன்னேரி (Ponneri)
    ├── ...
    └── ac_234_report.html # விளாத்திகுளம் (Vilathikulam)
```

## 📈 Dashboard Features

The main dashboard (`index.html`) provides:

1. **Constituency Navigation Grid** - Quick access to all 234 AC reports with color-coded deletion percentages
2. **Summary Statistics** - Key metrics on deletions, demographics, and geographic insights
3. **Visualizations**:
   - Deletion percentage distribution charts
   - Geographic heatmaps
   - Demographic breakdowns
   - Time-series analysis
4. **Interactive Data Table** - Sortable table with detailed AC-wise statistics

### Deletion Percentage Color Coding

The constituency grid uses a gradient color scheme to highlight deletion severity:
- 🟢 **Green** (0-10%): Lower deletion rates
- 🟡 **Yellow-Orange** (10-20%): Moderate deletion rates  
- 🟠 **Orange** (20-30%): High deletion rates
- 🔴 **Red** (30%+): Very high deletion rates

## 🏛️ Assembly Constituency Reports

Each AC report (`ac_reports/ac_[number]_report.html`) includes:

- **Constituency Profile** - Name, number, and key demographics
- **Deletion Statistics** - Total deletions, percentage, and comparisons
- **Data Breakdowns** - Age groups, gender distribution, polling booth analysis
- **Detailed Tables** - Comprehensive data tables for in-depth review

### Constituencies with Highest Deletion Rates

Based on the analysis, some constituencies show significantly higher deletion percentages:

1. **AC 21 - அண்ணா நகர் (Anna Nagar)**: 42.18%
2. **AC 20 - ஆயிரம் விளக்கு (Thousand Lights)**: 40.68%
3. **AC 14 - வில்லிவாக்கம் (Villivakkam)**: 40.65%
4. **AC 18 - துறைமுகம் (Harbour)**: 38.64%
5. **AC 16 - எழும்பூர் (Egmore)**: 37.91%

## 🚀 Usage

### Viewing the Dashboard

1. **Online**: This repository can be deployed to GitHub Pages for online access
2. **Local**: Simply open `index.html` in any modern web browser

```bash
# Clone the repository
git clone https://github.com/tamilmarxist/stopsir.git

# Open the dashboard
cd stopsir
# Open index.html in your browser
```

### Navigating the Analysis

- **Main Dashboard**: Start at `index.html` for the overview
- **Constituency Reports**: Click any constituency in the navigation grid or browse the `ac_reports/` folder
- **Data Exploration**: Use the sortable table to filter and analyze specific metrics

## 📊 Data Insights

The analysis reveals:

- **Statewide deletion patterns** across urban vs rural constituencies
- **Geographic hotspots** with unusually high deletion rates  
- **Demographic trends** in deleted voter profiles
- **Assembly Constituency comparisons** for contextual understanding

## ⚠️ Important Notes

- This analysis is based on publicly available electoral roll data
- Deletion percentages represent the proportion of voters removed during SIR
- Individual constituency patterns may reflect various administrative factors
- Data accuracy depends on official electoral roll sources

## 🔍 Methodology

The analysis examines:
1. Electoral roll snapshots before and after SIR
2. Voter deletion counts per Assembly Constituency
3. Percentage calculations relative to total registered voters
4. Geographic and demographic segmentation

## 📝 License

This project contains analysis of publicly available electoral data. Please refer to Election Commission regulations for data usage guidelines.

## 🤝 Contributing

This is an official analysis repository. For inquiries or collaboration, please contact the repository maintainers.

## 📧 Contact

For questions or additional information about this analysis, please open an issue in this repository.

---

**Last Updated**: December 2025  
**Data Source**: Tamil Nadu Electoral Rolls - Special Intensive Revision Process  
**Coverage**: All 234 Assembly Constituencies of Tamil Nadu
