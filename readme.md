# Quora Q&A System

This project analyzes and compares NLP models like BERT, T5 and GPT2 on the Quora Question-Answer dataset, using metrics such as ROUGE, BLEU, and F1 scores.
1. The repository includes two Jupyter Notebook files: **QnA_task_final (1).ipynb**, which covers routine preprocessing tasks such as tokenization, stemming, and lemmatization.
2. Another one, **novel_improvements.ipynb**, which explores alternative preprocessing techniques learned from various sources.
3. The results from both approaches show minimal variance.

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

![results](https://github.com/user-attachments/assets/7e200e4b-2d29-4727-9c78-d9459601aa6b)

![c5f0eb59-a61d-4eae-90fd-877c20359d16](https://github.com/user-attachments/assets/4c8063e6-30f2-479e-845b-a52357a6fba9)


## Future Work
1. **Model Enhancements:** Explore improvements to model architectures or fine-tuning methods.
2. **Additional Data:** Integrate more diverse datasets to enhance model robustness.
3. **Ensemble Methods:** Combine multiple models to leverage their strengths.
4. **Advanced Metrics:** Investigate additional evaluation metrics for comprehensive analysis.
5. **Error Analysis:** Conduct in-depth error analysis to identify and address model limitations.
