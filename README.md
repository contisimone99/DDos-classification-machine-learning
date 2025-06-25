# AI for DDoS Detection

## Project Description

This project focuses on applying machine learning techniques for the detection of DDoS (Distributed Denial of Service) attacks in cloud-based environments. The primary objective is to identify a classification model capable of reliably distinguishing between benign and malicious traffic, with a specific focus on minimizing **false negatives**, i.e., cases where an attack goes undetected.

## Dataset

The dataset used is **BCCC-cPacket-Cloud-DDoS-2024**, available on [Kaggle](https://www.kaggle.com/datasets/bcccdatasets/bccc-cpacket-cloud-ddos-2024). It contains over 300 features (both numerical and categorical) and has a size of approximately 1.21 GB.

### Preprocessing

Main preprocessing steps included:

* **Removal of non-informative features**: `flow_id`, `protocol`, IP addresses, and port numbers were removed to avoid overfitting and ensure generalization.
* **Handling NaN and Infinite values**: Columns with mostly infinite values were dropped. Remaining NaNs were removed as the dataset is large enough to tolerate this.
* **Data type correction**: Ensured consistent numerical formatting (e.g., converting `'5'` to `5`).
* **Incorrect label handling**: A class labeled “label” with only 2 instances was removed entirely.
* **Feature selection**: Applied a feature importance threshold (> 0.01), resulting in 28 relevant features.
* **Dataset split**: The data was divided into an 80/20 train-test split.

## Exploratory Analysis

* The dataset is slightly imbalanced, but manageable without resampling.
* Some outliers were detected but retained, as they belonged to the benign class and could provide useful signals.
* Correlation analysis was conducted to identify redundant features.

## Models Tested

Several models were evaluated using cross-validation, including:

* **Random Forest**
* **Decision Tree**
* **Logist regression**
* **Gaussian Naive Bayes**

### Evaluation Metrics

* **Recall** and **F1-score** were prioritized, as minimizing false negatives is crucial in this domain.
* Results showed **Random Forest** as the best-performing model, followed by **Decision Tree**.

## Conclusions

* **Random Forest** achieved the highest performance in terms of precision-recall balance.
* Learning curves confirmed that the model does not suffer from overfitting.
* Tree-based models proved most suitable for this classification task.

## Future Work

* Apply dataset balancing techniques (e.g., oversampling, undersampling) to improve classification of minority attack classes.
* Experiment with non-tree-based models such as neural networks or support vector machines.

## License

This project is licensed under the **MIT License**. See the [`LICENSE`](LICENSE) file for more details.

## Author

Simone Conti
