# ECG Classification Project
Automated multilabel classification of ECG waveforms using CNN, ResNet, and Transformer architectures on MIMIC-IV-ECG data

# Automated Multilabel ECG Classification

---

## Contributors
- [@nikita-bedi](https://github.com/nikita-bedi)
- [@cginder](https://github.com/cginder)
- [@mondira17](https://github.com/mondira17)
- [@ounlu](https://github.com/ounlu)

## Project Overview

Electrocardiograms (ECGs) are among the most commonly performed diagnostic procedures in medicine, with over 10 million conducted annually in the United States. However, ECG interpretation remains challenging—even for experienced clinicians. Studies have shown that manual interpretation accuracy hovers around **45–60% for non-cardiology healthcare professionals** and approximately **50% among physicians**.

This project aims to develop **automated, multilabel ECG classification models** that can predict multiple cardiac diagnoses from raw waveform data. Our work explores various deep learning architectures to identify the optimal approach for robust and generalizable ECG interpretation.

---

## Dataset

We used the **MIMIC-IV-ECG** dataset, available through PhysioNet. This is a large, real-world clinical dataset comprising:

- **800,000 ECGs from 160,000 patients**
- **90GB total size (33GB compressed)**


### 🔍 Dataset Components

1. **`record_df`**: Raw ECG waveform data (voltage-time signals from inpatient, outpatient, and emergency settings).
2. **`measure_df`**: Machine-generated ECG measurements (e.g., RR interval, QTc).
3. **`outcomes_df`**: Diagnostic labels and outcomes, including ICD-10 codes and mortality data.

**Note** Due to data use regulations, the raw data for this project cannot be shared publicly. You can request access to the MIMIC-IV-ECG dataset via PhysioNet by completing the required data use agreements and credentialing.

---

## Models

We experimented with a variety of deep learning models to evaluate performance across several metrics, including AUC, AUPRC, and balanced accuracy.

### Architectures

- **Vanilla CNN**
- **Autoencoder + MLP Classifier**
- **CNN-LSTM Hybrid**
- **ResNet1D**
- **Transformer Classifier**
- **Transformer-CNN Hybrid**

---

## Results & Insights

**ResNet1D** delivered the strongest overall performance, offering a strong balance of generalization and robustness. Its residual connections improved training stability and allowed the model to capture both local waveform features and global contextual information across ECG sequences.

While **CNN-LSTM** performed well on classes with temporal patterns (e.g., **Premature Atrial Complex - PAC**), **ResNet1D** consistently outperformed on the majority of diagnoses.

Transformer-based models **underperformed**, and the hybrid model—while better—still lagged behind the simpler residual architecture.

---

## Files Included

- `EDA.ipynb`: Contains exploratory data analysis code.
- `ECG_Models.ipynb`: Contains model development, training, and evaluation code.
- `model_histories/`: Folder contatining training logs and metrics (e.g., accuracy, loss, AUC).
- `saved_models/`: Folder containing the final model files (`.keras`) for deployment or fine-tuning.

---

## Conclusion

For multilabel ECG diagnosis on an imbalanced, real-world dataset, **ResNet1D** provided the most reliable performance and is our recommended architecture.

This project was completed as part of **AC209B at Harvard University**.

---

## References

1. Drazen E, Mann N, Borun R, Laks M, Bersen A. Survey of computer-assisted electrocardiography in the United States. J Electrocardiol. 1988;21:S98-S104. doi:10.1016/0022-0736(88)90068-4
2. Kashou AH, Noseworthy PA, Beckman TJ, et al. ECG Interpretation Proficiency of Healthcare Professionals. Curr Probl Cardiol. 2023;48(10):101924. doi:10.1016/j.cpcardiol.2023.101924
3. Cook DA, Oh SY, Pusic MV. Accuracy of Physicians’ Electrocardiogram Interpretations: A Systematic Review and Meta-analysis. JAMA Intern Med. 2020;180(11):1461-1471. doi:10.1001/jamainternmed.2020.3989
4. McKeen, K., Oliva, L., Masood, S., Toma, A., Rubin, B. and Wang, B.
McKeen, K., Oliva, L., Masood, S., Toma, A., Rubin, B., & Wang, B. (2024). ECG-FM: An Open Electrocardiogram Foundation Model. Retrieved from https://arxiv.org/abs/2408.05178


