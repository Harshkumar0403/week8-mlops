### Analysis & Mitigation
📌 Impact of Label Poisoning on Model Performance

Label poisoning introduces incorrect labels into the training set, confusing the Decision Tree during splits.
Observations from results:

* At 5% poisoning


     - Slight drop in accuracy

     - F1 score mostly stable

     - Model still generalizes well

*  At 10% poisoning

     - Clear performance degradation

     - Decision boundaries begin to shift incorrectly

* At 50% poisoning

     - Model becomes nearly random

     - Accuracy collapses

     - F1 score extremely low

     - MLflow UI clearly shows a steep degradation trend

     - Poisoning attacks directly harm decision boundaries, making class separation ineffective.







### How to Mitigate Poisoning Attacks

1. Outlier / Anomaly Detection

   - Detect mislabeled samples using:

   - Isolation Forest

   - kNN distance

   - Model disagreement (cross-ensemble filtering)

2. Use Robust Training Techniques
  
   - Label smoothing
  
   - Noise-robust loss (Generalized Cross Entropy)
  
   - Confidence-based reweighting

3. Data Provenance Tracking

   - Version datasets using DVC
  
   - Maintain audit logs of data sources

4. Increase Dataset Size
   - When quality drops, quantity must increase:
  
   - To overcome 10% poisoning → require ~30–50% more clean samples
  
   - At 50% poisoning → nearly impossible without external clean data
  
5. Human-in-the-loop Monitoring
   - Manual review of mislabeled clusters based on embeddings.
