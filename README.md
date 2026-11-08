# Indonesian Sentiment Analysis Using LSTM

Individual UTS Project — Deep Learning  
Institut Teknologi PLN | 2026

## About the Project

This project implements Indonesian text sentiment classification using a Long Short-Term Memory (LSTM) neural network with PyTorch.

The model classifies Indonesian text into three sentiment categories:

- Positive
- Negative
- Neutral

The project covers dataset exploration, text preprocessing, vocabulary construction, sequence encoding, LSTM architecture, model training, and performance evaluation.

## Project Information

| Information | Details |
|---|---|
| Student | Arif Prima Rahadian |
| Student ID | 202432107 |
| Class | C |
| Institution | Institut Teknologi PLN |
| Study Program | Information Systems |
| Course | Deep Learning |
| Algorithm | Long Short-Term Memory (LSTM) |
| Framework | PyTorch |
| Task | Multiclass Sentiment Classification |

## Dataset

**Dataset for Indonesian Sentiment Analysis**

- Dataset Owner: Alvin Kurniawan Hanafie (`alvinhanafie`)
- Source: [Kaggle — Dataset for Indonesian Sentiment Analysis](https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis)
- Language: Indonesian
- Sentiment Classes: Negative, Neutral, Positive
- License displayed on Kaggle: Apache 2.0

### Dataset Files

| File | Initial Rows | Role in This Project |
|---|---:|---|
| `train_preprocess_ori.tsv` | 11,000 | Labeled source data for training and internal validation |
| `valid_preprocess.tsv` | 1,260 | Separate labeled evaluation data |
| `test_preprocess_masked_label.tsv` | 500 | Unlabeled texts used for inference |

The dataset contains two columns: `text` (Indonesian text) and `sentiment` (sentiment label).

The masked-label file contains placeholder values rather than usable ground-truth labels. Therefore, it is used for inference only and not for calculating evaluation metrics.

### Data Preparation

The original training file contained 11,000 rows. Preprocessing removed 67 duplicate texts and 14 texts that overlapped with the labeled evaluation file, leaving 10,919 records.

This remaining data was divided using a stratified 90:10 split:

- Training subset: 9,827 records
- Internal validation subset: 1,092 records
- Separate labeled evaluation file: 1,260 records
- Unlabeled inference file: 500 records

The vocabulary was built using the training subset only. Sequences were padded or truncated to a maximum length of 80 tokens.

## Model Architecture

The implemented architecture consists of:

`Embedding → LSTM → Dropout → Fully Connected → 3-class Classification`

The model uses a single-layer, unidirectional LSTM. The final hidden state is passed through dropout and a fully connected layer to produce classification logits for the three sentiment categories.

### Hyperparameters

| Hyperparameter | Value |
|---|---:|
| Vocabulary Size | 8,492 |
| Embedding Dimension | 128 |
| Hidden Size | 128 |
| LSTM Layers | 1 |
| Dropout | 0.5 |
| Maximum Sequence Length | 80 tokens |
| Batch Size | 64 |
| Learning Rate | 0.001 |
| Maximum Epochs | 15 |
| Optimizer | Adam |
| Loss Function | Weighted CrossEntropyLoss |
| Early Stopping Patience | 3 |
| Gradient Clipping | 1.0 |
| Random Seed | 42 |

## Experimental Results

The model was evaluated using 1,260 labeled records from `valid_preprocess.tsv`. This file was kept separate from model training and checkpoint selection.

### Overall Performance

| Metric | Result |
|---|---:|
| Accuracy | 86.03% |
| Macro Precision | 0.8042 |
| Macro Recall | 0.8517 |
| Macro F1-Score | 0.8241 |
| Weighted F1-Score | 0.8630 |
| Best Epoch | 4 |
| Best Internal Validation Loss | 0.4375 |

### F1-Score by Class

| Sentiment | F1-Score |
|---|---:|
| Negative | 0.8160 |
| Neutral | 0.7475 |
| Positive | 0.9087 |

Training stopped at epoch 7 through early stopping. The model checkpoint with the lowest internal validation loss was selected from epoch 4.

The increase in validation loss after epoch 4 indicates a degree of overfitting during the later training epochs.

**Evaluation Note:** These metrics represent evaluation on the separate labeled validation file, not the official masked Kaggle test set.

## Repository Structure

```text
UTS-Deep-Learning-2026/
│
├── README.md
├── .gitignore
├── requirements.txt
│
├── UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb
│
└── dataset/
    ├── train_preprocess_ori.tsv
    ├── valid_preprocess.tsv
    └── test_preprocess_masked_label.tsv
```

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/ariprimm/UTS-Deep-Learning-2026.git
cd UTS-Deep-Learning-2026
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Open the Notebook

Open the notebook using Jupyter Notebook or Google Colab:

`UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb`

You can also open it directly in Google Colab:

[Open Notebook in Google Colab](https://colab.research.google.com/github/ariprimm/UTS-Deep-Learning-2026/blob/main/UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb)

### 4. Prepare the Dataset

Ensure that all three TSV files are available inside the `dataset/` directory.

### 5. Run the Notebook

Execute all notebook cells sequentially to perform:

- Dataset inspection
- Text preprocessing
- Tokenization and vocabulary construction
- Sequence encoding and padding
- LSTM model training
- Model evaluation
- Sentiment prediction on unlabeled texts

## Dataset Attribution

**Dataset:** Dataset for Indonesian Sentiment Analysis  
**Owner:** Alvin Kurniawan Hanafie (`alvinhanafie`)

Original source:

https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis

The Kaggle page displays the Apache 2.0 license. Please refer to the original dataset page for the applicable license terms and attribution requirements.

## Author

**Arif Prima Rahadian**  
Information Systems  
Institut Teknologi PLN  
Class C — 2026

Individual academic project for the Deep Learning course.
