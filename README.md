# Trader Joe's NYC Flower Logistics Optimization

![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python&logoColor=white)
![Optimization](https://img.shields.io/badge/Method-MILP_%7C_VRPTW-green)
![Tools](https://img.shields.io/badge/Tools-Selenium_%7C_OSRM-orange)
![Status](https://img.shields.io/badge/Status-Course_Project-success)

> **Applying Operations Research to optimize the "Cold Chain" for fresh flower delivery in NYC.**
>
> **Impact:** Achieved a **31.5% cost reduction** by implementing time-window penalties and Off-Hour Delivery (OHD) incentives.

---

## 📖 Project Overview

Trader Joe's relies on a **"Turn and Burn"** strategy for its high-turnover floral inventory. However, the lack of precise transportation planning leads to significant wastage due to traffic delays and deterioration.

This project develops a **Vehicle Routing Problem with Time Windows (VRPTW)** model to optimize the logistics from the Brooklyn Navy Yard depot to **20 Trader Joe's locations** across NYC.

### Key Objectives
* **Minimize Costs:** Reduce total operational costs (transportation + spoilage penalties).
* **Reduce Congestion:** Incorporate **Off-Hour Delivery (OHD)** incentives.
* **Ensure Freshness:** Model deterioration rates (**10-15% loss** during delivery) to prioritize product quality.

---

## ⚙️ Methodology & Tech Stack

The system combines Python-based data engineering with rigorous Operations Research modeling.

### 1. Data Acquisition (Tech Stack)

* **Web Crawling (`Selenium`):**
    Scraped dynamic geospatial data for all 20 NYC Trader Joe's locations to build the demand nodes.

* **Distance Matrix (`OSRM`):**
    Integrated the **Open Source Routing Machine API** to calculate realistic non-Euclidean travel times and distances, accounting for NYC's complex one-way street grid and traffic patterns.

### 2. Mathematical Modeling (MILP)

The core logic is built on **Mixed-Integer Linear Programming**. Below represents the mathematical formulation derived for this study.

#### **A. Inputs, Parameters & Decision Variables**
> *Defining the sets (Depot, Customers), vehicle capacity constraints, and flow variables.*

<img width="1037" height="493" alt="1" src="https://github.com/user-attachments/assets/e4b01d7f-69dd-41aa-b02e-f9a1e2889ef5" />

#### **B. Benchmark System Formulation**
> *The baseline model focuses purely on distance minimization without time constraints.*

<img width="1110" height="326" alt="2" src="https://github.com/user-attachments/assets/034f346f-89ee-45be-8a41-126dffb8ea17" />


#### **C. Alternative System Formulation (VRPTW)**
> *The optimized model introduces Time Windows ($[a_i, b_i]$) and Penalty Costs to account for freshness and OHD incentives.*

<img width="1038" height="300" alt="3" src="https://github.com/user-attachments/assets/b33c122b-a434-4be1-ab8f-2e77d6e8ccff" />


---

## 📊 Results & Impact

The model compared a baseline scenario against our time-window optimized solution. While the optimized route increased total distance (to avoid traffic/wait for windows), it significantly reduced the **Generalized Cost** (Operational + Spoilage).

<img width="960" height="508" alt="result_1" src="https://github.com/user-attachments/assets/a6107f2d-6975-452c-8758-b9b5d467135a" />

<img width="1211" height="468" alt="result_2" src="https://github.com/user-attachments/assets/c1eba123-b620-4db8-9dbf-861235faf9bf" />


> **💡 Insight:** The optimization proves that **shortest distance $\neq$ lowest cost**. By accepting longer routes to adhere to Off-Hour Delivery windows, the system reduces "Turn and Burn" waste and capitalizes on NYC's night delivery incentives.

---

## 📜 Context

* **Course:** Urban Transportation & Logistics Systems Modeling
* **Date:** Oct 2024 – Jan 2025
* **Authors:** Archy Guo, Sizhe Xu
