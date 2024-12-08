**3 Dec, 24**

# HateXplain: A Benchmark Dataset for Explainable Hate Speech Detection

### Abstract :

- **1. The Problem**

  **Hate speech** (offensive or hateful language targeting individuals or groups) is a serious issue on social media. While advanced **models** (computer programs trained to detect hate speech) are improving, there isn’t much research on:

  - **Bias** (unintended unfairness, e.g., targeting specific communities).
  - **Interpretability** (understanding why a model makes a decision).

- **2. The Solution**

  The researchers created **HateXplain**, a special dataset (collection of labeled examples) for studying hate speech in detail. This dataset includes:

  1. **Three types of labels** for each social media post:

  - **Type of speech:** _Hate speech_, _offensive speech_, or _normal speech_.
  - **Target community:** Which group is being targeted (e.g., gender, race).
  - **Rationales:** Specific parts of the post (words/phrases) that justify the label.

  2. These labels help both in detecting hate and in understanding the **why** behind the decision.

- **3. The Findings**

  - Even the best **classification models** (models that assign posts to categories like hate, offensive, or normal) don’t perform well when it comes to **explainability** (showing clear reasons for their decisions).
  - Models trained using **human rationales** (marked parts of posts that justify the decision) are:
  - **More explainable** (easier to interpret).
  - **Less biased** (reduce unfair targeting of certain groups).

- **4. Contribution to Research**

  - The dataset and code are **public** (free for researchers to use).
  - It helps researchers develop better and **fairer hate speech detection models**.

##### **Bias (Unintended Unfairness)**

- **What it means:** Bias happens when a model unfairly favors or targets certain groups or communities.
- **Example:**  
  Imagine a model trained to detect hate speech. If it unfairly labels more posts about a specific group (e.g., a minority community) as "hateful," even when they aren’t, that’s bias.
- **Why it matters:** A biased model can harm certain communities by unfairly flagging their posts or allowing real hate speech against them to slip through.

---

##### **Rationales (Reasons Behind Decisions)**

- **What it means:** Rationales are specific words or phrases in a post that explain why it’s labeled as hate speech, offensive, or normal.
- **Example:**  
  Post: _“I can’t stand those people. They are ruining everything.”_

  - Label: Hate Speech.
  - **Rationale:** The words _“I can’t stand those people”_ are marked as the reason for labeling this as hate speech.

- **Why it matters:**  
  Without rationales, it’s hard to trust a model. For instance, if the model labels the post but doesn’t show _which part_ of the post is hateful, we can’t verify or understand the decision.

`We utilize existing state-of-the-art models and ob-serve that even models that perform very well in classification do not score high on explainability metrics like model plausibility and faithfulness. We also observe that models, which utilize the human rationales for training, perform better in reducing unintended bias towards target communities.`

**4 Dec, 24**

### Introduction

![fig 1](/image/hateXplain1.PNG)

- **1. The Problem**

  - **Hate speech** online is increasing and poses a serious threat to society.
  - Some hate speech has already led to crimes against minority groups (e.g., racial or religious communities).
  - Researchers are trying to build **automatic hate speech detection models** (tools to find and flag hate speech online).

- **2. Existing Solutions and Their Issues**

  - Many **datasets** (collections of labeled examples) and **models** (programs that make predictions) for hate speech detection already exist.
  - However, these models often fail to **generalize** (work well across different types of data).
    - **Example:** A model might incorrectly label harmless mentions of commonly attacked groups (e.g., "gay," "Muslim") as hate speech.
  - Models can be **biased** (unfairly favor or target certain groups). This is often due to **trigger words** (specific terms the model sees as hateful, even when they’re not).
  - Models are also **hard to explain** because they don’t show why a decision was made.
    - **Why explanation matters:** For transparency and fairness, we need to understand why a model flagged something as hate speech. Laws like **GDPR** even require such explanations.

- **3. The Solution (HateXplain)**

  The authors introduce **HateXplain**, a new **dataset** designed to improve hate speech detection by focusing on both **accuracy** and **explainability** (making models easier to understand).

  - The dataset includes posts from Twitter and Gab (two social media platforms).
  - Each post is labeled in three ways:

    1. **Speech type:** Is it hate speech, offensive, or normal?
    2. **Target community:** Which group is targeted (if any)?
    3. **Rationales:** Which words or phrases explain the label?

  - **Rationales Example:**  
     Post: _"Those people are destroying our culture!"_
    - Label: Hate Speech.
    - **Rationale:** Words like _"destroying"_ and _"our culture"_ explain why it’s hate speech.

- **4. Why Rationales Are Useful**

  - Rationales help make model decisions more human-like.
  - Models trained with rationales can reduce **bias** and improve fairness.
  - Example: If a model knows which exact words are problematic, it won’t wrongly label posts that only mention certain communities.

- **5. Key Findings**

  - The researchers tested existing models on the HateXplain dataset.
  - While the models were accurate in labeling posts, they struggled to provide good **explanations** (their highlighted rationales didn’t always match human reasoning).
  - Training models using rationales improved both **performance** and **fairness**.

- **6. Contribution to Research**

  - HateXplain is the first dataset for hate speech detection that includes word-level annotations (specific words explaining decisions).
  - The dataset is large (20K posts) and covers multiple perspectives (speech type, target community, rationales).
  - It’s publicly available for other researchers to use, helping advance hate speech detection research.

### Related Work:

`In our paper, we utilize the concept of rationales and provide the first benchmark hate speech dataset with human-level explanations`

- **Understanding Hate Speech**

  - Hate speech causes harm by devaluing minority groups and increasing prejudice among individuals exposed to it.
  - Exposure to hate speech, especially after real-world events, can increase online hate speech (Olteanu et al., 2018).

- **Efforts in Hate Speech Detection**

  - Researchers have developed **models** (programs to identify hate speech) and created **datasets** (collections of labeled posts) to improve detection.
  - Hate speech detection datasets are now available in multiple languages (Ousidhoum et al., 2019; Sanguinetti et al., 2018), helping global research efforts.
  - Computational approaches (like machine learning models) are being developed to detect hate speech automatically (Qian et al., 2019; Aluru et al., 2020).

- **Challenges with Existing Datasets**

1. **Conflation of Hate Speech and Offensive Language:**

   - Many datasets and studies combine **hate speech** (targeted hate) and **offensive language** (impolite or hurtful words).
   - This approach overlooks the differences between offensive terms used casually (e.g., in rap lyrics) versus actual hateful content.

2. **Examples of Misclassification:**

   - Words like _"nigga"_ are commonly used by African American communities in casual, non-hateful contexts.
   - Without understanding the context, models may incorrectly flag these as hate speech.

3. **Separating Hate from Offensive:**
   - Few works (e.g., Davidson et al., 2017) attempt to separate hate speech from offensive speech.
   - Failing to do so can result in biased systems that unfairly flag posts from certain groups.

- **Authors’ Contribution**

  - This paper addresses the above challenges by providing a **new dataset** with a **three-class categorization system**:
    1. **Hate Speech:** Clearly hateful, targeting specific groups.
    2. **Offensive Speech:** Hurtful but not hateful (e.g., casual slang).
    3. **Normal Speech:** Neutral or harmless language.
  - This categorization ensures better detection and reduces bias caused by conflating hate and offensive language.

- **How This Dataset Improves Upon Existing Ones**

  - The authors use the classification system inspired by Davidson et al. (2017) to clearly separate the types of speech.
  - By highlighting the importance of **context** in understanding words, the dataset makes models more accurate and less prone to errors.
  - It focuses on creating a system that can distinguish hate from casual offensive language, improving usability for real-world platforms like social media.

- **Technical Keywords (with meanings):**

1. **Hate Speech:** Language that targets and harms specific groups.
2. **Offensive Language:** Words that are impolite or hurtful but not hateful.
3. **Dataset:** A labeled collection of text for training and testing models.
4. **Bias:** Unfair tendencies in models, often caused by improper training.
5. **Context:** The situation in which a word is used, which affects its meaning.
6. **Classes:** Categories into which text is divided (e.g., hate, offensive, normal).

#### Dataset Collection and Annotation Strategies

![fig 2](/image/hateXplain2.PNG)

- Statistic of the collected dataset
  ![fig 3](/image/hateXplain3.PNG)

- **1. Dataset Sources**

  - **Where posts were collected from:**
    - **Twitter**: A popular platform where users post short text updates.
    - **Gab**: Another social platform, known for hosting controversial discussions.
  - These platforms were chosen because many previous hate speech studies used them (e.g., Davidson et al., 2017).

- **2. Sampling Method**

  - **How posts were selected:**
    - A **lexicon** (list of hate-related words) was used to find relevant posts.
    - The authors combined lexicons from different studies (Davidson et al., 2017; Ousidhoum et al., 2019; Mathew et al., 2019a) to create a more comprehensive list.
  - **Twitter posts:**
    - Sampled randomly from tweets posted between January 2019 and June 2020.
  - **Gab posts:**
    - Used a dataset from a previous study (Mathew et al., 2019a).

- **3. Preprocessing the Data**

  - To make the dataset clean and usable:
    - **Removed reposts and duplicates:** Ensured unique posts only.
    - **Excluded links, pictures, and videos:** Kept only the text because multimedia content could bias annotators (people labeling the posts).
    - **Kept emojis:** Emojis can provide clues about the tone of a post (e.g., sarcasm or anger).
    - **Anonymized usernames:** Replaced usernames with the `<user>` token to protect privacy.

- **Key Features of This Sampling Process**

  - Ensures posts are text-only, allowing annotators to focus purely on the language.
  - Uses a broad lexicon to capture a wide variety of hate and offensive speech.
  - Protects user privacy by anonymizing names.

- **Technical Keywords (with meanings):**
  1. **Lexicon:** A list of words or phrases used to find posts related to hate speech.
  2. **Corpus:** A collection of text data used for research or training models.
  3. **Duplicate Removal:** Ensuring the dataset doesn’t include repeated posts.
  4. **Annotation:** The process of labeling data (e.g., marking posts as hate, offensive, or normal).
  5. **Preprocessing:** Cleaning and preparing data for use in research or models.
  6. **Anonymization:** Removing personal information to protect privacy.

##### Annotation Procedure

![fig 4](/image/hateXplain4.PNG)

- **1. Annotation Task on MTurk**

  - **Who annotated the data?**

    - The task was given to workers on Amazon Mechanical Turk (MTurk), a platform where people perform small online tasks for pay.

  - **Three types of annotations for each post:**

  1. **Category Label:**
     - Classifies the text as _hate speech_ (targets a group), _offensive speech_ (hurtful but not hateful), or _normal_ (neutral or harmless).
  2. **Target Group:**
     - Identifies which group (e.g., race, gender, religion) is targeted if the post is hateful or offensive.
  3. **Span Annotation:**
     - Highlights specific words or phrases in the post that explain why the post was labeled hateful or offensive.

- **2. Target Group Annotation**

  - **Purpose:**

    - To capture who is being targeted by the hateful or offensive content.
    - Annotators choose from a predefined list of groups (e.g., racial groups, religious groups).

  - **Why span annotations matter:**
    - They give deeper insight into which parts of the text contribute to hate or offense.
    - Helps researchers understand how hate or offensive speech is expressed in language.

- **3. Annotation Instructions and Interface Design**

  - **Preparing annotators for the task:**
  - Annotators were **warned** that they might encounter hateful or offensive content.
  - Detailed **instructions** were provided, including:
    - Clear definitions of _hate speech_, _offensive speech_, and _normal_.
    - Step-by-step examples showing how to label posts, choose target groups, and highlight spans.

- **Ensuring high-quality data:**

  - Annotators had to meet **strict qualifications**:
    1. **Approval Rate:** Must have a 95% or higher approval rate on past tasks.
    2. **Experience:** Must have completed at least 5,000 approved tasks on MTurk.

- **Key Benefits of This Approach**

  - Provides **detailed and reliable annotations**, ensuring the dataset is accurate and useful for training models.
  - Using **span annotations** allows models to better explain their decisions, making them more interpretable.
  - High-quality workers and clear guidelines minimize errors and improve the dataset’s value.

- **Technical Keywords (with meanings):**

1. **Annotation:** The process of labeling data for a specific purpose (e.g., marking posts as hateful or offensive).
2. **MTurk:** Amazon Mechanical Turk, an online platform for crowdsourcing tasks.
3. **Hate Speech:** Language that attacks or demeans a specific group.
4. **Offensive Speech:** Hurtful language that isn’t necessarily hateful.
5. **Span Annotation:** Highlighting parts of a text that explain why it is labeled a certain way.
6. **HIT Approval Rate:** The percentage of successfully completed tasks by an MTurk worker.

##### Dataset Creation Step

![fig 6](/image/hateXplain6.PNG)

- **1. Pilot Annotation**

  - **Goal:**

    - Test if annotators could accurately classify posts and identify target groups.

  - **Process:**

    - Each annotator worked on 20 posts.
    - They were trained with examples and explanations to understand the labeling task.

    - **Results:**

      - Out of 621 annotators, **253 were selected** for the main task based on their performance.
      - Feedback from the pilot was used to improve the process.

- **2. Main Annotation Task**

  - **Dataset Sources:**

    - Posts were collected from **Twitter** and **Gab**, popular platforms for hate speech studies.

  - **Annotation Process:**

    - Each post was labeled by three annotators.
    - Final label was decided using **majority voting** (if two out of three agreed).

  - **Dataset Size:**

    - **Twitter:** 9,055 posts.
    - **Gab:** 11,093 posts.

  - **Agreement Score:**

    - Measured using **Krippendorff’s α** (a statistical measure of agreement between annotators): 0.46, which is higher than other hate speech datasets.

- **3. Class Labels and Target Communities**

  - **Class Labels:**
    - Each post was categorized as:
      - **Hateful** (attacks a group).
      - **Offensive** (hurtful but not hateful).
      - **Normal** (neutral or harmless).
  - Posts with all three annotators disagreeing (919 cases) were excluded.

  - **Target Communities:**

    - Annotators selected target groups (e.g., **African, LGBTQ, Women**) from a predefined list.
    - Only groups appearing in **100+ posts** were included.

  - **Top Targets:**

    - **Hate Speech:** African, Islam, Jewish.
    - **Offensive Speech:** Women, Africans, LGBTQ.

- **4. Rationale Annotation**

  - **What Are Rationales?**

    - Words or phrases highlighted by annotators to explain why a post is hateful or offensive.

  - **Process:**

    - Posts labeled as hateful or offensive were sent back to annotators for rationale annotation.
    - On average, 5.48 words were highlighted per post for offensive speech and 5.47 for hate speech.

  - **Frequent Rationales:**
    - **Hate Speech:** Words like _nigger_, _kike_, and _moslems_.
    - **Offensive Speech:** Words like _retarded_, _bitch_, and _white_.

- **5. Ground Truth Attention**

  - **What Is Attention?**

    - A focus on certain words or parts of a text to explain a model’s decision.

  - **How It’s Created:**
    - Rationales from annotators are converted into **attention vectors** (lists marking important words as 1).
    - These vectors are averaged and normalized using a **softmax function** (a mathematical way to convert numbers into probabilities).
    - A **temperature parameter** is tuned to make important words stand out more.

- **Special Case for Normal Posts:**

  - Since normal posts have no rationales, all words are treated equally using a **uniform distribution**.

- **Key Statistics and Observations**

  - **Post Length:** Average length = 23.42 words per post.
  - **Common Targets:** Groups like African and Women are frequently targeted, aligning with past studies.
  - **Dataset Quality:** High-quality annotations ensure the dataset is reliable for studying hate speech and bias.

- **Technical Keywords (with meanings):**

1. **Pilot Annotation:** Initial small-scale testing to select qualified annotators.
2. **Main Annotation:** The full labeling process for the dataset.
3. **Majority Voting:** Final label is decided based on agreement by most annotators.
4. **Krippendorff’s α:** A measure of agreement between annotators.
5. **Rationale:** Highlighted text that explains why a label was assigned.
6. **Attention Vector:** A mathematical representation of important words in a text.
7. **Softmax Function:** Converts numbers into probabilities for better focus on key parts of a text.
8. **Temperature Parameter:** Adjusts how strongly the model focuses on important words.
9. **Uniform Distribution:** Treating all words equally when no rationale is available.

##### Evaluation Metrics

The research defines three key **types of evaluation metrics** for assessing hate speech detection models. Here's the simplified explanation:

- 1. **Performance-Based Metrics**  
     These metrics check how well the model classifies posts into the three classes: **Hateful, Offensive, or Normal**.
- **Accuracy**: Measures the overall correctness of predictions.
- **Macro F1-Score**: Focuses on balanced performance across all classes, even if they are imbalanced (e.g., fewer hateful posts).
- **AUROC**: Shows how well the model separates the three classes (e.g., distinguishes hate speech from normal posts).

- 2. **Bias-Based Metrics**  
     These metrics identify if the model is unfairly biased against specific communities (like African, LGBTQ). Bias can lead to incorrect labeling of normal posts as toxic due to words associated with certain communities.

**Key Metrics**:

- **Subgroup AUC**: Measures how well the model separates toxic and normal posts within a specific community (e.g., posts about Asians).
  - _Higher value_: The model is accurate for that community.
- **BPSN (Background Positive, Subgroup Negative) AUC**: Measures if the model falsely flags normal posts about a community as toxic.
  - _Higher value_: Fewer false positives for that community.
- **BNSP (Background Negative, Subgroup Positive) AUC**: Measures if the model misses toxic posts about a community.
  - _Higher value_: Fewer false negatives for that community.
- **GMB (Generalized Mean of Bias) AUC**: Combines all the bias metrics (Subgroup, BPSN, BNSP) to give a single fairness score across all communities.

- 3. **Explainability-Based Metrics**  
     These metrics evaluate **how well the model explains its decisions** using rationales (key phrases in a post that justify the label).

- Two Aspects of Explainability:

1. **Plausibility**: How convincing the model’s explanations are to humans.

   - **IOU F1-Score**: Checks overlap between model-highlighted rationales and human-highlighted rationales.
   - **Token F1-Score**: Measures precision/recall for individual highlighted words.
   - **AUPRC**: A precision-recall score for soft token selection (partial importance of words).

2. **Faithfulness**: Whether the model’s explanations match its true reasoning.
   - **Comprehensiveness**: Measures how much the prediction drops when the rationale is removed.
     - _High comprehensiveness_: The rationale is very important to the prediction.
   - **Sufficiency**: Checks if the rationale alone is enough to make the prediction.
     - _High sufficiency_: The rationale captures all necessary information for the decision.

---

### Technical Keywords:

1. **Accuracy**: How often predictions are correct.
2. **F1-Score**: A measure that balances precision (correct predictions) and recall (finding all relevant cases).
3. **AUROC**: A curve that evaluates the model’s separation ability.
4. **Bias Metrics (Subgroup AUC, BPSN, BNSP, GMB)**: Ways to measure unintended model bias for specific groups.
5. **Explainability**: How well the model's reasoning is understandable and faithful to its decisions.
6. **Comprehensiveness**: Importance of highlighted rationales to the decision.
7. **Sufficiency**: Whether the rationale alone is enough for the decision.

### Models

The research describes different models used to evaluate the dataset. Two versions of each model are considered:

1. **Class Label Training**: Models are trained only on class labels (e.g., hate speech, offensive, normal).
2. **Class Label + Attention Training**: Models are trained on class labels **and** the attention weights (importance of words in predictions). Some models, like CNN-GRU and BiRNN, cannot support attention training.

##### Models Descriptions

- 1. **CNN-GRU**

- **Structure**: Combines Convolutional Neural Networks (CNN) and Gated Recurrent Units (GRU).
  - CNN extracts patterns in word sequences using **filters** (like window sizes of 2, 3, 4 words).
  - GRU processes sequences to capture word relationships in order.
  - The output from GRU is **max-pooled** (chooses the strongest feature).
- **Purpose**: Outputs predictions after processing word sequences.

- 2. **BiRNN (Bidirectional Recurrent Neural Network)**

- **Structure**: Processes input in both forward and backward directions for better understanding of word context.
- **Layers**:

  - Input word embeddings → Sequential RNN layers → Two fully connected layers → Final prediction.
  - **Dropout** (randomly turning off parts of the model during training) is used to prevent overfitting.

- 3. **BiRNN with Attention**

- **Structure**: Same as BiRNN but includes an **attention layer**.

  - Attention identifies the **most important words** in the text for making predictions.
  - The model is trained by comparing the attention weights to **ground truth attention** (human-marked important words).

- 4. **BERT (Bidirectional Encoder Representations from Transformers)**

- **Pre-Trained Transformer Model**: Learns relationships between words and sentences.
- **Structure**:
  - Input sentence → Processes with 12 layers of attention mechanisms → CLS (special token representing the whole sentence) → Fully connected layer for predictions.
- **Attention Supervision**: Matches the attention weights of the model with **ground truth attention** to make predictions that focus on the correct words.

- Training and Hyperparameters

1. **Data Splitting**:

   - 80% for training, 10% for validation (tuning model settings), 10% for testing.
   - The split maintains a **balanced distribution of classes** (stratified split).

2. **Word Embeddings**:

   - Non-BERT models use **GloVe embeddings** (pre-trained representations of words).
   - Token length is set to 128 for faster processing.

3. **Optimizers and Learning Rate**:

   - **Adam Optimizer**: A method to improve training efficiency.
   - Non-BERT models: Learning rate = **0.001**.
   - BERT: Learning rate = **2e-5**.

4. **Model-Specific Settings**:
   - **Hidden Layer Size**:
     - BiRNN-Attention: 64.
     - BiRNN (no attention): 128.
   - **Dropout Layers**: Added at various points to prevent overfitting.
   - **λ (regularizer)**: Balances attention training loss and overall training loss.
     - Best results: λ = 100 for BiRNN-Attention and BERT-Attention.

---

### Technical Keywords:

1. **CNN-GRU**: Combines convolution for feature extraction and GRU for sequence modeling.
2. **BiRNN**: Processes input text in forward and backward directions.
3. **Attention**: Mechanism to focus on the most important parts of the input.
4. **BERT**: Pre-trained transformer model for understanding word and sentence relationships.
5. **Dropout**: Technique to prevent overfitting by turning off random parts of the model during training.
6. **GloVe Embeddings**: Pre-trained word representations capturing word meanings.
7. **Adam Optimizer**: Algorithm to improve training performance.
8. **Learning Rate**: Speed at which the model learns during training.
9. **λ (Regularizer)**: A factor controlling how much weight is given to attention training loss.

### Result

1. **Performance**: Models trained with human rationales (e.g., BiRNN-HateXplain, BERT-HateXplain) perform slightly better overall. BiRNN-HateXplain improves **plausibility** and **comprehensiveness**, while BERT-HateXplain improves **faithfulness** but slightly reduces **plausibility**.

2. **Bias**: Human rationales help reduce bias effectively, especially when community terms are included. However, bias varies across communities (e.g., Asians have lower scores, Hispanics have more false positives). BERT-HateXplain handles bias better than others.

3. **Explainability**:

   - **Best Scores**:
     - **Comprehensiveness**: BERT-HateXplain [LIME].
     - **Plausibility**: BiRNN-HateXplain [Attn].
     - **Sufficiency**: CNN-GRU.
   - **LIME** explanations are generally more faithful than attention mechanisms.

4. **Impact of λ (Regularizer)**: Increasing λ improves performance, plausibility, and sufficiency but reduces comprehensiveness.

**Takeaway**: The dataset supports building models balancing **performance, bias reduction, and explainability**, depending on the task requirements.

### Limitations of the Work

1. **Lack of External Context**:  
   The models do not use additional information like user profiles, gender, or post history, which could improve classification accuracy.

2. **Language Restriction**:  
   The work is limited to English and does not address hate speech in other languages, excluding multilingual contexts.

**Key Takeaway**: The approach is effective but lacks external and multilingual factors critical for broader applicability.

### Summary of Conclusion and Future Work:

The paper introduces **HateXplain**, a benchmark dataset for detecting hate speech. It includes **20,000 posts** from **Gab and Twitter**, annotated with:

1. **Labels**: Hate, Offensive, or Normal.
2. **Target communities**: Groups mentioned in the text.
3. **Rationales**: Specific text snippets marked by annotators to explain the label.

**Key Observations**:

- Models that perform well in classification might not provide **plausible** (human-convincing) or **faithful** (aligned with reasoning) explanations for their predictions.

**Future Work**:

- Integrating HateXplain with existing hate speech datasets (e.g., Davidson et al. 2017, Founta et al. 2018) to expand its utility and scope.

This work highlights the importance of both **accurate detection** and **explainability** in hate speech models.

#### what is `Ground Truth`?

![fig 5](/image/hateXplain5.PNG)

- **Ground Truth** refers to the actual, verified data or information used as a benchmark to evaluate models or systems in machine learning and research. It represents the most accurate and reliable answer or label for a given task, often created by human experts or reliable processes.

**Examples in Context:**

1. **Hate Speech Annotation:**
   - If a post is labeled as _"Hateful"_ by multiple annotators and verified, this label is the **ground truth**. It's what the model will learn from and aim to replicate.
2. **Image Classification:**

   - In a dataset of dog and cat images, if a picture is verified as a "dog," this label becomes the **ground truth**.

3. **Medical Diagnosis:**
   - A diagnosis confirmed by multiple medical experts based on tests and evidence serves as the **ground truth** for training models in healthcare.
     **Why Is Ground Truth Important?**

- It acts as the **standard of correctness** to evaluate machine learning models during training and testing.
- Models aim to replicate or match the ground truth to ensure accuracy.

- **In Your Dataset Context:**
  - **Ground Truth Attention**: In your hate speech study, "ground truth attention" is derived from **rationale annotations**, where annotators highlight specific words or phrases that justify a post being labeled as hateful or offensive.
  - These rationales create a verified map (attention vector) of which parts of the text are critical for the model to focus on.

This image illustrates the process of creating **Ground Truth Attention** for hate speech or offensive speech datasets. Here's a step-by-step explanation:

### **Steps in the Image:**

![fig 5](/image/hateXplain5.PNG)

1. **Input: Annotations by Annotators**

   - Three annotators (`Anno 1`, `Anno 2`, `Anno 3`) independently highlight words or phrases in the text that they believe justify the label (e.g., "Hate" or "Offensive"). These highlighted sections are called **attention spans**.

2. **Label Categorization**

   - The text is categorized into two cases:
     - **Label is Normal**: The post is labeled as neutral or "normal."
     - **Label is Offensive/Hate Speech**: The post is labeled as either "Hateful" or "Offensive."

3. **Normal Label Processing**

   - For "Normal" posts, there are no specific attention spans because the text does not contain offensive or hateful content.
   - Instead, a **uniform attention** is assigned: all tokens (words) in the sentence get equal weight. This is calculated as `1 / sentence length`.

4. **Offensive/Hate Speech Label Processing**

   - For "Hate" or "Offensive" posts:
     - The highlighted spans from all three annotators are combined, and their values are averaged to create a **combined attention vector**.
     - **Softmax Function**: This vector is normalized using a **softmax function**, which converts the values into a probability-like distribution. The softmax ensures the attention focuses on the important (highlighted) tokens while de-emphasizing the others.

5. **Final Output: Ground Truth Attention**
   - The result is a **Ground Truth Attention vector**:
     - For "Normal" posts, it is a uniform distribution across all tokens.
     - For "Hate" or "Offensive" posts, it highlights the critical tokens (words) based on annotators’ rationale.

**Purpose of Ground Truth Attention**

- It guides machine learning models to focus on the important parts of the text (e.g., offensive terms like "nigger" or "bitch") when learning to classify the post.
- It ensures that the attention mechanism in models is aligned with human reasoning.
