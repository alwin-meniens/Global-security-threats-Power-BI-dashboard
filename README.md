# CyberRisk Intelligence — Global Cybersecurity Threats (2015–2024)

[![Power BI](https://img.shields.io/badge/Power_BI-Desktop-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Dataset: Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/atharvasoundankar/global-cybersecurity-threats)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)
[![Documentation: Methodology](https://img.shields.io/badge/Docs-Methodology_&_Findings-blue?logo=markdown)](docs/methodology-and-findings.md)
[![Documentation: Data Dictionary](https://img.shields.io/badge/Docs-Data_Dictionary-teal?logo=markdown)](docs/data-dictionary.md)
[![DAX Measures](https://img.shields.io/badge/DAX-Measures_Reference-purple?logo=dax)](dax/measures.dax)

An interactive Power BI dashboard exploring cybersecurity incidents, financial losses, attack patterns, and incident response times across countries and industries.

---

### 📑 Quick Links & Documentation
- 📊 **[Interactive Dashboard Screenshot](dashboard/cyberrisk-dashboard.png)**
- 📐 **[DAX Measures & Implementation (`dax/measures.dax`)](dax/measures.dax)**
- 🔍 **[Detailed Methodology & Findings (`docs/methodology-and-findings.md`)](docs/methodology-and-findings.md)**
- 📖 **[Data Dictionary & Schema (`docs/data-dictionary.md`)](docs/data-dictionary.md)**
- 💾 **[Power BI File (`cyberrisk-intelligence-dashboard.pbix`)](cyberrisk-intelligence-dashboard.pbix)**

---

## 📊 Dashboard Preview

[![Dashboard Preview](dashboard/cyberrisk-dashboard.png)](dashboard/cyberrisk-dashboard.png)

---

## 🎯 Project Overview

Cybersecurity incidents can create significant financial and operational risks for organisations. This project uses business intelligence techniques to explore a dataset of 3,000 recorded incidents spanning 2015–2024.

The objective is to transform structured data into an interactive dashboard that makes it easier to compare financial losses, explore attack patterns, and examine incident response times.

### Project Objectives
- Analyse financial losses over time.
- Compare recorded losses across countries and industries.
- Explore the distribution of cybersecurity attack types.
- Summarise key metrics using KPI cards.
- Practise data analysis, DAX, and dashboard design.

---

## 🛠️ Tools & Technologies

| Tool | Application |
| :--- | :--- |
| **Microsoft Power BI Desktop** | Dashboard development and visualisation |
| **DAX** | Measures and aggregations |
| **Power Query** | Data preparation and transformation |
| **GitHub** | Project documentation and version control |

---

## 📈 Dashboard Features

### KPI Cards
- **Total Cybersecurity Incidents:** Number of records analysed (3,000 incidents).
- **Total Financial Impact:** Aggregate recorded financial losses ($151.48B across all incidents).
- **Total Data Breached:** Aggregate of the selected dataset's breach-related measure.
- **Average Response Time:** Average recorded incident response or resolution time (36.48 hours).

### Analytical Visuals
- **Financial Impact by Year:** Compares recorded financial losses from 2015 to 2024.
- **Top 10 Countries by Financial Loss:** Ranks countries by aggregate recorded losses.
- **Financial Loss by Industry:** Compares losses across industry categories.
- **Cybersecurity Threat Distribution:** Shows the relative frequency of recorded attack types.
- **Year Range Slicer:** Filters the dashboard by year.

---

## 🔍 Key Findings

The following findings are reported from the selected dataset:

1. **IT and Banking record the highest industry losses:**  
   IT records approximately **$24.81 billion** and Banking approximately **$22.77 billion** in aggregate financial losses.
2. **The UK has the highest recorded country-level loss:**  
   The UK records approximately **$16.50 billion**, followed by Germany at **$15.79 billion** and Brazil at **$15.78 billion**.
3. **DDoS and Phishing are the most frequent attack types:**  
   They account for approximately **17.70%** and **17.63%** of the recorded incidents, respectively.

*Interpretation note: These are patterns in the selected dataset, not necessarily representative estimates of real-world cybersecurity risks. Validate the calculations against the final Power BI model before publication. For full breakdown and statistical analysis, refer to [Methodology & Findings](docs/methodology-and-findings.md).*

---

## 📐 DAX Measures

The dashboard uses DAX to calculate its core metrics. For the full code and extended calculations, see [`dax/measures.dax`](dax/measures.dax).

### Total Financial Impact
```dax
Total Financial Impact = 
SUM( 'Global_Cybersecurity_Threats_2015-2024'[Financial Loss (in Million $)] )
```

### Total Cybersecurity Incidents
```dax
Total Cybersecurity Incidents = 
COUNTROWS('Global_Cybersecurity_Threats_2015-2024')
```

### Total Data Breached
```dax
Total Data Breached = 
SUM( 'Global_Cybersecurity_Threats_2015-2024'[Data Breached (GB)] )
```

### Average Response Time
Use the response-time column name from the actual Power BI model:
```dax
Average Response Time = 
AVERAGE( 'Global_Cybersecurity_Threats_2015-2024'[Response Time (Hours)] )
```

*Verify all column names and units against the final model. In particular, confirm what the data-breached measure represents before describing it as affected users or breached records. If using the unedited source column, response time maps to `[Incident Resolution Time (in Hours)]` and user impact maps to `[Number of Affected Users]`.*

---

## 🔬 Methodology & Limitations

- The analysis uses the selected dataset's recorded observations and field definitions.
- Financial-loss totals depend on the units and reporting assumptions used in the source data.
- The dataset's country and attack-type distributions may reflect curated sampling.
- The analysis is exploratory; it does not predict future attacks or establish causal relationships.
- Results should not be generalised to all real-world cybersecurity incidents without additional evidence.

For in-depth analysis and data schema:
- 📑 **[Methodology & Verified Findings](docs/methodology-and-findings.md)**
- 📖 **[Data Dictionary](docs/data-dictionary.md)**

---

## 📚 Dataset & Attribution

- **Dataset:** [Global Cybersecurity Threats (2015–2024)](https://www.kaggle.com/datasets/atharvasoundankar/global-cybersecurity-threats)
- **Author:** Atharva Soundankar
- **Platform:** Kaggle
- **Licence:** Reported as [CC0: Public Domain](http://creativecommons.org/publicdomain/zero/1.0/); verify the original dataset licence before redistributing the data.

---

## 💡 What I Learned

- Building KPI cards and analytical visuals in Power BI.
- Creating DAX measures for aggregation and comparison.
- Exploring financial-loss patterns across countries and industries.
- Communicating analytical findings through dashboard design.
- Documenting data definitions, assumptions, and limitations.

---

## 🚀 Future Improvements

- Add interactive filters for country, attack type, and target industry.
- Improve KPI formatting and unit consistency.
- Add year-over-year comparisons and trend measures.
- Introduce drill-through analysis for selected countries and industries.

---

## ▶️ How to View the Project

1. Review the dashboard screenshot in the [`dashboard/`](dashboard/cyberrisk-dashboard.png) folder.
2. Download or open the [`.pbix` file](cyberrisk-intelligence-dashboard.pbix) in Power BI Desktop.
3. Consult the [DAX measures file](dax/measures.dax) and documentation files in [`docs/`](docs/) for technical details.

---

## 👤 Author

**Alwin Meniens**  
B.Com Finance student interested in finance, business intelligence, data analytics, and AI.  
[![GitHub](https://img.shields.io/badge/GitHub-Profile-181717?logo=github&logoColor=white)](https://github.com/alwin-meniens)
