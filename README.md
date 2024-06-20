# README

## Pokémon GAN Training and Augmentation

This project involves training a Generative Adversarial Network (GAN) to generate Pokémon images using text embeddings derived from Pokémon names. The workflow includes data preparation, BERT-based text embedding generation, and GAN training. Below is a detailed explanation of the process.

### Table of Contents
1. [Dataset Class](#dataset-class)
2. [Data Augmentation](#data-augmentation)
3. [BERT Embeddings](#bert-embeddings)
4. [GAN Training](#gan-training)
5. [Results Visualization](#results-visualization)

### Dataset Class

A custom dataset class is implemented to handle:

- Loading and transforming images.
- Generating text embeddings for Pokémon names using the BERT model.
- Providing the necessary data format for the DataLoader, which is used in the training process.
- link to the dataset - https://www.kaggle.com/datasets/thedevastator/pokemon-llava-images-and-text-descriptions

### BERT Embeddings

Text embeddings for Pokémon names are generated using a pre-trained BERT model. The text is tokenized and then passed through the BERT model to obtain a high-dimensional embedding, which captures the semantic meaning of the Pokémon names.

### GAN Training

The training process involves a GAN setup with two stages:

#### Stage 1

1. *Stage 1 Generator:* This network takes text embeddings and random noise as inputs and generates low-resolution images (64x64 pixels).
2. *Stage 1 Discriminator:* This network evaluates the authenticity of the generated images by comparing them to real images, conditioned on the text embeddings.

Both the generator and discriminator are trained iteratively. The generator aims to produce images that can fool the discriminator, while the discriminator aims to correctly distinguish between real and fake images.

#### Stage 2

1. *Stage 2 Generator:* This network refines the images produced by the Stage 1 generator, improving their resolution and quality.
2. *Stage 2 Discriminator:* This network evaluates the authenticity of the higher-resolution images produced in Stage 2.

Similar to Stage 1, the generator and discriminator are trained iteratively, but now with the refined images.

### Results Visualization

After training, the generated images are visualized to assess the performance of the GAN. These images are expected to look similar to real Pokémon images, capturing various details and features.
