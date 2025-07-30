<h1 align="center">
<b>CausalNet: End-to-End Causal Structure Learning and Counterfactual Explanations in Neural Networks</b>
</h1>
<h3 align="center">
<b>By: Anirudh Mazumder</b>
</h3>

## Project Summary
Traditional neural networks, which are trained for healthcare prediction tasks, have high predictive accuracies on datasets. However, they lack interpretability and generalizability, which limits their adoption in real-world clinical systems. Current explainable AI methods provide information about the importance of features, but fail to capture proper causal relationships, offering correlations rather than actionable causal insights. In order to fill this gap, I developed CausalNet. CausalNet is a novel end-to-end neural network architecture that learns predictive models and discovers causal structures through an integrated causal discovery layer. CausalNet incorporates a trainable adjacency matrix within the network, which learns a directed acyclic graph of latent features, enabling a gradient-based optimization of the causal structure alongside the prediction loss. The learned causal graph enables direct interventions for a counterfactual reasoning module, which performs do-operations on latent nodes to generate causally consistent explanations. Unlike post-hoc explanation algorithms, CausalNet provides actionable insights by modeling how changes to one variable propagate through the network to affect the final prediction. CausalNet is tested on healthcare datasets, demonstrating comparable prediction performance while recovering critical causal relationships and generating interpretable counterfactual explanations, addressing a critical gap between accuracy and interpretability.

## Code Usability
Inside each of the directories the datasets should already be loaded as well as the Jupyter Notebooks. The user simply has to install the Python packages that are refered inside of the code, and it can be ran end-to-end.

## Experiments
1. Generalizability Experiment - Cross-Dataset Transfer Learning
Objective: Test whether CausalNet's learned causal relationships improve generalization across different datasets compared to standard neural networks.
Setup: Trained both CausalNet and a standard neural network on one diabetes dataset, then evaluated performance on a second diabetes dataset from a different source. Used matched variables (Age, BMI, Blood Pressure) with standardized preprocessing and balanced class distributions.
Key Results:
- Same distribution performance: Standard network slightly outperformed CausalNet in accuracy (77.11% vs 72.24%)
- Cross-dataset generalization: CausalNet significantly outperformed the standard network
    - AUC: 71.80% vs 70.36% (p < 1.9×10⁻²², Cohen's d = 1.27)
    - Accuracy: 67.12% vs 66.52% (p < 3.9×10⁻¹⁴, Cohen's d = 0.88)
    - Win rate: CausalNet achieved higher AUC 93% of trials, higher accuracy 78% of trials

This demonstrates that CausalNet learns more generalizable causal relationships rather than dataset-specific correlations.

2. Protein Signaling Dataset - Causal Discovery Validation
Objective: Compare CausalNet's causal discovery performance against established ground truth from Sachs et al.'s protein signaling pathway data.
Setup: Used 7,466 samples with 11 protein variables. Applied threshold filtering to identify the strongest causal relationships.
Results:
- Thresholded graph (top 85% edges): 18 edges, SHD = 29, with 3 correctly identified relationships
- Full graph: 55 edges, SHD = 64, with 4 correctly identified relationships
- Shows CausalNet can recover some true causal structures but may infer spurious relationships without domain constraints

3. Cancer Dataset - Counterfactual Analysis
Objective: Demonstrate CausalNet's ability to generate actionable counterfactual explanations for individual predictions.
Setup: Trained on cancer prediction dataset with 8 features (age, gender, BMI, smoking, genetic risk, physical activity, alcohol intake, cancer history).
Performance: 84.67% accuracy, 92.27% AUC
Counterfactual Analysis Results: Successfully generated interpretable "what-if" scenarios showing how changing individual risk factors affects cancer prediction. Most relationships aligned with medical knowledge (e.g., increased smoking → higher cancer risk, increased physical activity → lower cancer risk), though some anomalies were observed (BMI relationship), indicating areas for model improvement.
Impact: Unlike traditional explainable AI that only shows feature importance, CausalNet provides actionable insights showing how interventions on specific variables propagate through the causal network to affect final predictions.

## Datasets
### Cancer Prediction Dataset
Cancer Prediction Dataset: https://www.kaggle.com/datasets/rabieelkharoua/cancer-prediction-dataset

### Generalizability Experiment Datasets (Diabetes Prediction)
Diabetes Dataset 1: https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset
Diabetes Dataset 2: https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database

### Protein Signaling Experiment
Protein Signaling Dataset: https://www.science.org/doi/10.1126/science.1105809