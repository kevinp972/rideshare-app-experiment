# Driver Incentive Program Evaluation

This repository contains an in-depth analysis of a ride-sharing platform’s incentive program rollout. The goal is to measure its effectiveness in increasing driver engagement using advanced causal inference techniques, including A/B testing, Difference-in-Differences (DiD), and Instrumental Variables (IV) to address endogeneity and estimate treatment effects.

## Project Overview

In an A/B testing framework, a subset of drivers were offered the opportunity to enroll in an incentive program via email. This project analyzes the program's impact on **daily minutes driven**, comparing outcomes between treated and control groups while accounting for selection bias and staggered enrollment.

The analysis follows these key steps:

1. **Experimental Design & Data Preparation**
   - Cleaned and merged driver activity and enrollment data
   - Constructed variables: treatment assignment, application/enrollment status, and time since experiment start

2. **Intent-to-Treat (ITT) Estimation**
   - Used DiD regression to estimate the effect of simply being offered the incentive
   - Included fixed effects (City × Experiment Start Date and Calendar Date) for robust within-cohort comparisons

3. **Addressing Endogeneity with IV (Two-Stage Least Squares)**
   - Recognized that self-selection into enrollment biases estimates
   - Used **treatment assignment** as an instrument for **actual enrollment** to estimate the **Treatment-on-the-Treated (TOT)** effect

4. **Strategic Implications**
   - Interpreted results in the context of platform labor supply constraints
   - Suggested targeting recommendations and marketing spend benchmarks based on estimated return per enrollee

## Key Results

| Effect Type | Estimate (Δ Minutes Driven) |
|-------------|-----------------------------|
| ITT         | +2.09%                      |
| TOT (IV)    | +17.9%                      |

> The incentive program significantly increases driver activity *among those who enroll*, highlighting the importance of boosting take-up to unlock impact.

## Methodologies Used

- A/B Testing
- Difference-in-Differences (DiD)
- Instrumental Variables (2SLS)
- Fixed Effects Regression (City × Experiment Start Date × Date)
- Concept: Semi-Log Model

## Strategic Takeaways

- The program is promising in **supply-constrained cities**.
- Improving **application/enrollment rates** is key to maximizing ROI.
- Ongoing monitoring is necessary as **take-up rates and effects may vary over time**.
- Results can be connected to **labor elasticity estimates** to guide city-level marketing investments.

## Files in This Repo

- `Causal-Effect-Estimation---Part-1.ipynb` – Main analysis using A/B Testing, DiD and Fixed Effects Regression
- `Causal-Effect-Estimation---Part-2.Rmd` – IV regressions (R, using `fixest`)
- `Causal-Effect-Estimation---Part-2.pdf` – The rendered version of the R Markdown File (**View this if you don't have R installed.**)
- `README.md` – This file

## 🙏 Acknowledgments

This project was inspired by a homework dataset from Professor **Keith Chen’s** class at UCLA Anderson. His engaging teaching on causal inference and experimentation motivated this deeper exploration into program impact and platform strategy.
