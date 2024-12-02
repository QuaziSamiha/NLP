**1 Dec, 24**

# Towards safer online communities: Deep learning and explainable AI for hate speech detection and classification☆

- [click here](https://www.sciencedirect.com/science/article/abs/pii/S0045790624000818)
  Here’s a simplified, step-by-step summary of the abstract:

### Abstract:

1. **Problem Statement**:

   - The internet and social media help people share ideas but also create problems like `cybercrimes` (illegal online activities) and `hateful speech` (messages that hurt or target specific groups).
   - Hateful speech harms `societal harmony` (peace among people).

2. **Objective**:

   - To solve this issue, the study aims to create a fully automated **hate speech detection model** that can find and classify harmful messages quickly and accurately.

3. **Methods**:

   - **Natural Language Processing (NLP)**: Teaching computers to understand human language.
   - **Deep Learning (DL)**: Advanced machine learning that mimics how the brain works to find patterns in data.

4. **Model Architecture**:

   - The model uses:
     - **Embedding Layer**: Turns words into numerical values so the computer can process them.
     - **Convolutional Neural Networks (CNN)**: Detect patterns like repeated words or phrases.
     - **Bidirectional Recurrent Neural Networks (Bi-RNN)**: Understands context by looking at text in both forward and backward directions.
     - **Bidirectional Long Short-Term Memory (Bi-LSTM)**: A more advanced RNN layer that remembers important parts of a sentence for longer.

5. **Performance**:

   - The model achieves **98.5% accuracy**, meaning it correctly detects hateful speech most of the time.

6. **Explainable AI**:

   - To make the model understandable:
     - **SHAP (SHapley Additive exPlanations)**: Shows how much each word contributes to the final result.
     - **LIME (Local Interpretable Model-Agnostic Explanations)**: Explains why the model makes specific decisions for a given sentence.

7. **Outcome**:
   - This approach helps build safer online spaces by quickly and accurately identifying harmful content while making the system transparent (easy to understand).

- Example to understand the model:

Think of the system as a security guard:

- **Embedding**: The guard reads and understands the language.
- **CNN**: Spots patterns in suspicious messages.
- **Bi-RNN & Bi-LSTM**: Analyzes the context of the message to decide if it’s harmful.
- **SHAP & LIME**: The guard explains why it flagged a specific message as harmful, ensuring fairness.

**2 Dec, 24**

### Introduction

- 1. **What is Hate Speech?**

  - Hate speech is any message (spoken, written, or symbolic) that shows **prejudice** (bias), **hostility** (anger), or promotes **violence** against people based on their identity, such as:

    - **Race** (skin color or ethnicity)
    - **Religion** (beliefs)
    - **Gender** (male/female/other identities)
    - **Sexual orientation** (e.g., LGBTQ+)

- 2. **Online Hate Speech**

  - Online hate speech spreads through platforms like social media, websites, or forums.
  - It’s dangerous because it:
    - **Spreads quickly** to large audiences.
    - Encourages real-life **discrimination** or **violence**.
    - Harms individuals and entire communities.

- 3. **The Role of Social Media**

  - Social media provides freedom of expression but sometimes **misuses** this right to promote hate.
  - Example: Some suspects in terror incidents had a history of posting hateful messages online (e.g., the Christchurch attack in New Zealand, 2019).
  - Hate crimes are increasing. In the U.S., hate crime reports rose by **11.6%** from 2020 to 2021.

- 4. **Why Automate Hate Speech Detection?**

  - Many platforms have rules against hate speech, but identifying it **manually** is slow and inefficient.
  - Researchers are turning to **machine learning (ML)** and **deep learning (DL)**:

    - **Machine Learning (ML)**: Uses computers to learn patterns (e.g., from training data) to detect hate speech.
    - **Deep Learning (DL)**: A more advanced ML method that doesn’t rely heavily on humans creating features manually.

- 5. **Challenges of Traditional Methods**

  - **NLP (Natural Language Processing)** models are language-dependent (e.g., English or another language) and can miss slang or hidden hate speech.
  - **Out-of-vocabulary issues**: Some models can’t recognize new words or unusual spellings used to bypass detection.
  - Traditional methods rely on **feature engineering** (human-designed rules), which is time-consuming and less flexible.

- 6. **Benefits of Deep Learning**

  - DL models automatically find **relevant patterns** in text without human help.
  - They work better with messy, real-world data.
  - Example: Detecting both “I hate you” and coded slang like “IH8U.”

- 7. **Proposed Solution**

  - The study introduces an **end-to-end deep learning framework** to identify hate speech automatically.
  - Key model features:
  - **5-layer design**: Includes layers like CNN (find patterns), BiRNN (understand text direction), and BiLSTM (remember important details).
  - **Explainable AI**:
    - **SHAP**: Shows which words influenced the decision (e.g., "hate" caused the flag).
    - **LIME**: Explains predictions for specific examples.
  - Tested on three datasets, achieving a **98.5% accuracy** for classifying hate speech.

- 8. **Structure of the Paper**
  - **Section 2**: Talks about existing hate speech detection methods.
  - **Section 3**: Explains the proposed framework.
  - **Section 4**: Shares the results of the study.
  - **Section 5**: Concludes the paper.

### Related work

![table 1](/image/DeepLearning-ExplainableAI1.PNG)

- 1. **Approaches to Hate Speech Detection**

  - Researchers use two main methods for hate speech detection:
    - **Traditional Machine Learning**: Needs human-created features (like word counts). Examples: Bag of Words (BoW) and Term Frequency-Inverse Document Frequency (TF-IDF).
    - **Deep Learning**: Finds patterns automatically without manual feature creation (e.g., word embeddings like Word2Vec, GloVe).

- 2. **Traditional Techniques**

  - **Davidson et al. (2017)**:
    - Created a dataset of 2,408 tweets (hateful, offensive, and normal content).
    - Used ML classifiers like Logistic Regression and Support Vector Machines.
    - Achieved `82% accuracy` using TF-IDF features.
  - **Basile et al. (2018)**:
    - Focused on hate speech against women and immigrants (multi-lingual data).
    - Classified text into "hate" or "non-hate" and "aggressive" or "non-aggressive."
    - Best performance: `89% accuracy`.
  - **Zhou et al. (2019)**:

    - Added emotional features using a multi-task learning approach (Semantic Knowledge Sharing).
    - Used attention mechanisms to highlight important parts of the text.
    - Achieved `95.1% accuracy`.

- 3. **Deep Learning Techniques**

  - **Pelico et al.**:
    - Fine-tuned `BERT (Bidirectional Encoder Representations from Transformers)`, achieving `81% accuracy`.
    - However, BERT models are `computationally heavy` (large parameters).
  - **Mozafari et al.**:
    - Improved BERT by creating a weighted dataset to reduce errors.
  - **Saleh et al.**:

    - Used domain-specific word embeddings (`HSW2V`) and BiLSTM for classification.
    - Combined hateful and offensive classes into one category.
    - Achieved an `F1 score of 0.95`.

- 4. **Advanced Architectures**

  - **Fazil et al.**:
    - Used three parallel CNNs with different filter sizes to extract features.
    - Added BiLSTM layers for better text sequence learning.
    - Used attention layers to give importance to critical words.
    - Achieved binary classification but may not perform well on real-world data.
  - **Ali et al.**:

  - Combined graph algorithms and machine learning to detect hate and social groups.
  - Used BiLSTM-GRU for six hate categories with `98.14% accuracy`.

- 5. **Low-Resource Language Challenges**

  - Detecting hate in `low-resource languages` (like Pushto) is harder because they lack sufficient written material.
  - Example:

    - **Awal et al.**: Developed `HateMAML`, a meta-learning model adaptable for multiple languages.
    - Used multilingual encoders like `mBERT` and `XLM-R`.
    - Achieved an average `F1 score of 0.738` across 8 low-resource languages.

- 6. **Summary of Performance**

  - Models combining `deep learning layers` (like BiLSTM) with modern word embeddings (e.g., GloVe, FastText) perform well.
  - Example:
    - **Mazari et al.**: Combined BiLSTM and Bi-GRU layers with `FastText` embeddings.
    - Achieved a `ROC-AUC score of 98.63%`.
  - However, many systems need improvements for real-time or diverse language use.

- 7. **Challenges Identified**

  - Many existing systems are:
    - Computationally complex.
    - Limited to high-resource languages (e.g., English).
    - Unvalidated on real-time or diverse datasets.
