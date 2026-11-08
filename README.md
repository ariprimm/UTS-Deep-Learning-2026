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
| Course | Deep Learning |
| Algorithm | Long Short-Term Memory (LSTM) |
| Framework | PyTorch |
| Task | Multiclass Sentiment Classification |

## Dataset

**Dataset for Indonesian Sentiment Analysis**

- Kaggle Owner: Alvin Kurniawan Hanafie
- Source: [Kaggle Dataset](https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis)
- Language: Indonesian
- Classes: Positive, Negative, Neutral
- License displayed on Kaggle: Apache 2.0

The dataset contains training, validation, and masked-label test files.

The masked-label file contains 500 texts without usable ground-truth sentiment labels and is therefore used for inference only.

## Model Architecture

The implemented architecture consists of:

`Embedding → LSTM → Dropout → Fully Connected → Classification`

Main configuration:

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

## Experimental Results

Evaluation was performed using 1,260 labeled records from the original validation file.

| Metric | Result |
|---|---:|
| Accuracy | 86.03% |
| Macro F1-Score | 0.8240 |
| Weighted F1-Score | 0.8629 |
| Best Epoch | 4 |
| Best Validation Loss | 0.4370 |

The evaluation results represent performance on the labeled validation data, not the official masked Kaggle test set.

## Repository Structure

```text
UTS-Deep-Learning-2026/
├── README.md
├── UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.ipynb
├── dataset/
│   ├── train_preprocess_ori.tsv
│   ├── valid_preprocess.tsv
│   └── test_preprocess_masked_label.tsv
├── report/
│   └── UTS_DEEPL_C_202432107_ARIFPRIMARAHADIAN.pdf
├── requirements.txt
└── .gitignore
```

## How to Run

1. Clone this repository:

```bash
git clone https://github.com/ariprimm/UTS-Deep-Learning-2026.git
```

2. Install the required libraries:

```bash
pip install -r requirements.txt
```

3. Open the notebook using Google Colab or Jupyter Notebook.

4. Ensure all three dataset files are placed inside the `dataset/` directory.

5. Run the notebook cells sequentially.

The notebook includes data inspection, preprocessing, model training, evaluation, and prediction on unlabeled texts.

## Dataset Attribution

Dataset source:

Alvin Kurniawan Hanafie — Dataset for Indonesian Sentiment Analysis.

https://www.kaggle.com/datasets/alvinhanafie/dataset-for-indonesian-sentiment-analysis

Please refer to the original Kaggle dataset page for its license and attribution requirements.

## Author

**Arif Prima Rahadian**  
Institut Teknologi PLN  
Information Systems — Class C

Individual academic project for the Deep Learning course.
