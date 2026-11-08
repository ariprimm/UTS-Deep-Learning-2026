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

- Dataset owner: Alvin Kurniawan Hanafie (`alvinhanafie`)
- Source: [Kaggle — Dataset for Indonesian Sentiment Analysis](https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis)
- Language: Indonesian
- Sentiment classes: Negative, Neutral, Positive
- License shown on Kaggle: Apache 2.0

### Dataset Files

| File | Initial rows | Role in this project |
|---|---:|---|
| `train_preprocess_ori.tsv` | 11,000 | Labeled source data used to create the training and internal validation subsets |
| `valid_preprocess.tsv` | 1,260 | Labeled evaluation data, kept separate from model training and checkpoint selection |
| `test_preprocess_masked_label.tsv` | 500 | Unlabeled texts used for inference only |

The dataset contains two columns: `text` (the Indonesian text) and `sentiment` (the sentiment label). The masked-label file contains placeholder values rather than usable ground-truth labels; therefore, it is not used to calculate evaluation metrics.

### Data Preparation

The original training file contained 11,000 rows. Preprocessing removed 67 duplicate texts and 14 texts that overlapped with the labeled evaluation file, leaving 10,919 records. This pool was split using a stratified 90:10 split:

- Training subset: 9,827 records
- Internal validation subset: 1,092 records
- Separate labeled evaluation file: 1,260 records
- Unlabeled inference file: 500 records

The vocabulary was built from the training subset only. Sequences were padded or truncated to 80 tokens.

## Model Architecture

The implemented architecture is:

`Embedding → LSTM → Dropout → Fully Connected → 3-class Classification`

The model uses a single-layer, unidirectional LSTM. The final hidden state is passed through dropout and a fully connected layer to produce logits for the three sentiment classes.

### Hyperparameters

| Hyperparameter | Value |
|---|---:|
| Vocabulary size | 8,492 |
| Embedding dimension | 128 |
| Hidden size | 128 |
| LSTM layers | 1 |
| Dropout | 0.5 |
| Maximum sequence length | 80 tokens |
| Batch size | 64 |
| Learning rate | 0.001 |
| Maximum epochs | 15 |
| Optimizer | Adam |
| Loss function | Weighted CrossEntropyLoss |
| Early stopping patience | 3 |
| Gradient clipping | 1.0 |
| Random seed | 42 |

## Experimental Results

The model was evaluated on the 1,260 labeled records from `valid_preprocess.tsv`. This is a separate labeled evaluation file; it is not the official masked Kaggle test set.

| Metric | Result |
|---|---:|
| Accuracy | 86.03% |
| Macro Precision | 0.8042 |
| Macro Recall | 0.8517 |
| Macro F1-Score | 0.8241 |
| Weighted F1-Score | 0.8630 |
| Best Epoch | 4 |
| Best Validation Loss | 0.4375 |

### F1-Score by Class

| Sentiment | F1-Score |
|---|---:|
| Negative | 0.8160 |
| Neutral | 0.7475 |
| Positive | 0.9087 |

Training stopped at epoch 7 through early stopping. The checkpoint with the lowest internal validation loss was selected from epoch 4. The rising validation loss after epoch 4 indicates a degree of overfitting during later epochs.

## Repository Structure

```text
UTS-Deep-Learning-2026/
│
├── README.md
├── .gitignore
├── requirements.txt
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

Open `UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb` in Jupyter Notebook or Google Colab.

You can also open it directly in Google Colab:

[Open Notebook in Google Colab](https://colab.research.google.com/github/ariprimm/UTS-Deep-Learning-2026/blob/main/UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb)

### 4. Prepare the Dataset

Keep all three TSV files inside the `dataset/` directory. The notebook searches the working directory and the `dataset/` directory for these files.

### 5. Run the Notebook

Execute the cells sequentially to perform dataset inspection, preprocessing, tokenization, vocabulary construction, sequence encoding, LSTM training, evaluation, and inference on unlabeled texts.

## Dataset Attribution

Dataset: **Dataset for Indonesian Sentiment Analysis** by Alvin Kurniawan Hanafie (`alvinhanafie`).

Original source: [Kaggle dataset page](https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis)

The Kaggle page displays the Apache 2.0 license. Refer to the original dataset page for the applicable license terms and attribution requirements.

## Author

**Arif Prima Rahadian**  
Information Systems  
Institut Teknologi PLN  
Class C — 2026

Individual academic project for the Deep Learning course.
