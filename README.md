# GraphCodeBERT Code Similarity Analysis Project

This repository provides a **sample project for training and inference of a code similarity classification model** based on **GraphCodeBERT**.  
The original experimental code written in Jupyter notebooks has been refactored into a **modular Python package** to improve readability, reusability, and maintainability.

---

## 🔥 Project Objectives

- **Code preprocessing and pair generation**  
  Provide utilities such as `remove_extras` to remove comments and unnecessary whitespace from source code, and generate positive/negative code pairs for training.

- **GraphCodeBERT-based classifier**  
  Implement a code similarity prediction model by wrapping HuggingFace’s `AutoModelForSequenceClassification` with GraphCodeBERT as the backbone.

- **Modular training and inference pipeline**  
  Define training, validation, and inference routines in `src/trainer.py`, and execute them via top-level scripts that read YAML configuration files.

- **Easy experiment control**  
  Adjust data paths, hyperparameters, and model save/load settings through `configs/train.yaml` and `configs/submit.yaml` without modifying source code.

---

## 📂 Directory Structure

    graphcodebert_project/
    ├── src/
    │   ├── __init__.py           # Package initialization
    │   ├── utils.py              # Seed fixing and code preprocessing utilities
    │   ├── dataset.py            # CodePairDataset and dataset construction helpers
    │   ├── model.py              # GraphCodeBERT classifier wrapper
    │   └── trainer.py            # Training, validation, and inference routines
    │
    ├── train.py                  # Training entry script
    ├── inference.py              # Inference entry script
    ├── configs/
    │   ├── train.yaml            # Training configuration
    │   └── submit.yaml           # Inference configuration
    ├── requirements.txt          # Required Python packages
    ├── assets/
    │   ├── model1.pt             # Example model weights (placeholder)
    │   └── model2.pt             # Example model weights (placeholder)
    ├── data/
    │   ├── train.csv             # Training dataset (example)
    │   ├── test.csv              # Test dataset (example)
    │   └── sample_submission.csv # Example submission format
    ├── .gitignore                # Files and directories ignored by Git
    └── .gitattributes            # Git attributes (e.g., LFS settings)

---

## 🚀 Getting Started

### Environment Setup

Python **3.9 or later** is recommended.  
Install required dependencies from the project root:

    pip install -r requirements.txt

---

### Training

After preparing the training dataset, run the following command to train the model.  
All training-related settings can be modified in `configs/train.yaml`.

    python train.py --config configs/train.yaml

---

### Inference

To generate predictions on the test set using trained model weights, run:

    python inference.py --config configs/submit.yaml

The inference script supports loading **one or multiple model checkpoints**, optionally ensembling their predictions, and outputs results in the format defined by `sample_submission.csv`.

---

## Notes

- `assets/model1.pt` and `assets/model2.pt` are provided as placeholders.  
  Replace them with actual trained model weights when running inference.
- `data/train.csv` and `data/test.csv` contain simple example code pairs and labels.  
  For real use cases, replace these files with your own datasets.
- The training and inference pipelines are intentionally kept simple.  
  You can extend them by customizing loss functions, evaluation metrics, or data loaders as needed.
