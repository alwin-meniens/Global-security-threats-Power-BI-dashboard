# Data Dictionary

## Project: CyberRisk Intelligence — Global Cybersecurity Threats (2015–2024)
**Author:** Alwin Meniens  
**Source Dataset:** [Global Cybersecurity Threats (2015–2024)](https://www.kaggle.com/datasets/atharvasoundankar/global-cybersecurity-threats) by Atharva Soundankar  
**License:** CC0 1.0 Universal (Public Domain)  
**File Format:** Comma-Separated Values (`.csv`)  
**Record Count:** 3,000 incident records across 10 years (2015–2024)

---

### Entity: `Global_Cybersecurity_Threats_2015-2024`

| Column Name | Data Type (Power BI) | Storage Type | Description | Example Values / Domain | Constraints & Business Rules |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `Country` | Text | String | Country where the incident was detected and reported | UK, Germany, Brazil, Australia, Japan, France, USA, Russia, India, China | 10 distinct sovereign jurisdictions represented |
| `Year` | Whole Number | Int64 | Calendar year of the reported security event | 2015, 2016, 2017, ..., 2024 | Range: 2015 to 2024 (10 consecutive years) |
| `Attack Type` | Text | String | Primary classification of cyber attack vector | DDoS, Phishing, SQL Injection, Ransomware, Malware, Man-in-the-Middle | 6 threat categories; relatively even distribution (~15%–18% each) |
| `Target Industry` | Text | String | Industry sector of the affected enterprise or organization | IT, Banking, Government, Retail, Healthcare, Telecommunications, Education | 7 primary economic sectors |
| `Financial Loss (in Million $)` | Decimal Number (Currency) | Float64 | Direct and indirect monetary damage caused by the incident, denominated in Millions of USD ($M) | 80.53, 62.19, 38.65, 41.44 | Min: ~$0.1M, Max: ~$100M per incident; Total dataset sum: $151,478.91M ($151.48B) |
| `Number of Affected Users` | Whole Number | Int64 | Scale of impacted individuals, customer accounts, or employee records compromised | 773,169; 295,961; 605,895 | Total dataset sum: 1,514,052,409 (~1.51B users) |
| `Attack Source` | Text | String | Attributed profile or classification of the threat actor | Hacker Group, Nation-state, Insider, Unknown | Threat actor categorization |
| `Security Vulnerability Type` | Text | String | Systemic weakness or entry point exploited to breach defenses | Unpatched Software, Weak Passwords, Social Engineering, Zero-day | Key vulnerability categorization |
| `Defense Mechanism Used` | Text | String | Security controls deployed at the perimeter or endpoint | VPN, Firewall, Antivirus, AI-based Detection | Defense mitigation profile |
| `Incident Resolution Time (in Hours)` | Whole Number / Decimal | Float64 | Elapsed time from incident containment to complete technical resolution | 63, 71, 20, 7 | Mean resolution time: 36.48 hours (~1.52 days) |

---

### Column Renaming & Model Equivalences

In the Power BI data model:
1. **`Financial Loss (in Million $)`**: Summed by `[Total Financial Impact]`. Displayed in dashboard KPI as `151.48K` (meaning 151.48 thousand million dollars, or $151.48 Billion).
2. **`Number of Affected Users` vs `Data Breached (GB)`**:
   - In the provided raw dataset file, user disruption is stored in `[Number of Affected Users]` (totaling 1.51 billion records, displayed as `2bn` rounded on the card).
   - In some academic literature or Kaggle iterations, an analogous metric is labeled `Data Breached (GB)`. Both mappings are recorded in [`dax/measures.dax`](../dax/measures.dax).
3. **`Incident Resolution Time (in Hours)`**: Represented on the dashboard as `Average Response Time` (mean = 36.48 hours).

---

### Data Hygiene & Validation Notes
- **Null Values:** Zero null or missing values across the 3,000 incident rows.
- **Completeness:** Each year has between 263 and 319 recorded events, maintaining balanced sample coverage across the 10-year analysis horizon.
- **Outliers:** Losses are distributed smoothly without negative figures or single-event distortions.
