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
| Pre-calibration | 7.31 [6.35–8.29] | +4.38 [2.78–5.77] | 7.80 | [-10.90, 19.65] | 0.807 | 0.651 |
| Post-calibration | **5.39 [4.51–6.34]** | **–0.03 [–1.49, 1.27]** | 7.21 | [–14.16, 14.10] | 0.799 | 0.638 |

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
   - Applies linear or isotonic calibration.
   - Computes metrics: MAE, Bias, SD, Limits of Agreement, Pearson’s *r*, and R².

6. **Visualization**
   - Training curves, scatter plots, and Bland–Altman plots (pre/post calibration).

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
   jupyter notebook Deep_Learning_with_PyTorch_ImageSegmentation.ipynb
   ```
4. Run all cells to reproduce training, EF estimation, and evaluation.

---

## 📈 Example Outputs

| Example | Description |
|:--|:--|
| ![Segmentation Results](./1.png) | LV segmentation (ED/ES frames) |
| ![Scatter Plot](./3.png) | Predicted vs. Reference EF |
| ![Bland-Altman](./4.png) | Bland–Altman before calibration |
| ![Calibrated Results](./5.png) | Improved agreement after calibration |
| ![Training Curve](./6.png) | Training and validation losses |

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
