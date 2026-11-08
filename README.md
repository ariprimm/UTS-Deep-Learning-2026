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

- Dataset Owner: Alvin Kurniawan Hanafie
- Source: [Kaggle Dataset](https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis)
- Language: Indonesian
- Classes: Positive, Negative, Neutral
- License displayed on Kaggle: Apache 2.0

### Dataset Files

| File | Description |
|---|---|
| `train_preprocess_ori.tsv` | Original labeled training data |
| `valid_preprocess.tsv` | Original labeled validation data |
| `test_preprocess_masked_label.tsv` | 500 unlabeled texts for inference |

The masked-label file does not contain usable ground-truth sentiment labels. Therefore, it is used for prediction only, not model evaluation.

## Model Architecture

The implemented architecture consists of:

`Embedding → LSTM → Dropout → Fully Connected → Classification`

### Hyperparameters

| Hyperparameter | Value |
|---|---:|
| Embedding Dimension | 128 |
| Hidden Size | 128 |
| Dropout | 0.5 |
| Batch Size | 64 |
| Learning Rate | 0.001 |
| Maximum Epochs | 15 |
| Optimizer | Adam |
| Loss Function | Weighted CrossEntropyLoss |
| Early Stopping Patience | 3 |
| Gradient Clipping | 1.0 |
| Random Seed | 42 |

## Experimental Results

The model achieved the following results using 1,260 labeled records from the original validation dataset.

| Metric | Result |
|---|---:|
| Accuracy | 86.03% |
| Macro F1-Score | 0.8240 |
| Weighted F1-Score | 0.8629 |
| Best Epoch | 4 |
| Best Validation Loss | 0.4370 |

Training was stopped at epoch 7 through early stopping, while the best model weights were obtained at epoch 4.

**Evaluation Note:** These metrics represent evaluation on the original labeled validation file, not the official Kaggle masked test set.

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

Open the notebook using Google Colab or Jupyter Notebook:

`UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb`

### 4. Prepare the Dataset

Ensure that all three TSV files are available inside the `dataset/` directory.

### 5. Run the Notebook

Execute the notebook cells sequentially to perform:

- Dataset inspection
- Text preprocessing
- Tokenization and vocabulary construction
- Sequence encoding and padding
- LSTM model training
- Model evaluation
- Sentiment prediction on unlabeled data

## Dataset Attribution

Dataset source:

**Alvin Kurniawan Hanafie — Dataset for Indonesian Sentiment Analysis**

https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis

Please refer to the original Kaggle dataset page for the complete license terms and attribution requirements.

## Author

**Arif Prima Rahadian**  
Information Systems  
Institut Teknologi PLN  
Class C — 2026

Individual academic project for the Deep Learning course.
