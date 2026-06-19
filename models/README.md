# Model Artifacts

This folder documents the trained model artifacts produced during the experiment.

The actual model files are not uploaded directly to this repository because the `.h5` weight files can be large. Instead, the model artifacts are stored externally in the project storage folder.

## Model Strategies

This experiment produces model artifacts for three training strategies:

1. **Frozen Baseline**
   The MobileNetV2 backbone is frozen, and only the classification head is trained.

2. **Partial Fine-Tuning**
   The last 30 layers of MobileNetV2 and the classification head are unfrozen.

3. **Full Fine-Tuning with Class Weighting and Light Augmentation**
   All layers are trainable, with inverse-frequency class weighting and light augmentation applied during training.

## Expected Model Folder Structure

During experimentation, the model artifacts were organized using the following structure:

```text id="u97is8"
models/
├── strategy_1_frozen_baseline/
│   ├── model_architecture.json
│   └── model_weights.h5
├── strategy_2_partial_finetuning/
│   ├── model_architecture.json
│   └── model_weights.h5
└── strategy_3_full_ft_cw_aug/
    ├── model_architecture.json
    └── model_weights.h5
```

## Artifact Description

Each strategy folder contains:

| File                      | Description                                 |
| ------------------------- | ------------------------------------------- |
| `model_architecture.json` | Stores the model architecture configuration |
| `model_weights.h5`        | Stores the trained model weights            |

The `.json` file defines the model structure, while the `.h5` file stores the trained weights generated during the experiment.

## Storage Note

The trained model files are stored externally due to file size limitations.

Project storage folder:

```text id="ns2wld"
https://drive.google.com/drive/folders/1WrYVQ7sOpG_e6kch5d5xwWGLjGsj3gSk?usp=drive_link
```

## Usage Note

To reproduce the experiment or load the trained models:

1. Download the model artifacts from the project storage folder.
2. Place the folders inside the local `models/` directory.
3. Make sure the structure matches the expected folder structure above.
4. Run the experimental notebook in the `notebooks/` folder.

## Reproducibility Note

The models were trained using the same MobileNetV2 backbone and shared experimental settings. The main difference across model artifacts is the training strategy applied to the backbone.
