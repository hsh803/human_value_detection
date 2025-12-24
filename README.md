# Human value detection
- A shared task, Human value detection 2024, Touché (https://touche.webis.de/shared-tasks.html#human-value-detection)
- Conducted experiments of Sub-task 1 from this shared task in a group (four memeber) as a project work in information retrieval course
- Sub-task 1: Given a text, for each sentence, detect which human values the sentence refers to.

## Task
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

## Initial experiments
- To find a proper pre-trained model for our project, we trained three BERT-based LLMs with the 11K training dataset as a initial experiment.
- Base codes given by the organization for training and evaluation were adjusted and implemented for our own experiments.
- We chose Roberta for further training due to its best performance
- Base code source: https://github.com/touche-webis-de/touche-code/tree/main/clef24/human-value-detection/approaches/bert-baseline

<img width="350" height="150" alt="image" src="https://github.com/user-attachments/assets/6c9b8a95-328a-4d66-8143-985155a2c0c9" />

## Further experiments
- Training Roberta base model on 11K, 22K, 33K and 44K (all)

## Evaluation 
- Performance for detection: Precision, Recall, F1
- Performance for each label: ROC (Receiver Operating Characteristic), AUC (Area Under the Curve)

## Results
- F1 and Recall scores of the evaluation get higher when the data size gets bigger while precision goes down when new data is added at the point from 22K to
33K and to all.
- To evaluate the model’s performance for each label, we used ROC and AUC curves because the evaluation code given by the organizer for this shared task used them.

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/791e5951-112b-467c-bbce-6834cffbd4a4" />
<img width="800" height="550" alt="image" src="https://github.com/user-attachments/assets/467e9db6-41d5-4f41-a424-d7638b52bbad" />

