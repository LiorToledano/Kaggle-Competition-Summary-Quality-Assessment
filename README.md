# Kaggle Competition Project - Summary Quality Assessment 
Top 5% - Silver Medal

![Competition Badge](https://img.shields.io/badge/Kaggle-91st%20Place-brightgreen)

This README file provides an overview of a Kaggle competition project in which I participated and achieved 91st place out of 2060 competitors. The project's objective was to develop a model that assesses the quality of summaries written by students in grades 3-12. The model evaluates the main idea and details representation, as well as the clarity, precision, and fluency of the language used in the summary. The project aimed to assist teachers in evaluating student work and provide immediate feedback to students.

## Competition Description

### Goal of the Competition
The primary goal of this Kaggle competition was to create a model capable of assessing the quality of student-written summaries. This involved evaluating how well a student's summary captured the main ideas and details of a source text and the quality of language used in the summary. The project's results would help teachers and learning platforms in providing valuable feedback to students.

### Context
Summary writing is a crucial skill for students of all ages. It enhances reading comprehension, critical thinking, and writing abilities. However, assessing and providing feedback on summaries can be time-intensive for teachers. Innovative technology, such as large language models (LLMs), can play a pivotal role in automating this process. This competition aimed to harness the power of machine learning to streamline summary evaluation.

The competition was hosted by CommonLit, a nonprofit educational technology organization dedicated to improving the reading, writing, communication, and problem-solving skills of students, especially those in Title I schools. CommonLit collaborated with The Learning Agency Lab, Vanderbilt University, and Georgia State University to promote this mission.

## Solution Overview

My solution for this competition was based on a combination of feature engineering and an ensemble of multiple models, including five DeBERTa large models and one DeBERTa-based model. The process involved extracting various features from the text data and using these features as inputs to a LightGBM (LGBM) model.

Key components of my solution included:

- **Preprocessing**: A custom preprocessor class was developed to perform text processing and feature extraction. This included text length analysis, word overlap counts, n-gram analysis, Named Entity Recognition (NER) overlap, and more.

- **Feature Engineering**: Features such as text length ratios, word overlap counts, bigram and trigram overlap counts, and quote counts were engineered to capture the characteristics of the summaries.

- **Spelling Correction**: A spelling correction function was implemented to identify and correct spelling errors in the text data.

- **NER Overlap**: Named Entity Recognition (NER) overlap was utilized to assess the intersection of NER entities between the source text and the student's summary.

- **Model Ensemble**: An ensemble of multiple DeBERTa models was used in combination with the engineered features to predict the quality of summaries.

- **Performance**: The model achieved 91st place out of 2060 competitors, demonstrating its effectiveness in assessing summary quality.

## Code Structure

The code for this project is organized into several key components, including data preprocessing, feature engineering, model training, and evaluation. The code leverages Python and various libraries, including Hugging Face Transformers (for DeBERTa models), SpaCy, and more.

## Usage

To replicate this project, follow these steps:

1. Clone the repository.

2. Install the required dependencies by running `pip install -r requirements.txt`.

3. Run the data preprocessing and feature engineering steps to prepare the data for model training.

4. Train the ensemble of DeBERTa models using the processed data.

5. Evaluate the model's performance using appropriate evaluation metrics.

Feel free to customize the README as needed, providing more specific details about your implementation, such as model hyperparameters, additional dependencies, and any additional sections that may be relevant to your project.
## Model Results

Here are the results of different experiments with the model:


| Experiment        | Max length | Content RMSE  | Content RMSE  | Content RMSE  | Content RMSE  | Wording RMSE  | Wording RMSE  | Wording RMSE  | Wording RMSE  | MCRMSE      |
| ------------------ | -------- | -------------- | -------------- | -------------- | -------------- | -------------- | -------------- | -------------- | -------------- | ----------- |
|                   |          | Fold 0         | Fold 1         | Fold 2         | Fold 3         | Fold 0         | Fold 1         | Fold 2         | Fold 3         |             |
| **DeBERTa V3 Large with LGBM**| 600        | 0.3769         | 0.4269         | 0.4007         | 0.4447         | 0.4898         | 0.5944         | 0.4695         | 0.5679         | 0.4714      |
| **DeBERTa V3 Large with LGBM**| 1024        | 0.3744         | 0.4251         | 0.3891         | 0.4366         | 0.4923         | 0.6030         | 0.4716         | 0.5677         | 0.4699      |
| **DeBERTa V3 Large with LGBM**          | 786        | 0.3843         | 0.4219         | 0.3918         | 0.4373         | 0.4886         | 0.6262         | 0.4699         | 0.5610         | 0.4726      |
| **DeBERTa V3 Large with LGBM**          | 1500        | 0.3767         | 0.4386         | 0.4029         | 0.4491         | 0.5017         | 0.6007         | 0.4850         | 0.5511         | 0.4757      |
| **DeBERTa V3 Base with LGBM**| 1250    | 0.3756         | 0.4226         | 0.3936         | 0.4415         | 0.4949         | 0.6109         | 0.4789         | 0.5927         | 0.4763      |
| **Ensemble (Optuna)**| -    | -              | -              | -              | -              | -              | -              | -              | -              | 0.459       |


### What Worked Well

- **Feature Engineering:** I successfully applied advanced feature engineering techniques, including welding small numbers of steps, extracting pitch-related features, and verifying their correlation with the target values. These features played a crucial role in enhancing the predictive power of my models, contributing to their overall success.

- **Model Selection:** The selection of the Light Gradient Boosting Machine (LGBM) as the second step in my modeling process proved to be a wise choice. LGBM consistently demonstrated strong performance and versatility, making it a reliable choice for my specific task. I'll delve into why this model was chosen and how it excelled in addressing the problem at hand.

- **Optimization with Optuna:** The introduction of Optuna into my workflow had a transformative impact on model optimization. By leveraging Optuna, I was able to fine-tune my LGBM model and the final ensemble, resulting in substantial performance improvements. I achieved enhanced model accuracy and robustness, thanks to the optimization process enabled by Optuna.

### What Didn't Work

- **Data Augmentation:** Despite my efforts to implement data augmentation, specifically through back translation, I encountered challenges that hindered the desired outcomes. I'll discuss the difficulties and limitations I faced in effectively applying this technique, shedding light on the reasons behind its limited success.

- **Alternative Models:** While exploring various models for the second stage of my process, including alternatives like CatBoost, I found that these models didn't deliver the expected results. I'll detail the factors and considerations that led to my decision to focus on LGBM as the primary model and the limitations I observed with other model choices.


## Acknowledgments

I would like to acknowledge the Kaggle community, CommonLit, and the competition hosts for providing this valuable opportunity to work on a real-world NLP problem. This project would not have been possible without their support.

## References
- [Training Notebook](https://www.kaggle.com/code/mohammad2012191/debertav3-pytorch-baseline-training-cv-0-467)
- [Inference Notebook](https://www.kaggle.com/code/mohammad2012191/debertav3-pytorch-baseline-inference-cv-0-467/notebook)

## Contact Information

For any questions or inquiries regarding this project, please contact me at liortoledano1@gmail.com.

---
