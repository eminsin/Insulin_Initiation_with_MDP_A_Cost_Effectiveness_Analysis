---



<p align="center">
  <img width="600" height="500" alt="image_summary of the project" src="https://github.com/user-attachments/assets/ecf10500-7412-4c89-b4ff-d26289c9795c" />
</p>

<h1 align="center">Insulin Initiation with MDP A Cost-Effectiveness Analysis</h1>



---

[![LINK](https://img.shields.io/badge/Hop%20to%20IEEE%20Wonderland-8A2BE2)](https://ieeexplore.ieee.org/document/9270187)



---

## 🎯 Project Overview
The thesis develops a **_finite-horizon Markov Decision Process (MDP)_** that determines the **_optimal timing for initiating insulin therapy_** in Type 2 Diabetes Mellitus (T2DM) by integrating disease progression, treatment history, costs, and quality-adjusted life years (QALYs). It provides a **_decision-support framework_** that reduces clinical inertia, improves patient outcomes, and minimizes healthcare expenditures.


---

## 🐛 Problem Context and Motivation
Type 2 Diabetes is a rapidly growing global health burden, responsible for escalating healthcare costs, increased risk of cardiovascular, renal, and ocular complications, significant reductions in quality of life.
Although insulin is highly effective in achieving glycemic control, its initiation is often delayed due to patient, clinician, and systemic barriers. This delay -known as clinical inertia- leads to prolonged hyperglycemia and higher complication risks. My thesis addresses the central question: _"When is the optimal time to initiate insulin therapy for a T2DM patient, given their health state and treatment history?"_ This is a complex decision under uncertainty - perfect for mathematical modeling.

---

## 🔬 Laboratory

**1. Markov Decision Process (MDP) Construction**  
The core analytical engine of the thesis is a **finite‑horizon Markov Decision Process** designed to model treatment progression in Type 2 Diabetes. The MDP is defined by:  

_State Space Design_  
Each health state is a structured tuple combining:
+ HbA1c control status
+ BMI category
+ Comorbidity presence (ASCVD, CKD, HF)
+ Current therapy stage (metformin, dual therapy, triple therapy)  
+ Drug‑use history

These elements are explicitly listed in Table 4.1.1 and Table 4.1.2 of the thesis.

_Action Set_  
Three clinically relevant actions:
+ Wait
+ Add new oral glucose‑lowering agent
+ Initiate insulin therapy

_Transition Probabilities_  
Transition matrices for each action (Tables 4.2.1.2–4.2.1.4) were estimated using:
+ Published clinical progression rates
+ HbA1c response distributions for MET, dual, and triple therapy
+ Insulin initiation response data
+ BMI‑linked risk adjustments

These probabilities satisfy the Markov property:

**formula**

_Finite Horizon_  
Decision epochs are set to 6‑month intervals, reflecting guideline‑recommended follow‑up frequency.

**2. Reward Function Construction**  
The reward function integrates clinical utility and economic cost, forming a health‑economic objective:  

**formula**

<ins>Components:</ins>

_QALY Estimation_
+ Baseline utilities for each health state (Table 4.2.2.1)
+ Utility gains from improved HbA1c under each therapy (Table 4.2.2.2)
+ Disutility penalties for uncontrolled HbA1c and therapy side effects (Table 4.2.2.3)

QALYs are discounted using a factor consistent with health‑economic standards.

_Cost Modelling_  
Annualized direct medical costs for:
+ Metformin
+ Dual therapy
+ Triple therapy
+ Insulin therapy
(Table 4.2.3.1)

Costs include medication, monitoring, and complication‑related expenditures.

_Monetary Valuation of QALYs_  
QALYs are converted to monetary units using a willingness‑to‑pay threshold (e.g., $100,000 per QALY), enabling unified reward scaling.

**3. Policy Optimization**  
The optimal policy is computed via **backward induction**:

**formula**

This dynamic programming approach yields:
+ Optimal action per state (Table 5.1.1)
+ Value function trajectories (Table 5.1.2)

**4. Sensitivity Analysis Framework**  
To test robustness, the thesis performs **one‑way sensitivity analyses** on:
+ Triple therapy cost (±$500–$1000)
+ Disutility of uncontrolled HbA1c (0.25 → 0.50)
+ Discount factor (0.80 → 0.81)
+ QALY monetary value ($100k → $200k)
+ Patient vs payer perspective (Table 5.2.11)

Each scenario re‑runs the MDP to observe shifts in optimal insulin timing.

**5. Data Sources & Parameterization**  
Parameters were derived from:
+ ADA and EASD guidelines
+ UKPDS, ACCORD, and other landmark trials
+ Published HbA1c reduction estimates for MET, SU, GLP‑1 RA, SGLT2i, DPP‑4i
+ Cost data from ADA (2018) and US healthcare expenditure reports
+ Utility values from validated QALY literature

**6. Computational Implementation**  
Although the thesis does not specify code, the modelling implicitly uses:
Matrix‑based cohort simulation
Dynamic programming loops for value iteration
Numerical handling of discounting and reward aggregation
Structured state enumeration based on Table 4.1.2







---

## 📂 Folder Structure



---

## 🧠 Notebook Topics

### 🧮 1.

### 🧮 2.

### 🧮 3.

### 🧮 4.



---

## 🛠 Built With




---

## 🌱 Inspired By

---



## 🤝 Connect

Feel free to reach out or star this repo!

Let’s learn together. 🌱
