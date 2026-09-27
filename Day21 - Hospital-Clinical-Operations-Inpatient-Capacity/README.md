<div align="center">



\# 🏥 Day 21: Hospital Clinical Operations \& Inpatient Capacity Command



\*\*Clinical Throughput, Bed Utilization Diagnostics, Diagnostic Acuity \& Healthcare Billing Economics\*\*



\[!\[Power BI](https://img.shields.io/badge/Power\_BI-Desktop-F2C811?style=for-the-badge\&logo=powerbi\&logoColor=black)](https://powerbi.microsoft.com/)

\[!\[DAX](https://img.shields.io/badge/DAX-Advanced\_Healthcare\_Analytics-0078D4?style=for-the-badge\&logo=microsoftexcel\&logoColor=white)](https://learn.microsoft.com/en-us/dax/)

\[!\[Domain](https://img.shields.io/badge/Domain-Healthcare\_\&\_Hospital\_Operations-0284C7?style=for-the-badge)](https://en.wikipedia.org/wiki/Health\_administration)

\[!\[Dataset](https://img.shields.io/badge/Dataset-Healthcare\_Dataset-20BEFF?style=for-the-badge\&logo=kaggle\&logoColor=white)](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)



<br/>



!\[Dashboard Preview](dashboard\_preview.png)



</div>



\---



\## 📁 Repository \& File Manifest



```text

Day21 - Hospital-Clinical-Operations-Inpatient-Capacity/

│

├── 📊 Hospital\_Clinical\_Operations\_Capacity.pbix  # Production Power BI Application \& Data Model

├── 📄 healthcare\_dataset.csv                     # Inpatient Clinical Dataset (55,500 admissions)

├── 🖼️ dashboard\_preview.png                      # High-Resolution Executive Dashboard Screenshot

└── 📝 README.md                                 # Full Project Architecture \& Technical Documentation

```



\### File Details \& Data Footprint

| File Name | File Type | File Size | Description |

| :--- | :---: | :---: | :--- |

| \*\*`Hospital\_Clinical\_Operations\_Capacity.pbix`\*\* | Power BI Report | \~3.8 MB | Inpatient operations model, complete DAX measure suite, UI containers, and responsive visuals. |

| \*\*`healthcare\_dataset.csv`\*\* | CSV Data Source | 6.4 MB | 55,500 audited hospital inpatient admissions spanning 2019 through 2024. |

| \*\*`dashboard\_preview.png`\*\* | Image (PNG) | \~1.2 MB | High-resolution canvas view used for portfolio documentation and social presentation. |

| \*\*`README.md`\*\* | Markdown Document | \~14 KB | Comprehensive operational problem statement, clinical benchmarks, DAX catalog, and reproduction steps. |



\---



\## 📌 Executive Summary



This clinical operations command center monitors inpatient throughput, bed occupancy efficiency, and healthcare revenue cycle metrics. Evaluating \*\*55,500 verified patient admissions\*\* across six chronic diagnostic categories totaling \*\*$1.42B in gross billing charges\*\*, the dashboard identifies inpatient length of stay (ALOS) patterns, diagnostic acuity distribution, and commercial insurance coverage realization across hospital networks.



> \[!IMPORTANT]

> \*\*Operational Capacity Takeaway:\*\* Hospital inpatient throughput averages \*\*15.51 Days ALOS\*\* across \*\*860,750 cumulative bed days occupied\*\*, with an average billing charge of \*\*$25,539.32 per admission\*\*. Furthermore, \*\*33.56% of admissions (18,627 patients)\*\* present abnormal laboratory/imaging results, requiring higher intensive care staffing, specialized nursing, and continuous bed monitoring.



\---



\## 📊 Core Clinical \& Operational Benchmarks



| Strategic Operational Metric | Baseline Portfolio Benchmark | Clinical \& Operational Significance |

| :--- | :---: | :--- |

| \*\*Total Inpatient Admissions\*\* | \*\*`55,500` Admissions\*\* | Audited multi-year hospital inpatient admissions (2019–2024). |

| \*\*Gross Healthcare Billing\*\* | \*\*`$1,417,432,043.40` ($1.42B)\*\* | Total hospital procedural, room, and clinical charges billed. |

| \*\*Average Length of Stay (ALOS)\*\* | \*\*`15.51` Days\*\* | Mean inpatient hospital bed occupancy duration per stay. |

| \*\*Total Bed Days Occupied\*\* | \*\*`860,750` Bed Days\*\* | Cumulative inpatient bed utilization across hospital wards. |

| \*\*Average Cost per Admission\*\* | \*\*`$25,539.32`\*\* | Mean financial billing realized per inpatient episode. |

| \*\*Average Cost per Bed Day\*\* | \*\*`$1,646.74` / Day\*\* | Mean financial realization generated per occupied bed day. |

| \*\*Abnormal Diagnostic Rate %\*\* | \*\*`33.56%` (18,627 Patients)\*\* | Patients presenting high-acuity lab/imaging diagnostic results. |

| \*\*Emergency Intake Velocity\*\* | \*\*`32.92%` (18,269 Admissions)\*\* | Unscheduled acute emergency intake requiring immediate bed assignment ($465.81M). |

| \*\*Elective Intake Volume\*\* | \*\*`33.61%` (18,655 Admissions)\*\* | Scheduled procedural admissions ($477.61M). |

| \*\*Top Billing Medical Condition\*\* | \*\*Diabetes (`$238.54M`)\*\* | Highest aggregate medical condition billing expenditure (9,304 patients). |

| \*\*Longest Inpatient Duration\*\* | \*\*Asthma (`15.70` Days ALOS)\*\* | Pulmonary conditions drive the highest average bed day occupancy. |

| \*\*Primary Payor Carrier\*\* | \*\*Cigna (`$287.14M`)\*\* | Largest insurance billing allocation across 11,249 admissions. |



\---



\## 🧱 Data Architecture \& Feature Engineering



The underlying model combines a cleaned clinical admissions table (`HospitalAdmissions`) linked directly to an automated continuous DAX Calendar table (`DimDate`).



```

&#x20;                 ┌───────────────────────────────┐

&#x20;                 │            DimDate            │

&#x20;                 │   (Continuous Date Matrix)    │

&#x20;                 └───────────────┬───────────────┘

&#x20;                                 │ 1

&#x20;                                 │ \*

&#x20;                 ┌───────────────┴───────────────┐

&#x20;                 │      HospitalAdmissions       │

&#x20;                 │    (55,500 Patient Records)   │

&#x20;                 └───────────────────────────────┘

```



\### 1. Data Schema \& Field Reference

| Field Name | Type | Description | Engineering Transformation |

| :--- | :---: | :--- | :--- |

| `Name` | Text | Patient Full Name | Capitalized each word to correct inconsistent raw text casing |

| `Age` | Whole Number | Patient Chronological Age (13–89) | Segmented into 4 Demographic Age Bands |

| `Gender` | Text | Patient Gender (Male / Female) | Demographic slicing dimension |

| `Blood Type` | Text | ABO/Rh Blood Group (8 types) | Biological classification field |

| `Medical Condition` | Text | Primary Admitting Diagnosis | 6 chronic conditions (Cancer, Diabetes, Asthma, etc.) |

| `Date of Admission` | Date | Hospital Inpatient Admission Date | Converted to discrete Date; linked to `DimDate\[Date]` (1:\*) |

| `Discharge Date` | Date | Patient Discharge Date | Standardized to discrete Date format |

| `Doctor` | Text | Attending Medical Physician | Clinical operational attribution |

| `Hospital` | Text | Admitting Hospital Facility | Multi-facility operational footprint |

| `Insurance Provider` | Text | Primary Payor Carrier | 5 carriers (Cigna, Medicare, Blue Cross, UnitedHealthcare, Aetna) |

| `Billing Amount` | Decimal | Total Billed Amount ($) | Core financial measure |

| `Room Number` | Whole Number | Assigned Inpatient Bed/Room Number | Operational facility tracking |

| `Admission Type` | Text | Admission Severity | Emergency, Urgent, Elective |

| `Medication` | Text | Primary Prescribed Inpatient Drug | 5 core pharmaceuticals |

| `Test Results` | Text | Diagnostic Acuity Finding | Normal, Inconclusive, Abnormal |

| `Length of Stay` | Whole Number | Computed Hospital Stay (Days) | `Duration.Days(\[Discharge Date] - \[Date of Admission])` |

| `Age Group` | Text | Age Demographic Bracket | `< 30`, `31 - 45`, `46 - 60`, `61+` |



\### 2. Power Query M Transformations

```powerquery

// 1. Text Normalization: Fix inconsistent capitalization

= Table.TransformColumns(#"Promoted Headers", {{"Name", Text.Proper, type text}})



// 2. Length of Stay Duration Calculation (Discharge Date - Admission Date)

= Table.AddColumn(#"Changed Type", "Length of Stay", each Duration.Days(\[Discharge Date] - \[Date of Admission]), Int64.Type)



// 3. Demographic Age Segmentation

= Table.AddColumn(#"Added LOS", "Age Group", each 

&#x20;   if \[Age] <= 30 then "< 30"

&#x20;   else if \[Age] <= 45 then "31 - 45"

&#x20;   else if \[Age] <= 60 then "46 - 60"

&#x20;   else "61+", type text)

```



\---



\## 📐 Complete DAX Measure Library



All clinical, financial, and throughput measures are organized within a dedicated `\_Measures` table:



\### 1. Inpatient Volume \& Bed Capacity Measures



```dax

// Total audited inpatient hospital stays

Total Admissions = 

COUNTROWS(HospitalAdmissions)

```



```dax

// Average inpatient bed duration per stay (Days)

Average Length of Stay = 

AVERAGE(HospitalAdmissions\[Length of Stay])

```



```dax

// Cumulative inpatient bed days occupied across hospital network

Total Bed Days Occupied = 

SUM(HospitalAdmissions\[Length of Stay])

```



\### 2. Healthcare Financial \& Billing Measures



```dax

// Gross billed inpatient revenue across all conditions

Total Billing Amount = 

SUM(HospitalAdmissions\[Billing Amount])

```



```dax

// Mean financial billing realized per inpatient admission

Avg Billing per Admission = 

DIVIDE(

&#x20;   \[Total Billing Amount], 

&#x20;   \[Total Admissions], 

&#x20;   0

)

```



```dax

// Mean billing realized per inpatient bed day occupied

Avg Cost per Bed Day = 

DIVIDE(

&#x20;   \[Total Billing Amount], 

&#x20;   \[Total Bed Days Occupied], 

&#x20;   0

)

```



\### 3. Clinical Acuity \& Outcome Measures



```dax

// Inpatient admissions resulting in abnormal diagnostic findings

Abnormal Test Results = 

CALCULATE(

&#x20;   \[Total Admissions],

&#x20;   HospitalAdmissions\[Test Results] = "Abnormal"

)

```



```dax

// Proportion of patient diagnostics flagged as abnormal

Abnormal Test Rate % = 

DIVIDE(

&#x20;   \[Abnormal Test Results], 

&#x20;   \[Total Admissions], 

&#x20;   0

)

```



```dax

// Percentage of admissions originating from acute emergency intake

Emergency Admission Rate % = 

DIVIDE(

&#x20;   CALCULATE(\[Total Admissions], HospitalAdmissions\[Admission Type] = "Emergency"),

&#x20;   \[Total Admissions],

&#x20;   0

)

```



```dax

// Percentage of scheduled elective clinical procedures

Elective Admission Rate % = 

DIVIDE(

&#x20;   CALCULATE(\[Total Admissions], HospitalAdmissions\[Admission Type] = "Elective"),

&#x20;   \[Total Admissions],

&#x20;   0

)

```



```dax

// Percentage of urgent unscheduled clinical procedures

Urgent Admission Rate % = 

DIVIDE(

&#x20;   CALCULATE(\[Total Admissions], HospitalAdmissions\[Admission Type] = "Urgent"),

&#x20;   \[Total Admissions],

&#x20;   0

)

```



\---



\## 🎯 Clinical Condition \& Throughput Analysis



\### 1. Diagnostic Condition Inpatient Breakdown

| Medical Condition | Admissions | ALOS (Days) | Total Billing ($) | Avg Cost / Stay | Abnormal Rate % | Operational Focus |

| :--- | :---: | :---: | :---: | :---: | :---: | :--- |

| \*\*Arthritis\*\* | 9,308 | 15.52 | $237.33M | $25,497.33 | 34.25% | Joint replacement rehab \& post-acute step-down care. |

| \*\*Diabetes\*\* | 9,304 | 15.42 | \*\*$238.54M\*\* | $25,638.41 | 34.05% | Glycemic management \& diabetic wound care pathways. |

| \*\*Hypertension\*\* | 9,245 | 15.46 | $235.72M | $25,497.10 | 32.58% | Cardiovascular telemetry \& medication titration. |

| \*\*Obesity\*\* | 9,231 | 15.46 | $238.21M | \*\*$25,805.97\*\* | 33.93% | Bariatric complications \& multi-specialty consults. |

| \*\*Cancer\*\* | 9,227 | 15.50 | $232.17M | $25,161.79 | 33.79% | Oncology inpatient cycles \& surgical recovery protocols. |

| \*\*Asthma\*\* | 9,185 | \*\*15.70\*\* | $235.46M | $25,635.25 | 32.76% | Respiratory therapy \& chronic pulmonary stabilization. |



\### 2. Payor Provider Billing Realization

| Insurance Carrier | Admissions | Total Billed Amount ($) | Billing Share % | Avg Cost / Admission | Payor Status |

| :--- | :---: | :---: | :---: | :---: | :--- |

| \*\*Cigna\*\* | 11,249 | \*\*$287.14M\*\* | 20.26% | $25,525.77 | Commercial Carrier Leader |

| \*\*Medicare\*\* | 11,154 | \*\*$285.72M\*\* | 20.16% | $25,615.99 | Public Government Payor |

| \*\*Blue Cross\*\* | 11,059 | \*\*$283.25M\*\* | 19.98% | $25,613.01 | Regional Commercial Network |

| \*\*UnitedHealthcare\*\* | 11,125 | \*\*$282.45M\*\* | 19.93% | $25,389.17 | National Commercial Network |

| \*\*Aetna\*\* | 10,913 | \*\*$278.86M\*\* | 19.67% | $25,553.29 | Private Commercial Payor |



\---



\## 💡 Strategic Executive Insights



1\. \*\*Balanced Chronic Disease Bed Occupancy:\*\* Inpatient admissions across all six chronic conditions are distributed evenly (between 9,185 and 9,308 admissions each), reflecting a hospital system managing broad, consistent community disease burdens rather than sharp isolated outbreaks.

2\. \*\*Elevated Diagnostic Acuity (33.56% Abnormal Rate):\*\* More than 18,600 admissions presented abnormal test findings, representing over $475.7M in clinical billing. Accelerating turnaround times on laboratory and pathology results directly reduces patient holding time and curbs unnecessary inpatient bed occupancy.

3\. \*\*Payor Mix Parity \& Revenue Stability:\*\* Billing volume is distributed across all five major payors (ranging between $278.9M and $287.1M each). This parity protects the hospital network from single-carrier reimbursement shocks or unilateral contract renegotiations.



\---



\## 📥 Dataset Source \& Setup Guide



\* \*\*Primary Source:\*\* \[Kaggle - Healthcare Dataset by Prasad Patil](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)

\* \*\*File Used:\*\* `healthcare\_dataset.csv` (55,500 rows × 15 columns)



\### Reproduction Steps:

1\. Clone or download this project repository:

&#x20;  ```bash

&#x20;  git clone \[https://github.com/yusufehtesham29/30-Days-Of-Power-BI.git](https://github.com/yusufehtesham29/30-Days-Of-Power-BI.git)

&#x20;  cd "Day21 - Hospital-Clinical-Operations-Inpatient-Capacity"

&#x20;  ```

2\. Place the downloaded `healthcare\_dataset.csv` inside this folder.

3\. Open `Hospital\_Clinical\_Operations\_Capacity.pbix` in \*\*Power BI Desktop\*\*.

4\. If prompted to reconnect the data source:

&#x20;  \* Go to \*\*Home > Transform Data > Data source settings\*\*.

&#x20;  \* Click \*\*Change Source\*\*, browse to your local `healthcare\_dataset.csv`, and click \*\*Close \& Apply\*\*.



\---



<div align="center">



Developed as part of the \*\*30-Day Enterprise Power BI Portfolio Challenge\*\*.



\[Back to Master Repository](https://github.com/yusufehtesham29/30-Days-Of-Power-BI)



</div>

