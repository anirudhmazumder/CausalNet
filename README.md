<h1 align="center">
<b>CausalNet</b>
</h1>
<h3 align="center">
<b>By: Anirudh Mazumder</b>
</h3>

## Project Summary
Traditional neural networks, which are trained for healthcare prediction tasks, have high predictive accuracies on datasets. However, they lack interpretability and generalizability, which limits their adoption in real-world clinical systems. Current explainable AI methods provide information about the importance of features, but fail to capture proper causal relationships, offering correlations rather than actionable causal insights. In order to fill this gap, I developed CausalNet. CausalNet is a novel end-to-end neural network architecture that learns predictive models and discovers causal structures through an integrated causal discovery layer. CausalNet incorporates a trainable adjacency matrix within the network, which learns a directed acyclic graph of latent features, enabling a gradient-based optimization of the causal structure alongside the prediction loss. The learned causal graph enables direct interventions for a counterfactual reasoning module, which performs do-operations on latent nodes to generate causally consistent explanations. Unlike post-hoc explanation algorithms, CausalNet provides actionable insights by modeling how changes to one variable propagate through the network to affect the final prediction. CausalNet is tested on healthcare datasets, demonstrating comparable prediction performance while recovering critical causal relationships and generating interpretable counterfactual explanations, addressing a critical gap between accuracy and interpretability.

## Datasets
### Cancer Prediction Dataset
Cancer Prediction Dataset: https://www.kaggle.com/datasets/rabieelkharoua/cancer-prediction-dataset

### Generalizability Experiment Datasets (Diabetes Prediction)
Diabetes Dataset 1: https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset
Diabetes Dataset 2: https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database

### Protein Signaling Experiment
Protein Signaling Dataset: https://www.science.org/doi/10.1126/science.1105809