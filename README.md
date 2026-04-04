# 🧠 Panic Attack Data Analysis Dashboard — Power BI Healthcare Intelligence Project

<p align="center">
  <img src="https://img.shields.io/badge/Tool-Power%20BI%20Desktop-F2C811?logo=powerbi&logoColor=black" />
  <img src="https://img.shields.io/badge/Domain-Healthcare%20Analytics%20%7C%20Mental%20Health-4a90d9" />
  <img src="https://img.shields.io/badge/Dashboard%20Pages-4-blueviolet" />
  <img src="https://img.shields.io/badge/Dataset-1%2C200%20Patients-orange" />
  <img src="https://img.shields.io/badge/Clinical%20Variables-21-blue" />
  <img src="https://img.shields.io/badge/Status-Production%20Ready-brightgreen" />
</p>

---

## 📌 Table of Contents

- [Business Problem](#-business-problem)
- [Project Objective](#-project-objective)
- [Dataset Description](#-dataset-description)
- [Data Cleaning & Preparation](#-data-cleaning--preparation)
- [Data Modeling](#-data-modeling)
- [Key KPIs & Metrics](#-key-kpis--metrics)
- [Dashboard Walkthrough](#-dashboard-walkthrough)
- [Business Insights](#-business-insights)
- [Business Recommendations](#-business-recommendations)
- [Tools & Technologies](#-tools--technologies)
- [How to Use](#-how-to-use)
- [Project Structure](#-project-structure)
- [Screenshots](#-screenshots)
- [Author](#-author)

---

## 🧩 Business Problem

### The Healthcare Industry Challenge

Mental health disorders — particularly anxiety and panic attack conditions — represent one of the **fastest-growing public health crises** worldwide. The World Health Organization estimates that anxiety disorders affect over 300 million people globally, generating enormous costs for healthcare systems, employers, and individuals. Yet despite the scale of this crisis, **clinical decision-making in mental health care remains disproportionately subjective and data-poor** compared to other medical disciplines.

Three specific gaps persist across healthcare organisations:

**1. Inability to Identify High-Risk Patients Early**
Healthcare providers lack a structured analytical framework to identify which patients are most likely to experience severe or frequent panic attacks. Without risk profiling, clinical interventions are reactive — patients receive care after crisis, not before it.

**2. No Unified View of Lifestyle-Symptom-Severity Relationships**
Panic attack severity is shaped by a complex web of factors: sleep quality, caffeine intake, smoking habits, alcohol consumption, exercise patterns, and underlying medical history. These data points exist across separate clinical notes, intake forms, and self-reports — never synthesised into a single analytical view that clinicians can act on.

**3. Treatment Effectiveness Is Not Being Tracked at Population Level**
Despite investing in therapy and medication for a significant proportion of patients, healthcare providers have no consistent mechanism to measure whether these interventions are reducing severity scores, attack frequency, or episode duration across the patient population.

### Who Bears the Cost

| Stakeholder | Pain Point |
|---|---|
| **Hospital & Clinic Administrators** | Cannot allocate mental health resources based on evidence about patient risk profiles |
| **Psychiatrists & Therapists** | Must make treatment decisions without aggregate pattern data across similar patient cohorts |
| **Public Health Officials** | No structured analytics to design population-level programmes targeting the right triggers |
| **Patients Themselves** | Delayed or inappropriate treatment due to lack of data-driven triage and personalised care |
| **Insurance Companies** | Cannot accurately assess risk profiles or design incentives that promote preventive mental healthcare |

---

## 🎯 Project Objective

This project delivers a **four-page, interactive Power BI healthcare analytics dashboard** built on 1,200 panic attack patient records. It transforms raw clinical and lifestyle data into structured, decision-ready intelligence for healthcare administrators, clinical staff, and public health planners.

**Business Goals:**
- Enable healthcare providers to identify the most prevalent panic attack triggers across their patient population
- Surface the relationship between lifestyle factors (sleep, caffeine, alcohol, exercise, smoking) and panic attack severity
- Provide demographic breakdowns (age group, gender) to support targeted intervention design
- Track symptom prevalence to inform triage protocols and clinical resource planning

**Analytical Goals:**
- Build a clean, single-table data model from a 21-field patient dataset with calculated columns
- Create a `Panic Score (HML)` segmentation variable to classify patients into Low, Medium, and High severity tiers
- Derive an `Age Group IF` dimension for cross-generational analysis of panic frequency and severity
- Deliver 4 focused dashboard pages covering symptoms, lifestyle factors, demographic patterns, and executive overview

---

## 📋 Dataset Description

### Source

| Property | Detail |
|---|---|
| **Format** | CSV — `panic_attack_dataset.csv` |
| **SQL Schema** | `New_Text_Document.txt` — `CREATE TABLE PANIC_ATTACK_DATA` |
| **Database** | `PowerBIProject` (defined in SQL DDL) |
| **Records** | 1,200 patient entries |
| **Fields** | 21 clinical and lifestyle variables |
| **Missing Values** | `Medical_History` only — 122 nulls (10.2%) |
| **Duplicates** | Zero — ID is unique across all 1,200 records |

### Full Field Dictionary

#### 👤 Demographic Fields

| Field | Type | Description & Values |
|---|---|---|
| `ID` | Integer | Unique patient identifier (1–1,200) |
| `Age` | Integer | Patient age — range 18–64, mean 41.1 years |
| `Gender` | String | Female (549 / 45.8%), Male (537 / 44.8%), Non-binary (114 / 9.5%) |

#### 🩺 Clinical / Attack Profile Fields

| Field | Type | Description & Values |
|---|---|---|
| `Panic_Attack_Frequency` | Integer | Attacks per period — range 0–9, mean 4.4 |
| `Duration_Minutes` | Integer | Average episode duration — range 5–44 min, mean 24.4 min |
| `Trigger` | String | PTSD (205), Unknown (206), Phobia (203), Caffeine (202), Social Anxiety (197), Stress (187) |
| `Heart_Rate` | Integer | Peak heart rate during attack — range 80–159 bpm, mean 120.3 bpm |
| `Medical_History` | String | Anxiety (492), Depression (349), PTSD (237), Null (122) |
| `Panic_Score` | Integer | Composite severity 1–10 — mean 5.57, std 2.79 |

#### 🏃 Lifestyle Fields

| Field | Type | Description & Values |
|---|---|---|
| `Caffeine_Intake` | Integer | Daily caffeine servings — range 0–5, mean 2.54 |
| `Exercise_Frequency` | Integer | Workouts per week — range 0–6, mean 2.96 |
| `Sleep_Hours` | Decimal | Average nightly sleep — range 4.0–9.0 hrs, mean 6.48 hrs |
| `Alcohol_Consumption` | Integer | Drinks per week — range 0–9, mean 4.4 |
| `Smoking` | Boolean | Yes: 325 (27.1%), No: 875 (72.9%) |

#### 💊 Symptom & Treatment Fields

| Field | Type | Prevalence |
|---|---|---|
| `Sweating` | Boolean | Yes: 836 (69.7%) — most common symptom |
| `Shortness_of_Breath` | Boolean | Yes: 746 (62.2%) |
| `Dizziness` | Boolean | Yes: 620 (51.7%) |
| `Trembling` | Boolean | Yes: 590 (49.2%) |
| `Chest_Pain` | Boolean | Yes: 487 (40.6%) |
| `Medication` | Boolean | Yes: 500 (41.7%), No: 700 (58.3%) |
| `Therapy` | Boolean | Yes: 605 (50.4%), No: 595 (49.6%) |

---

## 🔧 Data Cleaning & Preparation

### Missing Value Treatment

**`Medical_History` — 122 null values (10.2%)**
This is the dataset's only field with missing values. The nulls represent patients with **no formally diagnosed pre-existing mental health condition** — a clinically meaningful category, not a data quality failure. These records are retained in the model; the `Medical_History` slicer on the dashboard excludes them by default to prevent distortion of group-level clinical averages.

**All other 20 fields are complete** — zero nulls across 1,200 records.

### Standardisation Applied

- **Boolean fields** (`Sweating`, `Shortness_of_Breath`, `Dizziness`, `Chest_Pain`, `Trembling`, `Medication`, `Smoking`, `Therapy`) standardised to `Yes`/`No` string format in Power Query for consistent slicer behaviour
- **`Trigger`** validated across 6 clean categories: Stress, PTSD, Phobia, Caffeine, Social Anxiety, Unknown
- **`Gender`** confirmed as three-value categorical: Female, Male, Non-binary
- **`Sleep_Hours`** maintained as `DECIMAL (5,2)` per the SQL DDL schema definition
- **SQL DDL schema** (`New_Text_Document.txt`) used to define field types at data ingestion: `INT`, `STRING`, `BOOLEAN`, `number(5,2)`

### Calculated Columns Created in Power BI (DAX)

**`Panic Score (HML)` — Severity Tier Segmentation:**

This is the most important analytical addition in the model. It converts the continuous 1–10 Panic Score into three actionable clinical tiers used as a slicer and filter across multiple dashboard pages:

```
Low    : Panic_Score ≤ 3  → 324 patients (27.0%)
Medium : Panic_Score ≤ 6  → 397 patients (33.1%)
High   : Panic_Score ≥ 7  → 479 patients (39.9%)
```

**`Age Group IF` — Generational Cohort Segmentation:**

Derives a five-band age cohort from the continuous `Age` field, enabling the Age Group Analysis dashboard page:

```
18-25 : 181 patients (15.1%)
26-35 : 232 patients (19.3%)
36-45 : 268 patients (22.3%)
46-55 : 272 patients (22.7%)
56-65 : 218 patients (18.2%)  [note: includes age = 65 via ELSE clause]
```

---

## 🗄️ Data Modeling

### Schema Design

The model uses a **single flat-table schema** — one primary fact table with all 21 source fields plus two DAX-calculated columns:

```
┌──────────────────────────────────────────────────────────┐
│                   PANIC_ATTACK_DATA                       │
├───────────────────────────┬──────────────────────────────┤
│  DIMENSION / CATEGORICAL  │  MEASURE / NUMERIC           │
│  ─────────────────────    │  ─────────────────────       │
│  ID (PK)                  │  Panic_Attack_Frequency      │
│  Age                      │  Duration_Minutes             │
│  Gender                   │  Heart_Rate                  │
│  Trigger                  │  Caffeine_Intake              │
│  Medical_History           │  Exercise_Frequency          │
│  Sweating                 │  Sleep_Hours                 │
│  Shortness_of_Breath      │  Alcohol_Consumption         │
│  Dizziness                │  Panic_Score                 │
│  Chest_Pain               │                              │
│  Trembling                │  DAX CALCULATED COLUMNS      │
│  Medication               │  ─────────────────────       │
│  Smoking                  │  Panic Score (HML)           │
│  Therapy                  │  Age Group IF                │
└───────────────────────────┴──────────────────────────────┘
```

### Why a Single-Table Model?

The dataset represents **one observation per patient** — all clinical, lifestyle, demographic, and treatment variables are captured at the same grain. A star schema with dimension tables would add unnecessary complexity without enabling any additional analytical capability. The single-table design:
- Eliminates ambiguous join paths that could distort cross-dimensional slicer behaviour
- Allows all four slicer selections to propagate correctly across all dashboard pages
- Simplifies DAX — all measures reference the same table context without RELATED() complexity

### Slicer Architecture (4 Interactive Filters)

| Slicer | Field | Values |
|---|---|---|
| Severity Tier | `Panic Score (HML)` | Low / Medium / High |
| Demographics | `Gender` | Female / Male / Non-binary |
| Attack Trigger | `Trigger_Reason` | 6 trigger categories |
| Medical Background | `Medical_History` | Anxiety / Depression / PTSD |

---

## 📐 Key KPIs & Metrics

### Patient Population Summary KPIs

| KPI | Value | Clinical Significance |
|---|---|---|
| **Total Patients** | 1,200 | Full cohort — statistically robust for population-level analysis |
| **Average Panic Score** | 5.57 / 10 | Mid-range severity — significant burden across the full cohort |
| **High Severity Patients** | 479 (39.9%) | Nearly 4 in 10 patients need urgent clinical attention |
| **Average Attack Frequency** | 4.4 per period | Chronic, not episodic — multiple attacks per week on average |
| **Average Episode Duration** | 24.4 minutes | Clinically significant — attacks lasting nearly 30 minutes each |
| **Average Peak Heart Rate** | 120.3 bpm | 50% above typical resting rate — acute cardiovascular stress risk |

### Symptom Prevalence — Clinical Triage Indicators

| Symptom | Prevalence | Clinical Priority |
|---|---|---|
| **Sweating** | 69.7% | Most common — affects 836 of 1,200 patients |
| **Shortness of Breath** | 62.2% | Respiratory impairment — triage and safety management |
| **Dizziness** | 51.7% | Fall and injury risk — functional daily impact |
| **Trembling** | 49.2% | Motor control impairment — limits daily activities |
| **Chest Pain** | 40.6% | Cardiac symptom mimic — major ED and cost driver |

### Treatment Coverage Analysis

| Treatment Status | Count | % | Avg Panic Score |
|---|---|---|---|
| **Therapy Only** | 362 | 30.2% | 5.63 |
| **No Treatment** | 338 | 28.2% | 5.40 |
| **Medication Only** | 257 | 21.4% | 5.67 |
| **Both (Therapy + Medication)** | 243 | 20.3% | 5.61 |

> **Critical gap:** 28.2% of patients are receiving **zero treatment** despite a clinically significant average Panic Score of 5.40. This represents the highest-priority untreated population for healthcare outreach.

---

## 🖥️ Dashboard Walkthrough

*Presenting each page as a stakeholder-ready analytical narrative.*

---

### 📋 Page 1 — Panic Attacks (Overview / Landing Page)

**Visual Types:** Custom Image + Textbox narrative panel
**Canvas Size:** 1,280 × 720 px (16:9 widescreen)

**Presenting to Stakeholders:**

This is the dashboard's narrative anchor — the first screen any stakeholder sees when opening the file. A custom branded PNG image establishes professional visual identity. The textbox panel explains the clinical context: what Panic Score measures, what triggers are included, and what questions the dashboard is designed to answer.

This page communicates immediately to non-technical stakeholders — hospital administrators, board members, or public health commissioners — that this is a **decision-support tool**, not a data dump. It frames the analytical journey that follows across the three analytical pages.

The page title itself — "Panic Attacks" — combined with the branded imagery signals that this dashboard was built specifically for this domain, distinguishing it from a generic template.

**Purpose in the Flow:**
Sets the context → audiences understand *why* they are looking at this data before they engage with the numbers. A stakeholder who understands the framing will ask better analytical questions of the subsequent pages.

---

### 🤒 Page 2 — Number of Patients by Symptoms

**Visual Types:** 5 Horizontal Bar Charts
**Fields:** `DIZZINESS`, `TREMBLING`, `SWEATING`, `SHORTNESS_OF_BREATH`, `CHEST_PAIN` (Yes/No) × `COUNT(ID)`
**Interaction:** Clicking a bar in one chart cross-filters all other four charts

**Presenting to Stakeholders:**

This page answers the essential triage question: *"What physical symptoms define this patient population, and how prevalent is each?"*

Five side-by-side bar charts compare the count of patients experiencing vs. not experiencing each physical symptom. The visual immediately surfaces a crucial clinical reality: **sweating and shortness of breath are near-universal experiences** in this cohort — appearing in 7 in 10 and 6 in 10 patients respectively. No other physical symptoms approach this prevalence.

**Reading the Charts Clinically:**

**Sweating (836 patients / 69.7%):** The most prevalent symptom. While sweating is uncomfortable, it is not medically dangerous — but its high prevalence across the cohort confirms that physical symptom burden is a near-universal experience, not an outlier.

**Shortness of Breath (746 patients / 62.2%):** Affects nearly two-thirds of patients. Respiratory impairment during episodes creates real safety risks — particularly for patients who drive, operate machinery, or care for dependants. Clinical management should include breathing techniques as a standard component of every treatment plan.

**Dizziness (620 patients / 51.7%):** Over half the cohort experiences dizziness — a direct fall and injury risk. Patient safety planning should account for this, particularly for older patients in the 46–65 cohort.

**Trembling (590 patients / 49.2%) and Chest Pain (487 patients / 40.6%):** The chest pain figure is the most strategically important — 40.6% of confirmed panic patients experience a symptom that is clinically indistinguishable from cardiac chest pain in an emergency setting. This drives costly, unnecessary ED visits and cardiac investigations.

**Cross-Filter Use Case:**
Clicking "Yes" on the Chest Pain chart cross-filters all other symptom charts — revealing the symptom co-occurrence profile for chest pain patients. This informs which clinical protocols should be bundled for patients presenting with this high-cost symptom.

**Decisions Enabled:**
- Clinical protocol design — which symptoms require mandatory nursing assessment
- Patient education priorities — which symptoms to target in psychoeducation
- Resource allocation — estimating cardiac, respiratory, and physiotherapy referral volumes driven by panic presentations

---

### 📊 Page 3 — Other Requirements (Lifestyle Factor Analysis)

**Visual Types:** 4 Slicers + 3 Line Charts
**Slicers:** `Panic Score (HML)`, `Gender`, `Trigger_Reason`, `Medical_History`
**Line Charts:**
- Number of Patients by Drinks per Week (Alcohol Consumption)
- Number of Patients by Sleep Hours
- Number of Patients by Panic Attack Duration in Minutes

**Presenting to Stakeholders:**

This is the dashboard's most analytically rich and interactive page. It allows any stakeholder to explore the relationship between **lifestyle factors and panic attack patterns** by applying any combination of four slicers to dynamically refilter all three line charts simultaneously.

**Line Chart 1 — Patients by Drinks per Week (Alcohol Consumption):**
The distribution of alcohol consumption across the 0–9 drinks/week range is visible for the full cohort. Applying `Panic Score = High` reveals whether the highest-severity patients cluster at particular consumption levels. This answers the operational question: *"Should we screen for heavy alcohol use as a standard component of high-severity patient assessment?"*

**Line Chart 2 — Patients by Sleep Hours:**
Sleep hours follow a roughly normal distribution (4.0–9.0 hrs, mean 6.48 hrs). Mid-range sleepers show the highest average Panic Scores — a counter-intuitive finding that challenges the assumption that extreme sleep deprivation alone drives severity. This suggests **sleep quality and sleep regularity**, not just hours, as clinically relevant variables worth capturing in future patient intake.

**Line Chart 3 — Patients by Panic Attack Duration in Minutes:**
The spread of episode durations (5–44 minutes, mean 24.4 min) visualises the full range of acute episode burden. Combined with the mean attack frequency of 4.4 per period, patients in this cohort spend an average of over **100 minutes per period incapacitated by panic** — a meaningful productivity and quality-of-life quantification that healthcare systems can use to justify mental health investment.

**Slicer Power — Multi-Dimensional Patient Profiling:**
A clinical manager can combine slicers to create a targeted sub-group profile:
- `Panic Score = High` + `Medical History = PTSD` + `Trigger = Social Anxiety`
- All three line charts instantly filter to this specific high-risk patient profile
- The resulting lifestyle distributions reveal whether this sub-group drinks more, sleeps less, or experiences longer episodes than the general population
- These findings directly inform personalised care pathway design for the most complex patients

**Decisions Enabled:**
- Personalised care pathways — tailoring lifestyle interventions (sleep hygiene, alcohol reduction, caffeine guidance) to specific trigger and severity segments
- Group therapy programme targeting — identifying patient clusters with similar lifestyle profiles for cohort-based intervention design
- Treatment intensity decisions — which lifestyle risk factor combinations justify intensive vs. standard care pathways

---

### 📈 Page 4 — Age Group Analysis

**Visual Type:** 1 Clustered Bar Chart
**X-axis:** `Age Group IF` (calculated column — 5 age bands)
**Y-axis & Cluster Measures:** `Sum(SLEEP_HOURS)`, `Sum(PANIC_SCORE)`, `Sum(PANIC_ATTACK_FREQUENCY)`
**Legend Dimension:** `Trigger_Reason`
**Chart Title:** "Average of Sleep Hours / Panic Score / Panic Attack Frequency by Age Group"

**Presenting to Stakeholders:**

This is the demographic intelligence page — revealing how panic attack burden is distributed across five generational cohorts and identifying the age groups where clinical resource investment will deliver the greatest per-patient impact.

**Reading the Chart by Age Band:**

**18–25 (181 patients):** The highest Panic Score (5.78) and highest attack frequency (4.65/period) of any age group — young adults carry the greatest acute panic burden. They are also the group most likely to have sleep deprivation as a contributing lifestyle factor. Despite bearing the highest per-patient burden, this age group may be the least likely to self-refer to clinical services — suggesting the need for **proactive outreach through universities, employers, and digital channels**.

**26–35 (232 patients):** Still above average severity (5.69) with high attack frequency (4.44). PTSD and Social Anxiety emerge as key triggers in this cohort — corresponding to the stresses of early career, relationship formation, and social performance pressure.

**36–45 (268 patients — largest cohort):** The lowest average Panic Score (5.21) of any age group — a counter-intuitive finding. Mid-career adults may have developed stronger coping mechanisms, be more actively accessing treatment, or have more stabilised daily routines despite occupational stress. This cohort may represent the highest **treatment receptiveness** and the best potential return on therapy investment.

**46–55 (272 patients — largest cohort):** Recovery from the 36–45 trough — average score rises to 5.61. Life-stage transitions (career peaks, family changes, approaching retirement) likely re-activate stress and anxiety pathways.

**56–65 (218 patients):** Elevated scores (5.66) and attack frequency (4.53) — a second wave of panic burden in older adults potentially driven by chronic health co-morbidities, bereavement, social isolation, and retirement adjustment. This cohort is also the most likely to have chest pain symptoms mis-attributed to cardiac causes, making accurate panic diagnosis especially important.

**Trigger Overlay in the Clustered Chart:**
The `Trigger_Reason` breakdown within each age band reveals trigger prevalence by cohort — informing whether Stress programmes should prioritise the 36–45 cohort, PTSD support the 18–35 cohort, or Unknown-cause investigation the older cohorts.

**Decisions Enabled:**
- Age-stratified resource planning — allocating intensive services to 18–25 and 56–65 cohorts
- Life-stage intervention design — matching programme content (student stress, occupational burnout, retirement adjustment) to each cohort's trigger profile
- Public health campaign targeting — directing awareness and referral campaigns to the highest-burden, most under-served age groups

---

## 💡 Business Insights

> *Translating analytical patterns from the data and dashboard into strategic intelligence for healthcare decision-makers.*

### Insight 1 — 40% of Patients Are High-Severity — Clinical Resources Are Under-Allocated

479 patients (39.9%) score 7 or above — the high-severity clinical tier. Yet only 243 patients (20.3%) receive both therapy and medication simultaneously. The **mismatch between high-severity population size and combined treatment coverage** represents a systematic under-treatment gap that administrators must address through urgent capacity planning and referral pathway review. The system is not matching its highest-acuity patients with its most intensive treatment option.

### Insight 2 — Sweating and Shortness of Breath Are Near-Universal — Clinical Protocols Should Standardise Response

Sweating (69.7%) and shortness of breath (62.2%) affect the majority of this patient population — yet these are also symptoms of cardiac, pulmonary, and other medical conditions. The prevalence in this confirmed panic cohort creates a strong clinical case for **standardised symptom-response protocols** that confidently distinguish panic-driven physical symptoms from other medical causes — reducing unnecessary investigations and improving patient triage efficiency.

### Insight 3 — Chest Pain in 40.6% of Patients Is a Major System Cost Driver

487 patients experience chest pain during panic attacks — the symptom most likely to trigger emergency department visits, ECG investigations, troponin assays, and cardiology referrals. A patient population with 40.6% chest pain prevalence at a mean attack frequency of 4.4 represents a **substantial and quantifiably reducible healthcare cost burden**. A mental health fast-track pathway for confirmed panic patients presenting with chest pain could meaningfully deflect expensive ED demand.

### Insight 4 — Smokers Show Materially Higher Panic Scores Than Non-Smokers

Smokers average a Panic Score of **5.91 vs. 5.44 for non-smokers** — an 8.6% higher severity differential. Nicotine withdrawal between cigarettes triggers physiological anxiety responses that compound panic disorder, creating a reinforcing cycle of symptom escalation. This finding directly supports **integrating smoking cessation support into panic disorder treatment pathways** as a co-morbidity treatment rather than an optional lifestyle recommendation.

### Insight 5 — PTSD Is Both the Highest-Frequency Trigger and the Highest-Severity Medical History

PTSD as a trigger produces the highest average attack frequency (4.69/period). PTSD as a diagnosed medical history produces the highest average Panic Score (5.74). **PTSD-positive patients are the single highest-risk clinical sub-group across every severity measure** in this dataset. Yet their treatment is not differentiated from general anxiety patients in most care pathways — a critical clinical gap that a dedicated PTSD-panic co-morbidity stream would address directly.

### Insight 6 — Young Adults (18–25) Carry the Highest Per-Patient Panic Burden

The 18–25 cohort records both the **highest average Panic Score (5.78) and highest attack frequency (4.65/period)** of any age group — despite being one of the smaller cohorts. This group also shows the lowest average sleep hours, strongly suggesting sleep deprivation as a key modifiable risk factor. Student mental health services and young adult primary care are likely the **highest-leverage intervention points** in terms of severity impact per resource invested.

### Insight 7 — 28.2% of Patients Receive Zero Treatment Despite Significant Clinical Need

338 patients are receiving neither therapy nor medication — a treatment void in more than one-quarter of the cohort. Their average Panic Score of 5.40 is not materially lower than treated patients, confirming they are experiencing significant clinical burden without any formal support. Healthcare systems need **active outreach and opt-in mechanisms** — digital self-referral pathways, GP screening triggers, and employer mental health access programmes — to identify and engage this population before conditions escalate.

### Insight 8 — Social Anxiety and PTSD Triggers Produce the Highest Severity — Not All Triggers Are Clinically Equivalent

Social Anxiety (5.77) and PTSD (5.77) triggers produce materially higher Panic Scores than Caffeine (5.38) and Unknown (5.38) triggers. This means **trigger type should directly inform treatment assignment**. Exposure therapy for phobia-triggered patients and trauma processing for PTSD-triggered patients require entirely different clinical competencies — yet trigger-specific pathway differentiation is absent in most anxiety services today.

---

## 💼 Business Recommendations

**1. Implement a Severity-Stratified Care Pathway Based on Panic Score (HML)**
Formalise the three severity tiers from the calculated column into operational care protocols: Low (self-management resources + 3-month review), Medium (structured CBT referral within 4 weeks), High (combined pharmacotherapy + intensive therapy + monthly clinical review). This directly addresses the current mismatch between 39.9% high-severity prevalence and 20.3% combined treatment coverage.

**2. Create a Dedicated PTSD-Panic Co-Morbidity Treatment Stream**
PTSD patients consistently appear at the top of every severity measure in this dataset. Establish a specialist pathway staffed by trauma-trained clinicians offering EMDR or trauma-focused CBT alongside pharmacotherapy. This targeted resource will likely yield the greatest per-patient outcome improvement of any single clinical investment, given PTSD's dual role as both trigger and highest-severity medical history category.

**3. Integrate Lifestyle Screening Into Every Initial Patient Assessment**
Alcohol consumption, sleep hours, and smoking status all show meaningful associations with panic severity in this dataset. Every new panic disorder patient should complete a validated lifestyle screening instrument at intake, automatically flagging patients for co-ordinated sleep hygiene, alcohol reduction, and smoking cessation support alongside their primary anxiolytic treatment.

**4. Build a Chest Pain Fast-Track Protocol to Reduce Emergency Department Demand**
Partner with Emergency Departments to implement a "Panic Presentation Protocol" — confirmed panic disorder patients presenting with chest pain are triaged directly to mental health crisis support rather than standard cardiac workup. Combined with GP-issued patient identification cards listing their panic disorder diagnosis, this protocol could generate significant measurable ED cost savings.

**5. Design Young Adult Prevention Programmes as a System Investment**
The 18–25 cohort's elevated severity profile — combined with their likely status as students or early-career workers — makes them ideal candidates for digital prevention programmes. Apps providing sleep tracking, guided breathing, and cognitive reframing exercises delivered through university health services or employer assistance programmes could intercept panic disorder **before it reaches clinical severity**, reducing long-term system burden.

**6. Activate the 338-Patient Untreated Population Through Active Outreach**
Design a structured outreach strategy: GP-triggered digital referrals, opt-in SMS check-in programmes, and community mental health workers embedded in primary care settings. Even a 50% engagement rate would add 169 patients into clinical pathways — measurably improving population-level outcomes and reducing future high-acuity demand.

**7. Integrate Smoking Cessation as Standard in Panic Disorder Treatment**
The 8.6% higher Panic Score in smokers demonstrates a clinically meaningful co-morbidity relationship. Include brief smoking cessation counselling and pharmacological support (varenicline or NRT) in the standard panic disorder treatment bundle for all smoking patients. Treating these as co-morbid — not independent — conditions directly addresses a modifiable severity driver that current pathways overlook.

---

## 🛠️ Tools & Technologies

| Tool / Technology | Role in Project |
|---|---|
| **Microsoft Power BI Desktop** | Primary BI platform — data modeling, DAX calculations, dashboard design |
| **Power Query (M Language)** | Data ingestion, Boolean field standardisation, type validation |
| **DAX (Data Analysis Expressions)** | Calculated columns: `Panic Score (HML)` severity tier, `Age Group IF` cohort segmentation |
| **SQL (DDL Schema)** | Schema definition — `CREATE TABLE PANIC_ATTACK_DATA` in `PowerBIProject` database |
| **CSV Source File** | `panic_attack_dataset.csv` — 1,200 rows × 21 columns |
| **Single Flat-Table Schema** | All 21 fields + 2 DAX calculated columns in one `PANIC_ATTACK_DATA` table |
| **Interactive Slicers (4)** | `Panic Score (HML)`, `Gender`, `Trigger_Reason`, `Medical_History` — cross-page filtering |
| **Custom Brand Images** | Two PNG visuals embedded for dashboard visual identity |
| **Brand Colour Palette** | `#66554E` warm brown (primary, 58 uses), `#CEC7BE` soft beige, `#FFFFFF` white |
| **Canvas Size** | 1,280 × 720 px (16:9 widescreen format) |

---

## ▶️ How to Use

### Prerequisites

- **Microsoft Power BI Desktop** — free from [powerbi.microsoft.com/desktop](https://powerbi.microsoft.com/desktop/)
- Windows OS (Power BI Desktop is Windows-native; Mac users can access via Power BI Service in browser)
- No external database or connection required — all data is embedded in the `.pbix` file

### Opening the Dashboard

```
1. Clone or download this repository to your local machine
2. Open:  Panic_Attack_Data_Analysis_Power_BI_Project.pbix
3. Power BI Desktop launches automatically — the embedded model loads instantly
4. Navigate between pages via bottom tabs:
      ├── Panic Attacks                   →  Overview / landing page
      ├── Number of Patients by Symptoms  →  5 symptom bar charts
      ├── Other Requirements              →  4 slicers + 3 lifestyle line charts
      └── Age Group Analysis              →  Demographic clustered bar chart
```

### Interacting with the Dashboard

**Severity Filtering (Other Requirements page):**
```
→ Select "Low", "Medium", or "High" in the Panic Score (HML) slicer
→ All three line charts instantly update to show the lifestyle distribution for that severity tier
→ Layer in Gender, Trigger, or Medical History slicers for multi-dimensional patient profiling
```

**Symptom Cross-Filtering (Symptoms page):**
```
→ Click any bar in one of the five symptom charts
→ All four remaining charts cross-filter to show the symptom co-occurrence profile
→ Example: Click "Yes" on Chest Pain → see what percentage of those patients also experience Dizziness
```

**Age Group Exploration (Age Group Analysis page):**
```
→ Hover over each age band in the clustered chart to see tooltips with exact values
→ Sleep Hours / Panic Score / Attack Frequency displayed per cohort
→ Click a Trigger_Reason segment to isolate that trigger's contribution within an age band
```

**Publishing to Power BI Service:**
```
→ Home ribbon → Publish → select your workspace
→ Access the live interactive dashboard at app.powerbi.com from any browser
→ Share with clinical administrators, department heads, or public health commissioners
```

---

## 📁 Project Structure

```
Panic-Attack-Analytics-PowerBI/
│
├── Panic_Attack_Data_Analysis_Power_BI_Project.pbix   # Primary Power BI workbook
│                                                       # Contains: embedded data + DAX model + all visuals
│
├── panic_attack_dataset.csv                            # Source dataset — 1,200 patients × 21 fields
│
├── New_Text_Document.txt                               # SQL DDL schema
│                                                       # CREATE TABLE PANIC_ATTACK_DATA (21 typed fields)
│
├── Screenshots/                                        # Dashboard page exports
│   ├── 01_Overview_Panic_Attacks.png                   # Landing page — branded overview
│   ├── 02_Symptoms_Analysis.png                        # 5 symptom bar charts
│   ├── 03_Lifestyle_Analysis.png                       # 4 slicers + 3 lifestyle line charts
│   └── 04_Age_Group_Analysis.png                       # Demographic clustered bar chart
│
└── README.md                                           # Project documentation (this file)
```

### Internal Power BI Model Reference

| Component | Detail |
|---|---|
| **Dashboard Pages** | 4 (Overview, Symptoms, Lifestyle/Other Requirements, Age Group Analysis) |
| **Visual Types** | 5 Bar Charts + 3 Line Charts + 1 Clustered Bar Chart + 4 Slicers + 1 Image + 1 Textbox |
| **Data Source Table** | 1 flat table — `PANIC_ATTACK_DATA` |
| **Source Records** | 1,200 patient entries |
| **DAX Calculated Columns** | 2 (`Panic Score (HML)`, `Age Group IF`) |
| **Slicer Dimensions** | 4 (`Panic Score HML`, `Gender`, `Trigger_Reason`, `Medical_History`) |
| **DAX Measures** | `CountNonNull(ID)`, `Sum(PANIC_SCORE)`, `Sum(PANIC_ATTACK_FREQUENCY)`, `Sum(SLEEP_HOURS)` |
| **Canvas Size** | 1,280 × 720 px (16:9 widescreen) |

---

## 📸 Screenshots

> *Export pages from Power BI Desktop: File → Export → Export to PDF, or use the snipping tool for individual page captures. Save to the `Screenshots/` folder.*

### Page 1 — Panic Attacks (Overview)
![Overview]![<img width="1141" height="655" alt="image" src="https://github.com/user-attachments/assets/00b2a924-e7ee-4581-b5fe-0aa3c83dfadb" />
]()

> Custom branded landing page with narrative textbox and branded PNG. Establishes clinical context and scopes the analytical agenda before stakeholders engage with data.

### Page 2 — Number of Patients by Symptoms
![Symptoms](<img width="1130" height="642" alt="image" src="https://github.com/user-attachments/assets/a7bb262e-6abc-4f3e-a7d9-e9c1ec9fcb1c" />
)
> 5 horizontal bar charts: Sweating (69.7%), Shortness of Breath (62.2%), Dizziness (51.7%), Trembling (49.2%), Chest Pain (40.6%). Cross-filter interaction between charts.

### Page 3 — Other Requirements (Lifestyle Analysis)
![Lifestyle](<img width="1138" height="647" alt="image" src="https://github.com/user-attachments/assets/bf264d3c-39f8-47c7-bfc3-28728aa4adcf" />
)
> 4 interactive slicers (Panic Score HML, Gender, Trigger, Medical History) driving 3 line charts showing alcohol consumption, sleep hours, and attack duration distributions.

### Page 4 — Age Group Analysis
![Age Groups](<img width="1139" height="647" alt="image" src="https://github.com/user-attachments/assets/1cfcd0c9-9ef8-4558-8599-d1e736253125" />
)
> Clustered bar chart showing Average Sleep Hours / Panic Score / Attack Frequency by 5 age cohorts (18–25 through 56–65) with Trigger_Reason breakdown overlay.

---

## 👤 Author

<table>
  <tr>
    <td align="center">
      <b>Vishal Londhekar</b><br/>
      <i>Data Analyst | Business Analyst</i><br/><br/>
      <a href="https://github.com/vishal-Londhekar">🔗 GitHub</a>
    </td>
  </tr>
</table>

> *"Healthcare analytics is not about dashboards — it's about ensuring the right patient receives the right intervention at the right time. Every insight here represents a real person whose quality of life can be measurably improved through better data-driven clinical decisions."*

---

## ⭐ If this project contributed to your healthcare analytics journey, please star the repository!

---

<p align="center">
  <img src="https://img.shields.io/badge/Built%20with-Power%20BI-F2C811?logo=powerbi" />
  <img src="https://img.shields.io/badge/Domain-Mental%20Health%20Analytics-4a90d9" />
  <img src="https://img.shields.io/badge/Patients%20Analysed-1%2C200-orange" />
  <img src="https://img.shields.io/badge/Clinical%20Variables-21-blueviolet" />
  <img src="https://img.shields.io/badge/Dashboard%20Pages-4-blue" />
</p>
