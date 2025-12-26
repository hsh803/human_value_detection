# Human value detection
- A shared task, Human value detection 2024, Touché (https://touche.webis.de/shared-tasks.html#human-value-detection)
- Conducted experiments of Sub-task 1 from this shared task in a group (four memeber) as a project work in information retrieval course
- Sub-task 1: Given a text, for each sentence, detect which human values the sentence refers to.

## Introduction
- Project goal: Train LLMs that works well on the multi-label task and test to answer to our experimental question 
- Experiment question: Is there a pattern of how the model’s effectiveness changes according to the size of the training data? How and why?

## Data
- 44 758 sentences and 19*2 (values * attained/constrained) human value labels in English
- Total sentences are divided into 11K, 22K, 33K, 44K (all)
- Toy example: https://github.com/touche-webis-de/touche-code/tree/main/clef24/human-value-detection/toy-dataset

## Models
- Bert base: https://huggingface.co/google-bert/bert-base-uncased
- Deberta: https://huggingface.co/microsoft/deberta-v3-base
- Roberta: https://huggingface.co/FacebookAI/roberta-base

## Evaluation 
- Performance for detection: Precision, Recall, F1
- Performance for each label: ROC (Receiver Operating Characteristic), AUC (Area Under the Curve)
- ROC: TPR (True positive rate), FPR (False positive rate) for each class
- AUC: Measures the entire two-dimensional area underneath the entire ROC curve

## Initial experiments
- Check data balance in the four divided datasets: all divisions and validations data have similar distribution in the lables as 11K.
- To find a proper pre-trained model for our project, we trained three BERT-based LLMs with the 11K training dataset as a initial experiment.
- Base codes given by the organization for training and evaluation were adjusted and implemented for our own experiments. (source: https://github.com/touche-webis-de/touche-code/tree/main/clef24/human-value-detection/approaches/bert-baseline)
- We chose Roberta for further training due to its best performance

<img width="300" height="210" alt="image" src="https://github.com/user-attachments/assets/248d737f-606b-4521-9c4e-689ecab4ac76" />
<img width="350" height="150" alt="image" src="https://github.com/user-attachments/assets/6c9b8a95-328a-4d66-8143-985155a2c0c9" />

## Further experiments
- Training Roberta base model on 11K, 22K, 33K and 44K (all)

## Results
- F1 and Recall scores of the evaluation get higher when the data size gets bigger while precision goes down when new data is added at the point from 22K to
33K and to all.
- AUC gets higher when the ratio increases but the labels that have relatively small data ratio, react more sensitively to the changes of the ratio.
- Average of AUC across all labels goes up when more data is added but also the imbalance of the dataset overall.

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/791e5951-112b-467c-bbce-6834cffbd4a4" />
<img width="800" height="550" alt="image" src="https://github.com/user-attachments/assets/467e9db6-41d5-4f41-a424-d7638b52bbad" />

## Highlights in conclusions
- RoBERTa works best on this multi-label sentiment analysis task.
- The model’s performance doesn’t always improve as the dataset’s size increases and the imbalance of the dataset can affect the model’s performance.
- Imbalance of training dataset may have an impact on the model’s performance.
- To improve the model’s performance, we can consider adjusting the distribution of labels over each dataset to reduce imbalance in them.


