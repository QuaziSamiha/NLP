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

- **Note**: The dataset contains offensive language because it’s necessary to study and solve this problem.

No worries! Let me break down **bias** and **rationales** with easy explanations and examples:

---

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

`We utilize existing state-of-the-art models and ob-serve that even models that perform very well in classificationdo not score high on explainability metrics like model plau-sibility and faithfulness. We also observe that models, whichutilize the human rationales for training, perform better in re-ducing unintended bias towards target communities.`

**4 Dec, 24**

### Introduction

![fig 1](/image/hateXplain1.PNG)

Sure! Here’s a simplified step-by-step summary of the introduction from the paper:

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
