# Antimicrobial Peptide Classification Using Protein Sequence Features

## COLAB
https://colab.research.google.com/drive/1PXrH_456vbON3IA9W43z-7QgNt2Fr6rv?usp=sharing


## Overview

Antimicrobial Peptides (AMPs) are short protein sequences that play a crucial role in the innate immune system by inhibiting the growth of bacteria, fungi, viruses, and other pathogens. Due to the increasing threat of antibiotic resistance, AMP prediction has become an important research topic in bioinformatics and computational biology.

This project aims to build a machine learning pipeline that classifies protein sequences as either Antimicrobial Peptides (AMPs) or Non-Antimicrobial Peptides (Non-AMPs) using sequence-based features extracted from FASTA files.

The project explores whether simple sequence-derived features can effectively distinguish AMP sequences from non-AMP sequences and compares the performance of several machine learning algorithms.

---

## Research Question

**Can protein sequence features be used to accurately distinguish antimicrobial peptides from non-antimicrobial peptides?**

---

## Objectives

- Build a complete bioinformatics classification pipeline.
- Extract informative features from protein sequences.
- Train machine learning models for AMP prediction.
- Compare model performance using multiple evaluation metrics.
- Analyze the characteristics of antimicrobial peptide sequences.

---

## Dataset

The dataset is obtained from the AMPlify benchmark dataset and contains experimentally verified antimicrobial peptides and non-antimicrobial peptide sequences.

### Positive Samples (AMP)

| File |
|--------|
| AMPlify_AMP_train_common.fa |
| AMPlify_AMP_test_common.fa |

### Negative Samples (Non-AMP)

| File |
|--------|
| AMPlify_non_AMP_train_balanced.fa |
| AMPlify_non_AMP_test_balanced.fa |

### Label Definition

| Label | Description |
|---------|---------|
| 1 | Antimicrobial Peptide (AMP) |
| 0 | Non-Antimicrobial Peptide (Non-AMP) |

---

## Dataset Statistics

| Category | Training Set | Testing Set |
|------------|------------|------------|
| AMP | TBD | TBD |
| Non-AMP | TBD | TBD |
| Total | TBD | TBD |

---

## Methodology

### Workflow

```text
Protein Sequences (FASTA)
            │
            ▼
     Data Preprocessing
            │
            ▼
     Feature Extraction
            │
            ▼
      Model Training
            │
            ▼
      Model Evaluation
            │
            ▼
      Result Analysis
```

---

## Data Preprocessing

The preprocessing stage consists of:

1. Reading FASTA files.
2. Extracting protein sequences.
3. Removing invalid characters.
4. Assigning class labels.
5. Combining datasets.
6. Preparing training and testing datasets.

### Example FASTA Sequence

```text
>AMP_001
GLFDIIKKIAESF
```

After preprocessing:

| Sequence | Label |
|-----------|---------|
| GLFDIIKKIAESF | 1 |

---

## Feature Extraction

Machine learning models cannot directly process amino acid sequences. Therefore, protein sequences must be converted into numerical feature vectors.

### Amino Acid Composition (AAC)

AAC measures the frequency of each amino acid within a sequence.

Example:

```text
Sequence:
GLFDIIKKIAESF
```

Feature vector:

| A | C | D | E | F | G | H | I | K | L | M | N | P | Q | R | S | T | V | W | Y |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0.08|0|0.08|0.08|0.15|0.08|0|0.23|0.15|0.08|0|0|0|0|0|0.08|0|0|0|0|

---

### Dipeptide Composition (DPC) *(Optional)*

DPC captures local sequence-order information by counting adjacent amino acid pairs.

Example:

```text
GL
LF
FD
DI
II
IK
KK
```

DPC contains 400 possible amino acid pair combinations.

---

## Machine Learning Models

The following machine learning models will be evaluated:

### Logistic Regression

A linear classification model used as the baseline.

### Random Forest

An ensemble learning algorithm that combines multiple decision trees.

### Support Vector Machine (SVM)

A powerful classifier that performs well in high-dimensional feature spaces.

---

## Evaluation Metrics

Model performance is evaluated using:

### Accuracy

Measures overall classification performance.

\[
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
\]

### Precision

Measures prediction reliability.

\[
Precision = \frac{TP}{TP + FP}
\]

### Recall

Measures detection capability.

\[
Recall = \frac{TP}{TP + FN}
\]

### F1-Score

Harmonic mean of Precision and Recall.

\[
F1 = \frac{2 \times Precision \times Recall}{Precision + Recall}
\]

### Confusion Matrix

Provides detailed information about classification results.

---

## Experimental Setup

### Environment

| Component | Version |
|------------|------------|
| Python | 3.10+ |
| Scikit-Learn | Latest |
| NumPy | Latest |
| Pandas | Latest |
| BioPython | Latest |
| Matplotlib | Latest |

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-repository/AMP-Classification.git
cd AMP-Classification
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

### Step 1: Data Preprocessing

```bash
python src/preprocessing.py
```

### Step 2: Feature Extraction

```bash
python src/features.py
```

### Step 3: Model Training

```bash
python src/models.py
```

---

## Project Structure

```text
AMP-Classification
│
├── data
│   ├── raw
│   │   ├── AMPlify_AMP_train_common.fa
│   │   ├── AMPlify_AMP_test_common.fa
│   │   ├── AMPlify_non_AMP_train_balanced.fa
│   │   └── AMPlify_non_AMP_test_balanced.fa
│   │
│   └── processed
│       ├── train.csv
│       └── test.csv
│
├── notebooks
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_feature_extraction.ipynb
│   └── 03_model_training.ipynb
│
├── src
│   ├── preprocessing.py
│   ├── features.py
│   └── models.py
│
├── results
│   ├── metrics.csv
│   ├── confusion_matrix.png
│   └── figures
│
├── presentation
│   └── Final_Presentation.pptx
│
├── requirements.txt
│
└── README.md
```

---

## Results

### Model Performance

| Model | Accuracy | Precision | Recall | F1-Score |
|---------|---------|---------|---------|---------|
| Logistic Regression | TBD | TBD | TBD | TBD |
| Random Forest | TBD | TBD | TBD | TBD |
| SVM | TBD | TBD | TBD | TBD |

---

## Discussion

This study investigates whether sequence-based features can effectively identify antimicrobial peptides.

Potential observations include:

- Certain amino acids may occur more frequently in AMP sequences.
- Sequence composition may provide useful discriminative information.
- Different machine learning models may exhibit varying performance characteristics.
- Feature engineering can significantly influence prediction accuracy.

---

## Future Work

Possible extensions include:

### Deep Learning Approaches

- Convolutional Neural Networks (CNN)
- Long Short-Term Memory Networks (LSTM)
- Transformer-based Models

### Protein Language Models

- ESM2 Embeddings
- ProtBERT Embeddings

### Generative AI

- Synthetic AMP Generation
- Novel Peptide Candidate Discovery

### Advanced Features

- Physicochemical Properties
- Pseudo Amino Acid Composition (PseAAC)
- Evolutionary Information

---

## Team Members

| Member | Responsibility |
|-----------|-----------|
| Member A | Background Research & Motivation |
| Member B | Dataset Collection & Preprocessing |
| Member C | Feature Extraction |
| Member D | Model Training & Evaluation |
| Member E | Results Analysis, Presentation & GitHub Integration |

---

## References

1. AMPlify: Attentive Deep Learning Model for Antimicrobial Peptide Discovery
2. Antimicrobial Peptide Database (APD)
3. DRAMP: Data Repository of Antimicrobial Peptides
4. BioPython Documentation
5. Scikit-Learn Documentation

---

## License

This project is developed for academic and educational purposes.

---

## Acknowledgements

We would like to thank the creators of the AMPlify dataset and the open-source bioinformatics community for providing valuable datasets and tools that made this project possible.
