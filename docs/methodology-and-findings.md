# Methodology and Analytical Findings

## Project: CyberRisk Intelligence — Global Cybersecurity Threats (2015–2024)
**Author:** Alwin Meniens  
**Academic Context:** B.Com Finance student building analytical skills in ACCA, financial analysis, and Power BI Business Intelligence.

---

## 1. Project Background and Objective

Cyber risk has transitioned from an isolated IT operational concern into a principal financial solvency and enterprise risk management challenge. Financial institutions, multinational corporations, and critical infrastructure entities must continually quantify breach exposure, assess vulnerability patterns, and optimize defensive capital expenditure.

The primary objective of this project was to ingest 10 years of historical global cyber incident data (2015–2024), build an intuitive and responsive Power BI business intelligence dashboard, and uncover empirical patterns across:
1. Long-term financial losses and year-over-year variability.
2. Cross-industry risk concentration and sector vulnerability.
3. Geographic distribution of financial impact across global economies.
4. Threat vector prevalence (DDoS, Phishing, Ransomware, Malware, SQL Injection, Man-in-the-Middle).

---

## 2. Technical Methodology & ETL Pipeline

```mermaid
flowchart LR
    A["Raw Data (Kaggle CSV)<br/>3,000 Records"] --> B["Power Query / ETL<br/>Type Validation & Cleaning"]
    B --> C["Data Modeling (VertiPaq)<br/>Global_Cybersecurity_Threats"]
    C --> D["DAX Calculation Engine<br/>Measures & Aggregations"]
    D --> E["Power BI Dashboard<br/>Interactive Visuals & Slicers"]
```

### 2.1 Extraction & Transformation (ETL)
- **Data Ingestion:** The dataset (`Global_Cybersecurity_Threats_2015-2024.csv`) containing 3,000 incident rows was imported via Power Query.
- **Type Transformation:**
  - `Year` converted to integer values for chronological sorting and slicer bounding (2015 to 2024).
  - `Financial Loss (in Million $)` converted to Decimal Currency for continuous numerical aggregation.
  - `Incident Resolution Time (in Hours)` converted to floating decimal to allow granular average response time calculations.
  - Categorical attributes (`Country`, `Target Industry`, `Attack Type`, `Attack Source`, `Security Vulnerability Type`) standardized to text.

### 2.2 Analytical Measures (DAX Architecture)
Four core key performance indicators (KPIs) were modeled in DAX:
1. `Total Cybersecurity Incidents`: Count of all reported breach events.
2. `Total Financial Impact`: Aggregate financial loss across all incidents in millions of USD.
3. `Total Data Breached`: Aggregate volume of compromised user accounts / breach volume.
4. `Average Response Time`: Mean technical incident resolution time in hours.

---

## 3. Verified Analytical Findings

All findings below were mathematically calculated from the actual dataset (3,000 observations) and cross-verified against the dashboard visuals.

### Finding 1: IT and Banking Absorb ~31.4% of Global Financial Losses
- **Metrics & Verified Values:**
  - Total Global Financial Loss across all 7 sectors: **$151,478.91M ($151.48 Billion)**.
  - Information Technology (IT): **$24,809.83M (16.38%)** across 478 incidents.
  - Banking: **$22,772.39M (15.03%)** across 445 incidents.
  - Combined IT & Banking share: **$47,582.22M (31.41%)** across 923 incidents.
- **Comparison & Pattern:**
  While remaining industries (Government, Retail, Healthcare, Telecommunications, and Education) each sustained approximately $20B–$21.2B in damages, IT and Banking stand out as high-value targets. IT alone experienced 14.1% higher financial loss than the cross-industry average ($21.64B).
- **Business & Financial Relevance:**
  IT and Banking handle highly liquid financial capital, sensitive personal identification records, and mission-critical digital infrastructure. For risk managers and financial underwriters, this underscores the necessity of tiered cyber insurance premiums and targeted capital allocations toward perimeter defenses and zero-trust authentication in these two sectors.
- **Caveats & Limitations:**
  The dataset records reported direct losses. In highly regulated sectors like Banking, regulatory disclosure mandates are more stringent than in education or retail, which may introduce mild reporting bias in observable incident counts.

---

### Finding 2: High Financial Impact Spread Across Developed Jurisdictions (UK, Germany, Brazil)
- **Metrics & Verified Values:**
  - United Kingdom (UK) ranks highest in cumulative financial loss: **$16,502.99M ($16.50 Billion)** across 321 incidents (average of $51.41M per incident).
  - Germany: **$15,793.24M** (291 incidents, average of $54.27M per incident).
  - Brazil: **$15,782.62M** (310 incidents, average of $50.91M per incident).
  - China recorded the lowest total among the top 10 at **$13,714.47M** (281 incidents).
- **Comparison & Pattern:**
  The total financial impact across all 10 tracked countries shows remarkable geographic breadth, with the top country (UK) representing only 10.9% of global losses, and each country in the top 10 absorbing between $13.7B and $16.5B.
- **Business & Financial Relevance:**
  Cyber threats are truly borderless. Multinational enterprises cannot rely solely on localized regional defenses. High-GDP economies face severe monetary exposure due to the concentration of multinational headquarters, complex cloud supply chains, and extensive digital transaction networks.
- **Caveats & Limitations:**
  The dataset samples 10 prominent countries with approximately 280 to 320 records each. It does not normalize losses against national GDP or aggregate national digital transaction volume.

---

### Finding 3: Threat Vector Uniformity Highlights Multi-Pronged Attack Surfaces
- **Metrics & Verified Values:**
  - Distributed Denial of Service (DDoS): **531 incidents (17.70%)**
  - Phishing: **529 incidents (17.63%)**
  - SQL Injection: **503 incidents (16.77%)**
  - Ransomware: **493 incidents (16.43%)**
  - Malware: **485 incidents (16.17%)**
  - Man-in-the-Middle (MitM): **459 incidents (15.30%)**
- **Comparison & Pattern:**
  No single attack type dominates the threat ecosystem; the distribution across all six threat vectors is exceptionally balanced, ranging between 15.3% and 17.7%.
- **Business & Financial Relevance:**
  From a corporate governance and ACCA internal audit perspective, organizations cannot concentrate their cybersecurity budget on a single defense vector (e.g., solely deploying anti-phishing training or solely investing in DDoS mitigation appliances). Enterprise resilience requires a balanced, defense-in-depth framework spanning network integrity, database hardening (SQL injection), perimeter filtering (DDoS), and human risk management (phishing simulations).
- **Caveats & Limitations:**
  Synthetic or curated benchmark datasets frequently display near-uniform categorical distributions to facilitate unbiased machine learning benchmarking. Real-world incident frequencies may exhibit greater seasonal spikes and targeted campaigns during specific macroeconomic or geopolitical events.

---

## 4. Metric Unit Investigation & Interpretation Nuance

A critical responsibility of a data analyst is unit precision. Two specific metrics in the dashboard require clear documentation:

### 4.1 Financial Loss Unit Representation
- **Dataset Column Definition:** `Financial Loss (in Million $)`
- **Mathematical Sum:** `151,478.91` (representing 151,478.91 million dollars = **$151.48 Billion USD**).
- **Dashboard Display:** The KPI card displays `151.48K`. In Power BI default formatting, the value `151,478.91` formatted with automated thousand-display units appends `K`. 
- **Analytical Clarity:** Executive audiences should understand that `151.48K [Million $]` equals **$151.48 Billion**. In future revisions, creating an explicit calculated measure `[Total Financial Impact ($Bn)] = DIVIDE([Total Financial Impact], 1000, 0)` with `$#,##0.00 "B"` formatting eliminates potential reader ambiguity.

### 4.2 Data Breached / Disrupted Users KPI
- **Dashboard Card Value:** `2bn`.
- **Dataset Analysis:** The aggregate sum of `[Number of Affected Users]` equals **1,514,052,409** (~1.51 billion individuals/records). Power BI's automatic single-digit billion formatting rounds 1.51 billion up to `2bn`.
- **Analytical Clarity:** While visually compact, configuring decimal precision to display `1.51B` provides more accurate reporting for audit and regulatory compliance.

---

## 5. Limitations and Analytical Caveats

1. **Static Benchmark vs. Live Telemetry:** The dataset represents a historical, cross-sectional benchmark rather than real-time SIEM (Security Information and Event Management) telemetry.
2. **Even Categorical Dispersion:** The uniform incident distribution across countries (~300 records each) and attack vectors (~500 records each) reflects curated sampling rather than unstructured real-world incident volatility.
3. **PBIX Internal DataModel:** The `.pbix` VertiPaq database utilizes XPress9 proprietary compression, meaning internal DAX expression strings are embedded in the proprietary model schema rather than plain-text XML. All visual bindings and field references were directly verified via the report visual definitions.
