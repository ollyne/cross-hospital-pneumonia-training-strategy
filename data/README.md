# Data Access

This folder documents the dataset access and local data structure used in the experiment.

The raw datasets are not included directly in this repository due to file size limitations. To reproduce the experiment, users need to download the datasets separately and organize them according to the expected folder structure.

## Datasets Used

This study uses two public chest X-ray datasets:

1. **NIH ChestX-ray14**
   Used as the source domain for training, validation, and in-domain testing.

2. **Guangzhou Chest X-ray Dataset**
   Used as the external test domain for cross-hospital evaluation.

## Dataset Role

| Dataset                       | Role            | Usage                                       |
| ----------------------------- | --------------- | ------------------------------------------- |
| NIH ChestX-ray14              | Source domain   | Training, validation, and in-domain testing |
| Guangzhou Chest X-ray Dataset | External domain | External-domain testing only                |

Guangzhou is never used during training, validation, or threshold calibration.

## NIH ChestX-ray14 Summary

The NIH binary subset used in this experiment contains:

```text id="vr63fd"
21,431 total images
1,431 pneumonia cases
20,000 non-pneumonia cases
6.7% pneumonia prevalence
```

NIH is split at the patient level using a 70/15/15 ratio to prevent data leakage.

## Guangzhou Dataset Summary

The full Guangzhou dataset contains:

```text id="3juyjh"
5,856 total images
4,273 pneumonia cases
1,583 normal cases
```

For external evaluation, this study uses the official Guangzhou test split:

```text id="q0wjam"
624 total images
390 pneumonia cases
234 normal cases
62.5% pneumonia prevalence
```

## Expected Local Folder Structure

During experimentation, the local data directory followed this structure:

```text id="wgjnox"
data/
├── Guangzhou/
│   ├── normal/
│   └── pneumonia/
└── NIH/
    ├── images/
    ├── labels/
    └── metadata/
```

The exact internal structure may be adjusted depending on the downloaded dataset format, but the notebook assumes that the NIH and Guangzhou files are organized consistently before training and evaluation.

## Label Mapping

The binary label mapping used in this experiment is:

```text id="92yvg1"
Pneumonia     → positive class (y = 1)
Non-pneumonia → negative class (y = 0)
Normal        → negative class (y = 0)
```

For NIH ChestX-ray14, the negative class is defined as non-pneumonia and may include other thoracic findings.

For Guangzhou, the negative class contains only normal cases.

This label difference is important when interpreting cross-domain performance.

## Storage Note

The dataset files are stored externally because they are too large to be uploaded directly to GitHub.

Project storage folder:

```text id="hv5u7t"
https://drive.google.com/drive/folders/1wXuTQR8qDd8qdzgtl5DJp6W54WkJ8d1d?usp=drive_link
```

## Reproducibility Note

To reproduce the experiment:

1. Download the required datasets.
2. Place the files according to the expected local folder structure.
3. Run the preprocessing workflow if needed.
4. Open the experimental notebook in the `notebooks/` folder.
5. Run the notebook to train, evaluate, and generate results.
