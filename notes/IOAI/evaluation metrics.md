Model evaluation metrics to measure model performance is a broad subject that includes an immense number of performance metrics. A new metric can come to life in a recently published paper or can be discovered in practice as ML is applied to a new task in the real world.

Data scientists use a large set of common metrics when they build and evaluate models. Model performance evaluation is about measuring model predictions (inferences) relative to how the model performs against ground truth. In the model building process, experiment tracking solutions are normally used to track performance metrics over multiple training and test runs. As models are deployed in the real world, ML monitoring and observability platforms are normally used to track performance over time.

## Model evaluation metrics by task

ML performance metrics are typically ML task-specific. Keep in mind this is not a comprehensive list.

### Tabular

**Regression**
- MAE (Mean Absolute Error)
- MAPE (Mean Absolute Percentage Error)
- RMSE (Root Mean Square Error)
- MSE (Mean Square Error)

**Classification**
- AUC (Area Under Curve)
- Log Loss
- Accuracy
- Precision
- Recall
- F1 Score

**Ranking**
- NDCG (Normalized Discounted Cumulative Gain)
- DCG (Discounted Cumulative Gain)
- IDCG (Ideal Discounted Cumulative Gain)
- NDCG@K (Normalized Discounted Cumulative Gain)
- MAP (Mean Average Precision)
- Recall@

### Image

**Classification**
- Precision
- Recall
- Accuracy
- F1 Score

**Object detection (bounding box)**
- Average IOU (Intersection Over Union)
- MAP (Mean Average Precision)
- AP (Average Precision)

**Segmentation**
- Average IOU (Intersection Over Union)
- AP (Average Precision)
- MAP (Mean Average Precision)

**Depth Estimation**
- Abs-Rel (Absolute relative difference)
- SQ-Rel (Square relative difference)
- ARD (Absolute Relative Distance)
- RMSE (Root Mean Square Error)

**Video Classification**
- Accuracy
- Precision
- F1 Score
- Recall
- MAP (Mean Average Precision)
- IOU (Intersection Over Union)

**Zero Shot Image Classification**
- Top K accuracy
- Seen class accuracy
- Novel class accuracy

### Language models

**Conversational**
- BLEU Score (BiLingual Evaluation Understudy)

**Fill Mask**
- Perplexity

**Question Answering**
- F1 Score
- Exact Matrch

**Sentence Similarity**
- Euclidean distance (embedding)
- Cosine distance (embedding)
- Reciprocal rank
- NDCG (Normalized Discounted Cumulative Gain)

**Summarization**
- ROUGE Score

**Text Classification**
- Accuracy
- Precision
- Recall
- F1 Score

**Token Classification (NER, POS)**
- Accuracy
- Precision
- Recall
- F1 Score

**Translation**
- BLEU Score

**Text Generation**
- Perplexity
- KL Divergence
- Cross entropy
- PSI (Population Stability Index)

## Model performance management

The idea of model performance management encompasses managing model performance across the full lifecycle from testing through production. The textbook use of performance metrics normally lacks ideas around daily variability of performance, how to handle delays in ground truth, how much and how often to aggregate samples for performance analysis, how to create baselines and how to trace down changes in model performance.

The production environment in many cases can be quite different from the model building environment. These differences can come about in how ground truth is collected and analyzed.