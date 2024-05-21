# Enhancing Mathematical Reasoning in LLMs: Fine-Tuning for Math Word Problem

[**Research Paper**](https://drive.google.com/file/d/1k0v51RtDxmZboesr6D3V342qeq2ymymW/view?usp=sharing)
[**Slide Deck**](https://drive.google.com/file/d/1tCkOXH20rnPX5XnESAzb3vpvXuapaxkk/view?usp=sharing)

## Table of Contents
1. [Introduction](#introduction)
3. [Usage](#usage)
8. [Results](#results)
10. [Conclusion](#conclusion)
12. [Acknowledgments](#acknowledgments)

## Introduction

This project focuses on improving the RoBERTa model's mathematical reasoning by fine-tuning on the MathQA dataset. The aim is to enhance the ability of LLMs' understanding and reasoning for mathematical questions by leveraging domain-specific fine-tuning techniques.

## Usage
The fine-tuned RoBERTa-MQA models are installable through Huggingface's library under _nickrwu/_ name space.

### Fine-tuned Models:
1. [RoBERTa-MQA-FORMRAT](https://huggingface.co/nickrwu/roberta-mqa-formrat)
2. [RoBERTa-MQA-RAT](https://huggingface.co/nickrwu/roberta-mqa-rat)
3. [RoBERTa-MQA](https://huggingface.co/nickrwu/roberta-mqa)


```
from transformers import *

# MQA + Rationale + Annotated Formula
tokenizer = AutoTokenizer.from_pretrained('nickrwu/roberta-mqa-formrat')
model = AutoModel.from_pretrained('nickrwu/roberta-mqa-formrat')

# MQA + Rationale
tokenizer = AutoTokenizer.from_pretrained('nickrwu/roberta-mqa-rat')
model = AutoModel.from_pretrained('nickrwu/roberta-mqa-rat')

# MQA
tokenizer = AutoTokenizer.from_pretrained('nickrwu/roberta-mqa')
model = AutoModel.from_pretrained('nickrwu/roberta-mqa')
```

### Running the Project

1. Load the [MathQA dataset](https://math-qa.github.io/) and preprocess the dataset.
2. Train the base and fine-tuned models using the provided Jupyter notebook or scripts.
3. Evaluate the models and compare their performance.

## Results
| Model               | F1-Score    | Precision   | Recall      | Accuracy    |
| ------------------- | ----------- | ----------- | ----------- | ----------- |
| RoBERTA-base        | 0.163       | 0.199       | 0.202       | 0.181       |
| RoBERTA-race        | 0.310       | 0.327       | 0.311       | 0.320       |
| RoBERTA-mqa         | 0.376       | 0.380       | 0.375       | 0.379       |
| RoBERTA-mqa-rat     | 0.538       | 0.541       | 0.536       | 0.539       |
| RoBERTA-mqa-formrat | 0.558       | 0.559       | 0.557       | 0.560       |
|                                                                             |
| Random Chance       | 0.333       | 0.200       | 1.000       | 0.200       |
| Human Base (n=25)   | 0.747       | 0.596       | 1.000       | 0.596       |

The fine-tuning process yielded substantial improvements in model performance metrics. The RoBERTa base model exhibited significant gains, starting with baseline metrics of 0.163 for F1-score. Further fine-tuning this model on the MathQA dataset elevated the F1-score and accuracy to 0.558. This represents a remarkable 250% increase in the F1-score from the base RoBERTa model, highlighting the effectiveness of our targeted modifications.

## Conclusion
The significant improvements observed in the machine learning model’s performance metrics following our interventions can be attributed to a deliberate strategy aimed at overcoming its initial shortcomings in dealing with the MathQA dataset’s inherent complexity. Enhancements in data preprocessing—aimed at better capturing the intricacies of mathematical statements and options—and a more tailored training regimen, focusing on targeted parameter tuning and efficient resource utilization, have collectively elevated the model's understanding and problem-solving capabilities. These strategic adjustments have led to better performance metrics, reinforcing the efficacy of our approach.

## Acknowledgments
**Contributors:** Thanks to the project team members who contributed to data preparation, model training, and evaluation.

**Resources:** 
* High Performance Computing resources provided by New York University
* Open-source tools from Hugging Face and Weights & Biases
