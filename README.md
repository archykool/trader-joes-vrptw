🌸 Trader Joe's NYC Flower Logistics Optimization

Applying Operations Research to optimize the "Cold Chain" for fresh flower delivery in NYC.
Achieved a 31.5% cost reduction by implementing time-window penalties and Off-Hour Delivery (OHD) incentives.

📖 Project Overview

Trader Joe's relies on a "Turn and Burn" strategy for its high-turnover floral inventory. However, the lack of precise transportation planning leads to significant wastage due to traffic delays and deterioration.

This project develops a Vehicle Routing Problem with Time Windows (VRPTW) model to optimize the logistics from the Brooklyn Navy Yard depot to 20 Trader Joe's locations across NYC.

Key Objectives:

Minimize total operational costs (transportation + spoilage penalties).

Incorporate Off-Hour Delivery (OHD) incentives to reduce congestion.

Ensure freshness by modeling deterioration rates (10-15% loss during delivery).

⚙️ Methodology & Tech Stack

The system combines Python-based data engineering with rigorous Operations Research modeling.

1. Data Acquisition (Tech Stack)

Web Crawling (Selenium): Scraped dynamic geospatial data for all 20 NYC Trader Joe's locations to build the demand nodes.

Distance Matrix (OSRM): Integrated the Open Source Routing Machine API to calculate realistic non-Euclidean travel times and distances, accounting for NYC's complex one-way street grid and traffic patterns.

2. Mathematical Modeling (MILP)

The core logic is built on Mixed-Integer Linear Programming. Below represents the mathematical formulation derived for this study.

A. Inputs, Parameters & Decision Variables

Defining the sets (Depot, Customers), vehicle capacity constraints, and flow variables.

<!-- 建议插入 PPT 中关于 Parameters & Sets 的那张截图 -->

<div align="center">
<img src="./assets/slides/parameters_slide.png" alt="Model Parameters" width="90%">
</div>

B. Benchmark System Formulation

The baseline model focuses purely on distance minimization without time constraints.

<!-- 建议插入 PPT 中 Benchmark System Objective Function 的那张截图 -->

<div align="center">
<img src="./assets/slides/benchmark_slide.png" alt="Benchmark Formulation" width="90%">
</div>

C. Alternative System Formulation (VRPTW)

The optimized model introduces Time Windows ($[a_i, b_i]$) and Penalty Costs to account for freshness and OHD incentives.

<!-- 建议插入 PPT 中 Alternative System (Time Penalty) 的那张截图 -->

<div align="center">
<img src="./assets/slides/alternative_system_slide.png" alt="Alternative System Formulation" width="90%">
</div>

📊 Results & Impact

The model compared a baseline scenario against our time-window optimized solution. While the optimized route increased total distance (to avoid traffic/wait for windows), it significantly reduced the Generalized Cost (Operational + Spoilage).

<插图>
<插图>

Insight: The optimization proves that shortest distance $\neq$ lowest cost. By accepting longer routes to adhere to Off-Hour Delivery windows, the system reduces "Turn and Burn" waste and capitalizes on NYC's night delivery incentives.

📜 Context

Course: Urban Transportation & Logistics Systems Modeling

Date: Oct 2024 – Jan 2025

Authors: Archy Guo, Sizhe Xu