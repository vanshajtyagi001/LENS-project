Language Experience Neuroimaging System (LENS) using Explainable AI, Contrastive Learning & GNN
LENS is an automatic AI system that helps classify people into three groups: Early Bilingual (EB), Late Bilingual (LB), and Monolingual Control (MC).
It uses high-dimensional resting-state functional MRI (fMRI) data along with personal information like age, gender, and background. This helps find biological signs of brain flexibility that are often missed when people just report their own language experiences.

Key Achievements
Performance: The system achieved an average classification accuracy of 77.22%, using a 10-Fold Stratified Cross-Validation method.
This is better than the 66.67% accuracy of traditional methods.

Robust Learning: The system uses a special two-step training method first to learn from data using something called Triplet Loss, then it fine-tunes the model.This helps it better understand brain patterns even when there are only 92 subjects in the dataset.

Explainability: The system has a custom Explainable AI (XAI) tool that shows which brain connections and personal factors are most important in classification.


Technical Architecture
The system uses a Late-Fusion Architecture that processes brain and personal data in separate parts that work together:
Graph Neural Network (GNN) Branch:
- Node Definition: 39 specific brain regions identified by the MSDL Atlas.

- Edge Definition: 39×39 Functional Connectivity Matrices, calculated using Pearson Correlation.

- Core: A Custom GraphConvLayer that follows a specific rule for passing information between nodes.


Demographic MLP Branch:
- Processes 8 features, such as age, gender, ethnicity, and language skill scores.


Fusion Layer:
- Combines a 32-dimensional brain pattern with an 8-dimensional personal profile for final classification.


Project Structure
minor_project.ipynb: This is the main notebook where the model is developed, trained, and tested.
final_best_model_77_percent.pt: This is the saved version of the best model.
fmri_preprocessed_timeseries.npy: This file contains the processed fMRI time data.
participants_clean.tsv: This file has clean participant data and labels for classification.

Implementation & Methodology
Dataset: The data comes from ds001747 on OpenNeuro, which includes 92 people with brain scans like fMRI and structural MRI.


Preprocessing: The data goes through steps like removing skull images, normalizing values to 0–1 scale, removing trends, and filtering for specific brain rhythms.


Optimization: The model was trained on an NVIDIA A100 GPU using PyTorch and the PyTorch Geometric library.


Frontend: An interactive Streamlit dashboard lets users run predictions and view 3D brain patterns called "neural fingerprints."


Scientific Significance:
LENS is a helpful tool for scientists to test ideas about brain adaptability.
It shows that learning a second language early in life changes the brain more than learning it later. This gives real biological clues for future research.
