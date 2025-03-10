# Overview
This project focuses on classifying ICD-9 codes from discharge summaries, which are unstructured medical texts describing a patient’s condition, diagnosis, treatment, and discharge instructions. The task is to predict one or more ICD-9 codes based on these clinical discharge summaries, using machine learning techniques such as Logistic Regression, LSTM (Long Short-Term Memory), Artificial Neural Networks (ANN), and Classifier Chains.


# Problem Statement
Given a discharge summary, the goal is to classify it into one or more ICD-9 codes, which represent diagnoses, treatments, or procedures related to the patient’s care. ICD-9 codes are essential for medical billing, insurance claims, and organizing patient records.

The task involves processing unstructured discharge summary text and applying multi-label classification models to predict the corresponding ICD-9 codes.


# Dataset
The dataset for this project consists of discharge summaries from patients, with each summary associated with one or more ICD-9 codes. The dataset typically includes:

* Discharge Summaries: Textual records that describe the patient's condition, diagnoses, procedures, and instructions upon discharge.
* ICD-9 Codes: A set of one or more ICD-9 codes corresponding to the conditions or procedures described in the discharge summary.

# Approach

## 1. Text Preprocessing
The unstructured clinical text undergoes several preprocessing steps:

* Tokenization: Splitting the text into words or phrases.
* Stopword Removal: Filtering out common words that do not carry significant meaning.
* Lowercasing: Converting all words to lowercase.
* Vectorization: Converting text data into numerical representations using techniques like TF-IDF and BioWord2Vec.

## 2. Modeling Techniques

### 2.1 LSTM (Long Short-Term Memory)
LSTM, a type of Recurrent Neural Network (RNN), is used to capture long-range dependencies in text data. LSTM is suitable for text classification tasks where contextual information from the sequence is important.
This model will be used to predict multiple medical categories based on the clinical notes.
### 2.2 Logistic Regression
Logistic Regression is a simple yet powerful model used for binary classification. In this project, it will be used for multi-label classification tasks, following the Binary Relevance method, where it predicts the presence or absence of each label for a given clinical note.

### 2.3 Classifier Chains with Logistic Regression as Base
Classifier Chains is an ensemble approach where multiple binary classifiers are trained sequentially, with the predictions of previous classifiers being fed into the next. In this project, Logistic Regression is used as the base classifier for each chain.
This approach works well for multi-label classification tasks, where labels are dependent on each other.

### 2.4 Artificial Neural Networks (ANN)
Artificial Neural Networks (ANN) are used to model complex relationships between the input features and target labels. In this project, a feed-forward neural network will be used as the base classifier for the Classifier Chains approach.
The advantage of using ANN is its ability to capture complex patterns in the data, which may improve performance for multi-label classification.

### 2.5 Classifier Chains with Specific Label Order
The order of labels in Classifier Chains is determined heuristically based on accuracy. Different permutations of label orders are evaluated, and the order that maximizes overall classification accuracy is selected.


## 3. Evaluation
The performance of the models is evaluated using the following metrics:

* Multi-label accuracy: Calculates the proportion of correctly predicted labels by measuring the intersection over the union of true and predicted labels for each sample, averaged across all samples.
* Macro Jaccard Score and F1-Score: These metrics are evaluated for each label and aggregated for overall model performance.
* Hamming Loss: Measures the fraction of labels incorrectly predicted.
