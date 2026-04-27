# 🏥 Singapore Hospital ED — Patient Flow Simulation

> **Discrete-event simulation of a Singapore public hospital Emergency Department using queueing theory (M/G/c model)**
>
> *Lakshmi C · PhD, Mathematics · Singapore Permanent Resident*

---

## 📌 Project Overview

This project simulates **24 hours of patient flow** through a Singapore hospital Emergency Department (ED) using **discrete-event simulation (SimPy)** grounded in **M/G/c queueing theory**.

The simulation models realistic patient arrivals, triage classification, doctor consultation, and discharge — capturing the complexity of a live ED environment. It is directly connected to my peer-reviewed research:

> Lakshmi C. *Application of queueing theory in health care: a literature review.*
> Journal of Operations Research for Health Care, 2(1–2), 25–39, 2013.
> https://doi.org/10.1016/j.orhc.2013.03

---

## 🎯 Objectives

- Simulate ED patient flow using Poisson arrivals and general service times (M/G/c model)
- Model Singapore MOH triage categories (P1–P4) with realistic arrival and consultation distributions
- Measure wait times, length of stay, and MOH target compliance across triage categories
- Perform sensitivity analysis on staffing levels to identify optimal doctor-to-patient ratios
- Provide actionable insights for hospital resource planning and patient flow optimisation

---

## 📊 Dashboard Preview

![Singapore Hospital ED Simulation Dashboard](sg_hospital_simulation_dashboard.png)

![Sensitivity Analysis — Staffing vs Performance](sg_hospital_sensitivity.png)

---

## 🔬 Methodology

### Queueing Theory Foundation

The ED is modelled as an **M/G/c queue**:

| Component | Model |
|-----------|-------|
| **Arrivals (M)** | Poisson process with time-varying rates (hour-by-hour) |
| **Service time (G)** | Normally distributed per triage category |
| **Servers (c)** | Multiple doctors with priority scheduling |

### Triage Categories (Singapore MOH Standard)

| Category | Description | MOH Wait Target | Arrival % |
|----------|-------------|-----------------|-----------|
| P1 | Resuscitation | Immediate | 3% |
| P2 | Emergency | < 15 minutes | 12% |
| P3 | Urgent | < 30 minutes | 35% |
| P4 | Semi-urgent | < 60 minutes | 50% |

### Arrival Rates by Time of Day

Based on typical Singapore public hospital ED patterns:

| Time Block | Patients/hour |
|------------|--------------|
| 00:00–06:00 | 4.2 |
| 06:00–09:00 | 7.8 |
| 09:00–12:00 | 12.5 (peak) |
| 12:00–15:00 | 11.0 |
| 15:00–18:00 | 13.2 (peak) |
| 18:00–21:00 | 10.5 |
| 21:00–24:00 | 6.8 |

---

## 📈 Key Results (Base Scenario: 8 Doctors, 24 hours)

| Metric | Value |
|--------|-------|
| Total patients simulated | 214 |
| Average wait time | 3.7 minutes |
| Average length of stay | 25.6 minutes |
| Overall MOH target compliance | 97% |
| P2 Emergency compliance | 100% |
| P3 Urgent compliance | 100% |
| P4 Semi-urgent compliance | 100% |

### Sensitivity Analysis Finding

> Reducing doctors from 8 to 5 drops overall MOH target compliance below 80% — the critical threshold for Singapore public hospital KPIs. The simulation quantifies the exact staffing level needed to maintain safe patient care standards.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.10+** | Core language |
| **SimPy** | Discrete-event simulation engine |
| **NumPy / Pandas** | Data processing and analysis |
| **Matplotlib** | Dashboard and visualisation |
| **SciPy** | Statistical distributions |

---

## 📁 Repository Structure

```
sg-hospital-patient-flow-simulation/
│
├── sg_hospital_simulation.py          # Main simulation code
├── sg_hospital_simulation_dashboard.png  # 24h results dashboard
├── sg_hospital_sensitivity.png        # Staffing sensitivity analysis
├── sg_ed_simulation_results.csv       # Full patient-level results data
├── sg_ed_sensitivity_results.csv      # Staffing analysis results
└── README.md                          # This file
```

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/lakrohid/sg-hospital-patient-flow-simulation.git
cd sg-hospital-patient-flow-simulation
```

### 2. Install dependencies
```bash
pip install simpy numpy pandas matplotlib scipy
```

### 3. Run the simulation
```bash
python sg_hospital_simulation.py
```

This will generate:
- Dashboard PNG (patient flow results)
- Sensitivity analysis PNG (staffing vs performance)
- Two CSV files with full results data

### 4. Customise parameters

Open `sg_hospital_simulation.py` and modify the top-level parameters:

```python
NUM_DOCTORS  = 8    # change number of doctors
NUM_NURSES   = 12   # change number of nurses
NUM_BEDS     = 40   # change number of ED beds
SIM_DURATION = 24 * 60  # simulation length in minutes
```

---

## 💡 Insights & Real-World Relevance

1. **Peak hour surges (09:00–18:00)** account for the majority of ED congestion — targeted staffing shifts during these windows can improve compliance without increasing overall headcount.

2. **P1 Resuscitation patients** require immediate attention by definition — the simulation highlights how doctor availability at any given moment affects this critical category.

3. **Optimal staffing sweet spot**: The sensitivity analysis shows that 8–9 doctors maintains >90% MOH compliance, while fewer than 6 doctors causes system-wide wait time deterioration.

4. **Queueing theory validation**: Results align with M/G/c theoretical predictions — server utilisation, mean queue length, and wait times follow expected distributions, validating the simulation design.

---

## 🔗 Related Research

- Lakshmi C. *Application of queueing theory in health care: a literature review.* **Journal of Operations Research for Health Care**, 2013. [DOI](https://doi.org/10.1016/j.orhc.2013.03)
- Lakshmi C. *Performance Analysis of M/G/c retrial queueing systems.* **OPSEARCH**, 2005.
- Lakshmi C. *Modelling M/G/1 Queueing Systems with Server Vacations.* **ORION**, 2006.

---

## 👩‍💻 About the Author

**Lakshmi C** — PhD, Mathematics (Madurai Kamaraj University, 2008)

Postdoctoral Research Fellow, Nanyang Technological University, Singapore (2011–2012), specialising in queueing theory applications in healthcare logistics. Published researcher in healthcare operations research. Singapore Permanent Resident.

- 📧 lakrohid@gmail.com
- 🔗 [LinkedIn](https://www.linkedin.com/in/c-lakshmi/)
- 🌐 [Portfolio](https://www.datascienceportfol.io/lakrohid)

---

## 📄 License

This project is open-source under the [MIT License](LICENSE).

---

*If you find this project useful, please ⭐ star the repository!*
