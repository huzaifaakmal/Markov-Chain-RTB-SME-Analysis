# Bridging the Marketing-Operations Interface: A Markov Decision Framework for SME Retargeting, Ad Fatigue Mitigation, and Demand Forecasting

## 📌 Project Overview
This repository contains the data pipeline, Markov Chain models, and statistical analyses for the research project: **"Bridging the Marketing-Operations Interface: A Markov Decision Framework for SME Retargeting, Ad Fatigue Mitigation, and Demand Forecasting."**

While existing literature on Real-Time Bidding (RTB) heavily focuses on algorithmic bidding optimization, this project translates consumer state transitions into actionable financial metrics for resource-constrained Small and Medium Enterprises (SMEs). 

By analyzing over 1.1 million impressions, this code models consumer dynamics (Exposed, Clicked, Converted, and Fatigued) to mathematically prove Customer Acquisition Cost (CAC) reductions, model the "Ad Fatigue Penalty," and provide accelerated demand signals for logistics and inventory management.

## 📊 Key Empirical Findings
*   **173.2x CAC Reduction:** The Realized Cost Per Click (CPC) drops from 98.02 RMB (Cold users) to 0.57 RMB (Warm/Retargeted users).
*   **The Ad Fatigue Penalty:** After 3 consecutive exposures without a click, the probability of a fatigued user clicking crashes to 0.38% (with a 99.62% chance of remaining fatigued). 
*   **Operations/Demand Forecasting:** Transitioning a user to the "Clicked" state reduces the expected touchpoints to conversion by 18.9% (from 1,732 to 1,406), providing faster demand signals for logistics.
*   **Zero-Leakage Validation:** Out-of-sample testing (Train: March 11; Test: March 12) yielded an absolute prediction error of only 0.0004.

## 📁 Dataset
Due to GitHub's file size limits, the raw iPinYou Real-Time Bidding dataset (6.3 GB) is not included in this repository. 
*   **Dataset Source:** [iPinYou Global RTB Bidding Algorithm Competition Dataset](http://data.computational-advertising.org/) or via Kaggle.
*   **Required Files:** The pipeline specifically uses `imp.20130311.txt.bz2`, `clk.20130311.txt.bz2`, `conv.20130311.txt.bz2`, and the March 12 test files. 

## 🛠️ Repository Structure
*   `Verify_Markov_Chain_RTB_Analysis.ipynb`: The master Jupyter Notebook containing the complete, leakage-free data pipeline from raw log extraction to statistical testing and visualization.
*   `Figure_RQ1_Training_Matrix.png`: Heatmap of the baseline Markov transition probabilities.
*   `Figure_RQ2_Regional_Context.png`: Bar chart of geographical variance in click probabilities.
*   `Figure_RQ3_SME_Strategy.png`: Bar chart illustrating the 173.2x Realized CPC reduction.
*   `Figure_RQ4_Testing_Matrix.png`: Heatmap of the out-of-sample validation matrix.
*   `Figure_5_3State_Diagram.png`: Network diagram of the Exposed → Clicked → Converted funnel.
*   `Figure_6_Ad_Fatigue_Penalty.png`: Bar chart illustrating the drop in conversion probability for fatigued users.

## 🚀 How to Run the Code
1. Clone this repository.
2. Download the iPinYou dataset and place the `.bz2` files in a local directory.
3. Update the `folder_path` variable in the first cell of the Jupyter Notebook to point to your local directory.
4. Install the required dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy scikit-learn networkx
5. Run all cells in Verify_Markov_Chain_RTB_Analysis.ipynb.

## 📝 Methodology Highlights
Markov Chains: Used to calculate state transition probabilities via frequency matrices and row normalization.

Chi-Square Test: Proved statistical significance of state dependency (p < 0.0000).

3-State Conversion Model: Utilized the Markov Fundamental Matrix (I - Q)^-1 to calculate expected touchpoints to conversion.

Machine Learning Metrics: Evaluated predictive validity using scikit-learn (Accuracy, Precision, Recall, F1-Score) to handle class imbalance in RTB data.