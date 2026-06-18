# Training Strategy Analysis for Lightweight Pneumonia Detection Under Cross-Hospital Distribution Shift

This repository contains the source code, preprocessing workflow, experimental notebook, figures, result files, and artifact documentation for the study **“Training Strategy Analysis for Lightweight Pneumonia Detection Under Cross-Hospital Distribution Shift.”**

The project analyzes how different training strategies affect the robustness of a lightweight MobileNetV2-based pneumonia detection model under cross-hospital distribution shift. NIH ChestX-ray14 is used as the source domain, while the Guangzhou chest X-ray dataset is used as the external test domain.

## Project Overview

This study compares three training strategies using the same MobileNetV2 backbone:

1. **Frozen Baseline**
   The MobileNetV2 backbone is frozen, and only the classification head is trained.

2. **Partial Fine-Tuning**
   The last 30 layers of MobileNetV2 and the classification head are unfrozen.

3. **Full Fine-Tuning with Class Weighting and Light Augmentation**
   All layers are trainable, with inverse-frequency class weighting and light augmentation applied to the training set.

The goal is to isolate the effect of training strategy while keeping the backbone architecture fixed.

## Repository Structure

```text
cross-hospital-pneumonia-training-strategy/
├── data/
│   └── README.md
├── figures/
│   └── experiment figures and plots
├── models/
│   └── README.md
├── notebooks/
│   └── full experimental notebook
├── preprocessing/
│   └── preprocessing workflow
├── results/
│   └── evaluation result CSV files
├── .gitignore
├── README.md
└── requirements.txt
```

## Project Artifacts

This repository documents several artifacts produced during the experiment:

| Artifact Type                | Location           | Description                                                                                                 |
| ---------------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------- |
| Experimental Notebook        | `notebooks/`       | Full notebook used for model training, evaluation, threshold calibration, and analysis                      |
| Preprocessing Workflow       | `preprocessing/`   | Preprocessing workflow for preparing the external Guangzhou dataset                                         |
| Figures                      | `figures/`         | Generated plots and visual outputs from the experiment                                                      |
| Result Files                 | `results/`         | CSV files containing evaluation metrics, calibrated results, performance drop, and confusion matrix outputs |
| Dataset Documentation        | `data/README.md`   | Dataset access notes and expected local folder structure                                                    |
| Model Artifact Documentation | `models/README.md` | Notes on trained model artifacts and external storage location                                              |

Raw datasets and trained `.h5` model files are not uploaded directly to this repository due to file size limitations. They are documented through the `data/` and `models/` folders.

## Datasets

This project uses two public chest X-ray datasets:

* **NIH ChestX-ray14** as the source domain
* **Guangzhou Chest X-ray Dataset** as the external test domain

The raw datasets are not included directly in this repository due to file size limitations. Dataset access and local folder structure are explained in `data/README.md`.

## Model Artifacts

The trained model artifacts are not included directly in this repository because the `.h5` files can be large. Model storage information and folder structure are explained in `models/README.md`.

Each strategy originally contains:

* `.json` file for model architecture
* `.h5` file for trained model weights

## Experimental Outputs

This repository includes:

* Full experimental notebook
* Guangzhou preprocessing workflow
* Five generated figures from the experiment
* Four CSV result files
* Documentation for dataset and model artifact access

## Method Summary

The experiment uses:

* MobileNetV2 with ImageNet pretraining
* Input size of 224 × 224 × 3
* Binary pneumonia classification
* NIH ChestX-ray14 as the source domain
* Guangzhou Hospital dataset as the external test domain
* Patient-level NIH split with 70/15/15 ratio
* NIH validation-based threshold calibration
* NIH-to-Guangzhou performance drop analysis

## Requirements

Install the required dependencies using:

```bash
pip install -r requirements.txt
```

## How to Run

1. Download the required datasets and place them according to the structure described in `data/README.md`.
2. Install the required dependencies using `requirements.txt`.
3. Open the notebook in the `notebooks/` folder.
4. Run the preprocessing workflow if needed.
5. Run the experimental notebook to train, evaluate, and generate results.
6. Check the `figures/` and `results/` folders for output files.

## Results

The experiment compares the performance of Frozen Baseline, Partial Fine-Tuning, and Full Fine-Tuning with Class Weighting and Light Augmentation across NIH and Guangzhou domains.

The result files include evaluation metrics, calibrated performance, performance drop analysis, and confusion matrix-related outputs.

## Medical Disclaimer

This project is intended for academic research and experimental analysis only. The model is not intended for clinical deployment, medical diagnosis, or direct decision-making in real healthcare settings.

## Authors

* Collyne
* Erlitna Natasya Debora

## Supervisors

* Rico Halim
* Bakti Amirul Jabar


