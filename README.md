# GammaHadronPreditionModel
MAGIC Gamma Telescope Data Classification
Introduction
This notebook demonstrates the process of classifying high-energy gamma particles from hadronic cosmic rays. The goal is to distinguish between gamma-ray events (signal) and hadron-induced events (background) recorded by the Major Atmospheric Gamma-ray Imaging Cherenkov (MAGIC) telescope.

Data Source
The dataset used is magic04.data, which contains 10 attributes describing the atmospheric Cherenkov images recorded by the MAGIC telescope. The last column indicates the class: 'g' for gamma and 'h' for hadron. More details on the dataset can be found in the provided citation: D. Heck et al., CORSIKA, A Monte Carlo code to simulate extensive air showers, Forschungszentrum Karlsruhe FZKA 6019 (1998).

Steps Performed
Data Loading and Initial Exploration: The dataset was loaded into a pandas DataFrame, and column names were assigned for better readability.
Target Variable Encoding: The 'class' column was converted from categorical ('g', 'h') to numerical (1 for gamma, 0 for hadron).
Feature Distribution Visualization: Histograms were generated for each feature to visualize the distribution of gamma and hadron events, helping to understand feature separation.
Data Splitting: The dataset was split into training (60%), validation (20%), and testing (20%) sets to prepare for model development and evaluation.
Data Scaling and Oversampling: A custom function scale_dataset was defined and applied:
Features (X) were standardized using StandardScaler to ensure all features contribute equally to the model.
The training set was oversampled using RandomOverSampler to address potential class imbalance, preventing the model from being biased towards the majority class.
Model Training: A K-Nearest Neighbors (KNN) classifier (KNeighborsClassifier) was initialized with n_neighbors=5 and trained on the scaled and oversampled training data.
Model Evaluation: The trained KNN model was used to make predictions on the test set, and its performance was evaluated using a classification_report, providing metrics like precision, recall, and f1-score for each class.
