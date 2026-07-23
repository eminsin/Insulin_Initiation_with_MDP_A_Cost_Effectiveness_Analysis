---



<p align="center">
  <img width="600" height="500" alt="image_summary of the project" src="https://github.com/user-attachments/assets/ecf10500-7412-4c89-b4ff-d26289c9795c" />
</p>

<h1 align="center">Insulin Initiation with MDP A Cost-Effectiveness Analysis</h1>



---

[![LINK](https://img.shields.io/badge/Hop%20to%20IEEE%20Wonderland-8A2BE2)](https://ieeexplore.ieee.org/document/9270187)



---

## 🎯 Project Overview
My graduation dissertation (2019) develops a **_finite-horizon Markov Decision Process (MDP)_** that determines the **_optimal timing for initiating insulin therapy_** in Type 2 Diabetes Mellitus (T2DM) by integrating disease progression, treatment history, costs, and quality-adjusted life years (QALYs). It provides a **_decision-support framework_** that reduces clinical inertia, improves patient outcomes, and minimizes healthcare expenditures.


---

## 🐛 Problem Context and Motivation
Type 2 Diabetes is a rapidly growing global health burden, responsible for escalating healthcare costs, increased risk of cardiovascular, renal, and ocular complications, significant reductions in quality of life.
Although insulin is highly effective in achieving glycemic control, its initiation is often delayed due to patient, clinician, and systemic barriers. This delay -known as clinical inertia- leads to prolonged hyperglycemia and higher complication risks. My thesis addresses the central question: _"When is the optimal time to initiate insulin therapy for a T2DM patient, given their health state and treatment history?"_ This is a complex decision under uncertainty - perfect for mathematical modeling.

---

## 🔬 Laboratory

**1. Markov Decision Process (MDP) Construction**  

The core analytical engine of the thesis is a **finite‑horizon Markov Decision Process** designed to model treatment progression in Type 2 Diabetes. The MDP is defined by:  

_State Space Design_  
Each health state (with the priority of weight-control, no comorbidity presence) is a structured tuple combining:
+ HbA1c control status
+ BMI category
+ Drug‑use history (metformin, dual therapy, triple therapy)  

_Action Set_  
Three clinically relevant actions:
+ Wait in the current therapy
+ Add new oral glucose‑lowering agent 
+ Initiate insulin therapy

_Transition Probabilities_  
Transition matrices for each action were estimated from the medical publications that quantify:
+ HbA1c reduction per therapy class
+ BMI‑related risk changes
+ Insulin effectiveness and hypoglycemia risk
+ Failure rates of metformin, dual therapy, and triple therapy

These probabilities satisfy the Markov property:

```math
\sum_{j} p_{ij}(a) = 1
```  

_Finite Horizon_  
The model is evaluated for 20 years between 40 and 60 years of age.  
Decision epochs are set to 6‑month intervals, reflecting guideline‑recommended follow‑up frequency.

**2. Reward Function Construction**  

The reward function integrates **clinical utility** and **economic cost**, forming a health‑economic objective:  

```math
R(s,a) = \text{QALY}(s,a) - \text{Cost}(s,a)
```
QALYs are computed using:

```math
QALY = u(s,a) \cdot \Delta t
```

_Components:_

+ QALY Estimation
  + Baseline utilities for each health state
  + Utility gains from improved HbA1c under each therapy
  + Disutility penalties for uncontrolled HbA1c and therapy side effects (weight gain)

  QALYs are discounted using a factor consistent with health‑economic standards.

+ Cost Modelling  

  Costs are grouped in three main categories: 
  1) total medical cost (inpatient, outpatient, emergency room visits, urgent care visits, calls to physicians)
  2) total drug (medication) cost
  3) total cost of weight increase which may occur as an effect of the therapies.

+ Monetary Valuation of QALYs  

  QALYs are converted to monetary units using a willingness‑to‑pay threshold (e.g., $50,000 per QALY), enabling unified reward scaling.

**3. Policy Optimization**  

The optimal policy is computed via **backward induction**:

```math
V_t(s) = \max_{a \in A} \left[ R(s,a) + \sum_{s'} p_{ss'}(a) \, V_{t+1}(s') \right]
```
where:

- *V*<sub>t</sub>(s) : value of state *s* at decision epoch *t*
- *A* : set of available actions
- *R(s,a)* : reward combining QALYs and costs
- *p<sub>ss'</sub>(a)* : transition probability from state *s* to *s'* under action *a*

This dynamic programming approach yields:
+ Optimal action per state:  
The optimal policy $\pi^*$ selects the best action for each state:

```math
\pi^*(s) = \arg\max_{a \in A} \left[ R(s,a) + \sum_{s'} p_{ss'}(a) V_{t+1}(s') \right]
```

+ Value function trajectories

**4. Sensitivity Analysis Framework**  

To test robustness, the thesis performs **one‑way sensitivity analyses** on:
+ Triple therapy cost
+ Disutility of uncontrolled HbA1c
+ Discount factor
+ QALY monetary value
+ Starter utility of insulin therapy
+ Metformin therapy cost 
+ Patient vs payer perspective

Each scenario re‑runs the MDP to observe shifts in optimal insulin timing.

**5. Data Sources & Parameterization**  

Parameters were derived from:
+ ADA and EASD guidelines
+ UKPDS, ACCORD, and other landmark trials
+ Published HbA1c reduction estimates for MET, SU, GLP‑1 RA, SGLT2i, DPP‑4i, insulin
+ Cost data from ADA (2018) and US healthcare expenditure reports
+ Utility values from validated QALY literature

**6. Computational Implementation**  

The results are obtained from the MATLAB R2018b computer program.  
Although the repo does not specify code for now, the modelling implicitly uses:
+ Matrix‑based cohort simulation
+ Dynamic programming loops for value iteration
+ Numerical handling of discounting and reward aggregation
+ Structured state enumeration 



---

## 🧠 Results

🧮 Controlling weight is almost as important as blood sugar control

🧮 The effect of cost and QALY gains on initiation of insulin, which varies according to the type of therapy, demonstrates the importance of the type of therapy used

🧮 The uncontrolled HbA1c and BMI values together negates the type of dual therapy used after a certain age (58 years) and makes it important to start insulin directly

🧮 The use of GLP1 RA is not preferred because it is injectable and more expensive than SGLT 2i

🧮 Unlike the other types of therapy, insulin therapy causes a reduction in a patient's QALY in total from year to year because of its weight gain effect

🧮 For the triple therapy, the result has changed at a cost of $ 500 instead of $ 2000

🧮 In order to see the effet of non-control of HbA1c level, the results were evaluated for lower and higher values than the value we considered (0.16). It was found that a disutility up to 0.07 does not actually make a difference with the absence of it. Early insulin initiation is recommended for a larger value of 0.25, while direct insulin initiation has been detected in dual and triple therapies for a high value of 0.50 

🧮 By testing the discount factor, it was observed that if the value is between 0.81 and 0.80, it may be advisable to eliminate the difference between dual therapies and start insulin directly after 40 years of age.

🧮 It was observed that doubling the putative cost-effectiveness ratio resulted in initiating insulin treatment earlier, and when it was quadrupled, the individual should stay on the dual therapy if (s)he uses a dual therapy and more wait action would make sense in general

🧮 The results were seen when the larger, compared to other starter utilities (0.68 and 0.80), insulin initiation starter utility (0.813) had an occasional value. While the results of the base case already represent the value for greater than 0.80, it was tested by assigning a value of 0.70 as it would be difficult to start insulin if it was less than 0.68

🧮 The fact that monotherapy with much lower cost than other costs resulted in continuous wait action led us to see how the result changes if we accept this value close to other values. As a result, it was suggested action 𝐴, which can be considered more logical, for the health state of mono therapy when the two parameters (HbA1c and BMI) are not under control

🧮 the changes in the optimal policy were observed when the perspective is changed to the patient perspective by resetting the cost of all types of therapies. In this way, it was determined how the perspective can make big differences in optimal policy

... to be continued

---

## 📂 Folder Structure



---

## 🛠 Built With

`MATLAB` `R (to come)`


---

## 🌱 Inspired By

---



## 🤝 Connect

Feel free to reach out or star this repo!

Let’s learn together. 🌱
