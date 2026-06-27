# NetGuard AI — ML-Powered Network Intrusion Detection System

##  Overview
NetGuard AI is a machine learning–based Network Intrusion Detection System (NIDS) that 
classifies network traffic as **normal** or **anomalous** (malicious). The model was 
trained using IBM Watson Studio's **AutoAI** and deployed on **IBM Cloud (Watson Machine 
Learning)** for real-time predictions.

This project was built as part of the Edunet Foundation problem statement:
> **Problem Statement No.40 – Network Intrusion Detection**

##  Problem Statement
Create a robust network intrusion detection system using machine learning that analyzes 
network traffic data to identify and classify various types of cyber-attacks (DoS, Probe, 
R2L, U2R) and distinguish them from normal network activity, enabling early warning of 
malicious activity.

##  Dataset
- **Source:** [NSL-KDD Network Intrusion Detection Dataset (Kaggle)](https://www.kaggle.com/datasets/sampadab17/network-intrusion-detection)
- **Records:** ~125,973 training samples
- **Features:** 41 network traffic features (duration, protocol_type, flag, src_bytes, dst_bytes, etc.)
- **Target column:** `class` — binary (`normal` / `anomaly`)

##  Tech Stack
- **IBM Watson Studio** — AutoAI experiment for automated model building
- **IBM Watson Machine Learning** — model deployment & REST endpoint
- **Snap Decision Tree Classifier** — best-performing pipeline (selected by AutoAI)
- Python, scikit-learn, pandas

##  Approach
1. Loaded and explored the NSL-KDD dataset in IBM Watson Studio.
2. Ran an **AutoAI experiment** with `class` as the prediction column.
3. AutoAI generated 8 candidate pipelines (Snap Decision Tree & Decision Tree, with 
   feature engineering + hyperparameter optimization).
4. Selected the top-ranked pipeline (**P2**) based on optimized accuracy.
5. Deployed the model as an online deployment on IBM Cloud.
6. Tested the deployed endpoint with realistic traffic samples (normal HTTP session vs. 
   DoS/neptune-style attack pattern) to validate predictions.

##  Results
- Model type: Binary Classification
- Test case (normal HTTP traffic pattern): **Predicted "normal" — 100% confidence**

  Prediction Results :

  ![Prediction Results]("netguard-ai-intrusion-detection\step-4 (result).png"))
  

##  How to Reproduce
1. Download the dataset from the Kaggle link above.
2. Open `notebook/netguard_ai_pipeline.ipynb` in Jupyter or IBM Watson Studio.
3. Run all cells to retrain the pipeline.
4. Deploy via IBM Watson Machine Learning, or adapt the model for local inference.

##  Author
Built by Sharon Elango as part of the Edunet Foundation / IBM SkillsBuild AI program (2026).
```
