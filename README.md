# Fraud Detection

End-to-End ML project (Python Training → Java Serving) to detect fraudulent credit card transactions on an extremely imbalanced dataset. It demonstrates various machine learning fundamentals (loss functions, gradient descent, class imbalance handling, evaluation metrics).  The model is exported to ONNX, where Java Spring Boot is used for for serving predictions.  

---

## Problem Statement

Fraudulent credit card transactions are rare but costly. In the Kaggle dataset used here, only 0.17% of all transactions are fraud.  

A naïve model that predicts no fraud for every case would achieve 99.8% accuracy but would be useless.  

**Business Goal:**  
- Detect fraud with high recall (catch as many frauds as possible) while keeping false alarms at an acceptable level.  

**Success Metrics:**  
- **ML Metrics:** Recall ≥ 90% with Precision ≥ 70% (evaluated on validation/test set).  
- **Business Framing:** Balance cost of false negatives (missed fraud) vs false positives (legitimate customers flagged).  

For a detailed discussion, see [docs/problem_statement.md](docs/problem_statement.md).

---


