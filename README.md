# EchoEF-Net: Automated Ejection Fraction Estimation from Echocardiographic Segmentation using Deep Learning and Calibration

**Author:** Khaled Mohammed Elzekarey Elrefaey, MBBS  
**Independent Researcher**  
**Target Journal:** Frontiers in Cardiovascular Medicine  
**Date:** November 2025  

---

## 🧠 Overview
**EchoEF-Net** is a deep learning pipeline implemented entirely in a single **Jupyter Notebook (`.ipynb`)** for automated estimation of left-ventricular ejection fraction (LVEF) from echocardiographic segmentation using the **CAMUS dataset**.  
The notebook trains a segmentation model, computes ejection fractions from LV cavity contours, and applies a **calibration step** to enhance agreement with reference measurements.

---

## 📊 Key Results
| Stage | MAE (%) | Bias (%) | SD (%) | LoA | r | R² |
|:------|:---------|:----------|:--------|:----------------|:--:|:--:|
| Pre-calibration | 6.30 [5.54,7.07]  | 3.32 [1.98,4.60]  | 6.71  | [-9.84,16.47]  | 0.847 | 0.717 |
| Post-calibration | 4.98 [4.24,5.78] | -0.01 [-1.26,1.19] | 6.40 | [-12.55,12.54] | 0.845 | 0.714 |

> Calibration reduces systematic bias and improves clinical reliability of EF prediction.

---

## ⚙️ Notebook Contents

1. **Data Loading and Preprocessing**
   - Imports and processes the **CAMUS dataset** (2- and 4-chamber views).
   - Splits data into training, validation, and test sets.

2. **Model Architecture**
   - Implements segmentation models using **Segmentation Models PyTorch (SMP)**.
   - Supports configurable encoders such as ResNet and EfficientNet.
   - Loss: Dice + Cross-Entropy.

3. **Training and Validation**
   - Displays training progress with loss curves.
   - Automatically saves best-performing model checkpoints.

4. **Ejection Fraction Computation**
   - Calculates EF via **Simpson’s biplane formula** using segmented LV cavities.

5. **Calibration and Evaluation**
   - Computes metrics: MAE, Bias, SD, Limits of Agreement, Pearson’s *r*, and R².

6. **Visualization**
   - Scatter plots and Bland–Altman plots (pre/post calibration).

---

## 🧰 How to Run

### Requirements
- Python ≥ 3.9  
- Jupyter Notebook / JupyterLab  
- PyTorch ≥ 2.0  
- segmentation-models-pytorch  
- OpenCV, NumPy, Pandas, Matplotlib, SciPy  

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/KhaledElrefaey/EchoEF-Net.git
   cd EchoEF-Net
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Launch the notebook:
   ```bash
   jupyter notebook EchoEF-Net.ipynb
   ```
4. Run all cells to reproduce training, EF estimation, and evaluation.

---

## 📈 Example Outputs

| Example | Description |
|:--|:--|
| ![Scatter Plot](./1.png) | Predicted vs. Ground Truth EF Pre-Processing|
| ![Scatter Plot](./2.png) | Predicted vs. Ground Truth EF Post-Processing|
| ![Scatter Plot](./3.png) | Predicted vs. Ground Truth EF Pre- AND Post-Calibration|
| ![Bland-Altman](./4.png) | Bland–Altman Pre-Processing |
| ![Bland-Altman](./5.png) | Bland–Altman Post-Processing |
| ![Bland-Altman](./6.png) | Bland–Altman after calibration |
| ![Training Curve](./7.png) | Training and validation losses |

LV segmentation (ED/ES frames) 2 CH and 4 CH Views (Examples)

|:--|
| ![Segmentation Results](./8.png) |
| ![Segmentation Results](./9.png) |
| ![Segmentation Results](./10.png) |
| ![Segmentation Results](./11.png) |
| ![Segmentation Results](./12.png) |
| ![Segmentation Results](./13.png) |
---

## 🧬 Citation
If you use this notebook, please cite:
```
Elrefaey, K. M. E. (2025). EchoEF-Net: Automated Ejection Fraction Estimation from Echocardiographic Segmentation using Deep Learning and Calibration. *Frontiers in Cardiovascular Medicine*. Under Review.
```

---

## 📜 License
This project is released under the **MIT License**.  
Free for academic and non-commercial use with attribution.

---

## ❤️ Acknowledgments
- **CAMUS Dataset:** Leclerc et al., *Medical Image Analysis*, 2019.  
- Built with **PyTorch** and **Segmentation Models PyTorch (SMP)**.  
- Dedicated to open, reproducible AI research in echocardiography.

---
