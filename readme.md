![indigo_logo](https://github.com/user-attachments/assets/e16bcaad-aa05-44ee-8596-c4951eeed4a0)

# Quora QA Analysis

This project analyzes and compares NLP models like BERT, T5 and GPT2 on the Quora Question-Answer dataset, using metrics such as ROUGE, BLEU, and F1 scores.

## Table of Contents

- [Introduction](#introduction)
- [Setup](#setup)
- [Usage](#usage)
- [Results](#results)
- [Future Work](#future-work)

## Introduction

This project evaluates different NLP models' performance in answering questions from the Quora dataset. Models compared include BERT, FLAN-T5, and GPT-2, with metrics such as ROUGE, BLEU, and F1 scores used for evaluation.

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/quora-qa-analysis.git
   cd quora-qa-analysis
   ```

2. **Install dependencies:**

  ```bash
  pip install -r requirements.txt
  ```

3. **Load the dataset:**
 
  ```bash
  df = pd.read_json("hf://datasets/toughdata/quora-question-answer-dataset/Quora-QuAD.jsonl")
  ```

4. **Run the project:**

  ```bash
  bash run.sh
  ```

## Usage

1. **Preprocess the data:**

```bash
# Example from preprocess.py
def preprocess_text(text):
    tokens = nltk.word_tokenize(text)
    tokens = [word for word in tokens if word not in stop_words]
    tokens = [stemmer.stem(word) for word in tokens]
    return ' '.join(tokens)

  ```

2. **Generate answers using models:**


```bash
# Example from generate_answers.py
def get_answer(question, context, model_name):
    qa = pipelines[model_name]
    result = qa(question=question, context=context)
    return result['answer']


  ```

3. **Evaluate the models:**


```bash
# Example from evaluate.py
def calculate_metrics(reference, predicted):
    rouge_scores = scorer.score(reference, predicted)
    bleu_score = sentence_bleu([reference_tokens], predicted_tokens)
    # F1 score calculation
    return {
        'rouge1': rouge_scores['rouge1'].fmeasure,
        'rouge2': rouge_scores['rouge2'].fmeasure,
        'rougeL': rouge_scores['rougeL'].fmeasure,
        'bleu': bleu_score,
        'f1': f1
    }

```

4. **Run the main script:**
```bash
python src/main.py

```

## Results
The evaluation results, including average ROUGE-1, ROUGE-2, ROUGE-L, BLEU, and F1 scores, are printed for each model.


## Future Work
1. **Model Improvements:** Suggest improvements to models or preprocessing techniques based on findings.
2. **Enhancements:** Consider adding data sources or using ensemble methods to leverage multiple models' strengths.
3. **Further Analysis:** Investigate advanced metrics and perform error analysis to understand model limitations and strengths.
