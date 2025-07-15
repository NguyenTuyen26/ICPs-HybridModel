# Hybrid_CNN_BiLSTM_ICP

## Overview

Immune checkpoint proteins (ICPs) are essential regulators of immune responses and have become pivotal targets in cancer immunotherapy. In this project, we introduce a deep learning framework for ICP function prediction based on primary amino acid sequences.

Our approach integrates a hybrid architecture combining Convolutional Neural Networks (CNN) and Bidirectional Long Short-Term Memory networks (BiLSTM), designed to capture both local motifs and long-range dependencies within protein sequences. To further enrich the sequence representation, we utilize Evolutionary Scale Modeling (ESM) — a pretrained protein language model that captures deep semantic and structural features from raw sequences.

The proposed CNN+BiLSTM model, empowered by ESM-based embeddings, achieves high predictive performance. On an independent test set, it reached an **accuracy of 0.9807**, **MCC of 0.9499**, **sensitivity of 0.9912**, **specificity of 0.9745**, and **AUC of 0.9986**.

These results underscore the potential of combining protein language models with deep learning architectures for sequence-based protein function classification, and offer promising directions for automated functional annotation and immunotherapeutic target discovery.

---

## Methodology

We collect protein sequences and their corresponding labels (1 for ICP, 0 for non-ICP) in CSV format. Each row contains a protein ID, its amino acid sequence, and its label.

These sequences are processed using the ESM model to extract high-dimensional embeddings, which are saved as CSV files and used as input features.

The model is trained in the notebook `Buid_HybridModel_ICP_ESM.ipynb`, found in the `model/` directory. This notebook constructs the CNN-BiLSTM architecture and trains it using the labeled data.

To evaluate robustness, we perform k-fold cross-validation using `CV_HybridModel.ICP_ESM.ipynb`, assessing metrics such as ACC, AUC, SN, SP, and MCC.

Final generalization is evaluated on an independent test set using `ID_Hybrid.ICP_ESM.ipynb`, which applies the trained model to unseen sequences.

---

## Dependencies

- Google Colab or Jupyter Notebook environment
- Python ≥ 3.10
- Required libraries:
  - torch
  - pandas
  - numpy
  - scikit-learn
  - matplotlib

Install with:
```bash
pip install torch pandas numpy scikit-learn matplotlib
```

