

## Project Overview

This project implements an end-to-end Natural Language Processing (NLP) pipeline to analyze patient forum posts for drug safety monitoring. The system uses a pre-trained Transformer model to automatically extract key medical entities, evaluates the model's performance against a ground truth, and links the extracted entities to standard medical concepts using both lexical and semantic methods.



### Task 1: Entity Enumeration
- The entire dataset was parsed to enumerate all distinct medical entities.
- The total count of unique terms for each primary label (`ADR`, `Drug`, `Disease`, `Symptom`) was calculated to provide an inventory of the dataset's vocabulary.

### Task 2: Named Entity Recognition (NER)
- A pre-trained biomedical Transformer model (`d4data/biomedical-ner-all`) from the Hugging Face Hub was utilized to automatically label entities in a sample text.
- The model's predictions were formatted and displayed in two required ways:
    1.  **Span-based "Original" Format:** Identifying the entity text and its character start/end positions.
    2.  **BIO (Beginning, Inside, Outside) Format:** A detailed, word-by-word labeling scheme.

### Task 3: Overall Performance Measurement
- The performance of the NER model was calculated for a sample text.
- Standard metrics—**Precision, Recall, and F1-Score**—were used to compare the model's predictions against the ground truth from the `original/` sub-directory.

### Task 4: ADR-Specific Performance Measurement
- The performance calculation from Task 3 was repeated, but with a specific focus on the `ADR` (Adverse Drug Reaction) label.
- This targeted evaluation used the specialized `meddra/` sub-directory as the ground truth to measure the model's effectiveness at identifying drug side effects.

### Task 5: Performance on a Random Batch
- The evaluation process was automated to measure the model's performance across a random sample of **50 documents**.
- The **micro-averaged** F1-Score was calculated to obtain a more robust and statistically significant measure of the model's overall capability on this dataset.

### Task 6: Entity Linking and Normalization
- A system was built to link the informal entities found by the model to standardized medical concepts from SNOMED CT.
- Two distinct matching methods were implemented and compared:
    - **Method A:** Approximate String Matching (using `fuzzywuzzy`)
    - **Method B:** Semantic Embedding Matching (using `sentence-transformers`)

***

## Dataset

This project was intended for the **CADEC (CSIRO Adverse Drug Event Corpus)**.



## Technologies Used

- Python 3.11
- Conda
- Jupyter Notebook (in VS Code)
- **PyTorch**: As the backend framework for the Transformer models.
- **Hugging Face `transformers`**: For loading and using the pre-trained NER model.
- **`sentence-transformers`**: For creating semantic embeddings for entity linking.
- **`fuzzywuzzy`**: For approximate string matching.
- **`pandas`**: For data handling and manipulation.

***

## Setup and Installation

To run this project, it is recommended to recreate the Conda environment using the provided environment.yml file.

