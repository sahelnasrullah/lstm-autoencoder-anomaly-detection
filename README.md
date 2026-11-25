# LSTM Autoencoder Anomaly Detection (Network Intrusion)

Deep Learning coursework (BTH) in TensorFlow/Keras and scikit-learn.

Two LSTM autoencoders (a simple and a deeper one) are trained only on **normal** network traffic. Connections that are reconstructed poorly (high reconstruction error) are flagged as anomalies. The threshold is derived from the reconstruction errors on normal training data. An Isolation Forest is used as the baseline.

## Pipeline
1. Preprocessing: one-hot encoding of categorical columns, MinMax scaling, reshaping into LSTM input
2. Two LSTM autoencoder architectures trained with reconstruction loss
3. Threshold selection and anomaly detection by reconstruction error
4. Evaluation: Precision, Recall, F1, ROC-AUC on a held-out test set (5,039 rows)
5. Baseline comparison with Isolation Forest

## Results
| Model | Precision | F1 | ROC-AUC |
|---|---|---|---|
| LSTM autoencoders | ~0.94 | ~0.945 | 0.9835 – 0.9890 |
| Isolation Forest (baseline) | 0.634 | 0.776 | 0.979 |

The Isolation Forest reaches perfect recall only by flagging far too many rows, which hurts precision.

## Files
- `final_assignment2.ipynb` – code and outputs
- `Assignment2_Report.pdf` – full report

## Running
Get the *Network Intrusion Detection* dataset (`Train_data.csv`) from Kaggle and place it at `archive/Train_data.csv`. The dataset is not included in this repository.

```bash
pip install tensorflow pandas numpy scikit-learn matplotlib
jupyter notebook final_assignment2.ipynb
```
