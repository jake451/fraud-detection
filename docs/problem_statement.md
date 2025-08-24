# Problem Statement — Fraud Detection

## 1. Business Context
Fraudulent credit card transactions are rare but highly costly.  
In the dataset used here (Kaggle Credit Card Fraud Detection), only 0.17% of transactions are fraudulent.  

- **Fraudulent transactions (positives):** direct financial loss to the bank or merchant.  
- **Legitimate transactions (negatives):** most of the dataset.  

A naïve model that predicts “no fraud” for every case achieves 99.8% accuracy, but detects zero fraud.  Accuracy is therefore misleading for imbalanced problems.  

---

## 2. Business Goals
- Detect fraudulent transactions with high recall (catch as many frauds as possible).  
- Keep false alarms (false positives) at an acceptable level to avoid harming customers and support teams.  

**Business trade-offs:**  
- **False Negative (missed fraud):** high monetary cost; fraud loss absorbed by bank/merchant.  
- **False Positive (false alarm):** customer inconvenience, lost revenue from declined transactions, support center costs.  

Missing fraud (FN) is usually more costly than false alarms (FP). Therefore, recall is prioritized in metric design.  

---

## 3. Success Metrics

### ML Metrics
- **Recall ≥ 90%** → We want to catch at least 9 out of 10 frauds.  
- **Precision ≥ 70%** → Of flagged cases, at least 7/10 should be truly fraud.  
- **Evaluation sets:** Validation and test splits only (to avoid overfitting).  

### Business Metrics
- Reduction in fraud-related losses.  
- Acceptable customer experience (false alarms do not exceed support team thresholds).  
- Balance between recall (safety) and precision (usability).  

---

## 4. Confusion Matrix in Fraud Context

|                      | **Predicted Fraud** | **Predicted Normal** |
|----------------------|----------------------|-----------------------|
| **Actual Fraud**     | True Positive (TP)<br/>✔ Fraud caught | False Negative (FN)<br/>❌ Fraud missed |
| **Actual Normal**    | False Positive (FP)<br/>❌ False alarm (legit customer blocked) | True Negative (TN)<br/>✔ Correct pass |

- **TP:** Correctly flagged fraud.  
- **FN:** Missed fraud (most costly).  
- **FP:** False alarm (customer frustration, revenue loss).  
- **TN:** Correctly ignored normal transaction.  

---

## 5. Why 90% Recall / 70% Precision?
- **Recall ≥ 90%** → Fraud team requires catching almost all fraud. Missing too many cases = unacceptable risk.  
- **Precision ≥ 70%** → Ensures customers aren’t overwhelmed by false alarms. If precision dropped too low (e.g. 20%), users would lose trust.  
- These thresholds balance risk control (high recall) with customer experience (acceptable precision).  
- In real business settings, these thresholds are chosen through stakeholder alignment and cost analysis (fraud loss vs support cost).  

---

## 6. Constraints
- Predictions must run in real-time (fraud detection happens before approving a transaction).  
- Feature engineering must match between Python training and Java serving.  
- Models must be maintainable (periodic retraining to adapt to evolving fraud patterns).  

---

## 7. Out of Scope (for this project)
- Real-time transaction streaming (Kafka, Flink).  
- Integration with bank customer support systems.  
- Model retraining automation (MLOps pipelines).  

These could be considered as future extensions.  

---

## 8. References
- [Kaggle Credit Card Fraud Detection Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)  

---
