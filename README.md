# AI-Generated Text Detection

## Project Description
This project aims to detect AI-generated text by leveraging sentence embeddings from a fine-tuned large language model. Using the DAIGT v2 dataset, which contains labeled examples of AI-generated and human-generated text, the study creates a model to predict whether a given text is AI-generated or human-written.

## Methodology

### Embedding Generation with SimCSE-RoBERTa-large
- **Model**: SimCSE-RoBERTa-large was chosen for its strength in generating high-quality sentence embeddings.
- **Fine-Tuning**: The model was fine-tuned to improve sentence embeddings using a custom loss function that combines:
  - **CoSENT**: Maximizes similarity between semantically similar sentences.
  - **In-Batch Negatives**: Incorporates in-batch negatives to help the model better distinguish between similar and dissimilar sentences.
  - **AnglE**: Optimizes angular relationships in the embedding space for enhanced alignment of similar sentences.

### Data Preparation
- **Dataset**: DAIGT v2, containing:
  - **Label 1**: AI-generated text.
  - **Label 0**: Human-generated text.
- **Sentence Similarity Pairs**: Pairs of sentences were created as follows:
  - **Label 1**: Sentence pairs with the same label (both AI or both human) were considered similar and labeled as 1.
  - **Label 0**: Sentence pairs with dissimilar labels (one AI, one human) were considered dissimilar and labeled as 0.

### 3. Fine-Tuning the Model
- The SimCSE-RoBERTa-large model was fine-tuned on these sentence pairs to better capture subtle differences between AI-generated and human-generated text.

### 4. Embedding Generation
- **Embedding Extraction**: After fine-tuning, embeddings for each sentence in the dataset were generated, capturing nuanced distinctions between AI and human text.

### 5. Neural Network Classification
- **Model Training**: A neural network model was trained to predict whether a text is AI-generated or human-written using the generated embeddings as input.
- **Objective**: The neural network classifies each sentence based on its embedding, utilizing patterns learned from the similarity data.

