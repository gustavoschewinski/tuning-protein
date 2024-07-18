# README

## Objective of the Project

The goal of this project is to predict LiP-MS (limited proteolysis coupled to mass spectrometry) signals which indicate protein structural changes under osmotic stress, using advanced machine learning techniques including protein language models (PLMs).

## Organization
### 0. training_data_analysis
This section shows the distribution of the training data compared to the unused data. The effects of the data being chosen based on their q-values can be observed. 

### 1. data_preparation

This script prepares the data by reading protein sequences from a FASTA file and associated peptide data from related studies. It creates a binary vector indicating the positions of peptides within their respective proteins, crucial for understanding the context of each peptide sequence within the whole protein structure.

### 2. create_embeddings

Utilizes the ESM-2 model to generate embeddings for protein sequences. These embeddings transform protein sequences into a high-dimensional space, facilitating the extraction of meaningful biological information from the sequence data.

### 3. dl_model_data_prep

Prepares the dataset for deep learning model training. This includes reading embeddings, trimming them to fit model requirements, and merging them with the binary position data created in step 1, ensuring that each data point is represented accurately for the upcoming training phase.

### 4. dl_model_run

Builds and trains a deep learning model on the processed data. This model is designed to integrate the embeddings with the peptide position data to predict the LiP-MS scores, reflecting the structural changes in proteins under different conditions.

## Mutation Analysis

### 2. create_embeddings_validation.ipynb

Generates embeddings for mutated protein sequences to validate the model's ability to predict changes in protein structure and function due to mutations.

### 5. mutations

Uses the trained model from step 4 to predict LiP-MS scores for each mutated protein. This step is crucial for understanding the impact of specific mutations on protein structure, with visualizations provided for clear interpretation of the model's predictions.

## Environment Setup

To set up the required environment to run this project, use the following command:

```bash
conda env create -f environment.yml
```

## Theoretical Background and Implementation

This section outlines the methodologies and the data handling processes used in the project. The model focuses on peptides under 1000 amino acids to manage computational resources efficiently. The project uses a variety of data, including differential peptide abundance under osmotic stress conditions, sourced from prior studies.

Protein language model ESM-2, developed by Meta, is utilized for generating embeddings. This model is particularly adept at predicting protein structures and functions from sequence data, thanks to its deep learning architecture based on transformers.

The architecture of the deep learning model, referred to as _PeptideRegressor_, integrates embeddings with peptide positions to predict the LiP-MS scores. This includes a series of transformations and layers designed to process the embedding data efficiently and accurately.

## Results

The model's effectiveness is evaluated through various metrics, including the Spearman correlation coefficient, mean squared error, visual comparisons of predicted versus actual values, and mutations of peptides.
