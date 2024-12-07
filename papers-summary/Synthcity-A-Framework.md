**30 Nov, 24**

# Synthcity: a benchmark framework for diverse use cases of tabular synthetic data

- **Paper link** : [click here](https://proceedings.neurips.cc/paper_files/paper/2023/hash/09723c9f291f6056fd1885081859c186-Abstract-Datasets_and_Benchmarks.html)

- [pip install synthcity](https://pypi.org/project/synthcity/)

- [Github](https://github.com/vanderschaarlab/synthcity)

### Abstract

1. **Why Data is Important**: Machine learning needs good data to work well, like how a recipe needs quality ingredients. But getting good data is hard because it can have private details (sensitive), be unfair or unbalanced (biased), or be expensive to collect.

2. **What is Synthetic Data?**: Synthetic data is fake but realistic data made by computers. It helps when real data isn’t available or has problems. For example, it can protect privacy or fix unfairness in real data.

3. **The Problem**: There are many types of data, like numbers in tables (tabular), events over time (time series), or pictures (images). Each type has different tools (data generator model) to create synthetic data. It’s hard to compare these data generator model because they are scattered (fragmented), and each has different uses like fixing unfairness (fairness) or creating extra data to improve models (augmentation).

4. **What is Synthcity?**: Synthcity is a Python tool (library) that makes comparing and testing synthetic data generator easy. It’s like a one-stop shop for synthetic data.

5. **What Makes Synthcity Special?**:

   - You can test different synthetic data generator with just one command.
   - It’s easy to add new data generators because it works like a plug-and-play system.
   - It gives access to many modern tools for creating synthetic data.

6. **Examples**:
   - You can use it to make fake tabular data for testing or training models.
   - It can also create extra data (augmentation) to improve your model when real data isn’t enough.

In short, Synthcity is like a helpful toolkit that simplifies using and comparing synthetic data tools (synthetic data generators) for machine learning!

**7 Dec, 24**

#### what Synthcity actually does:

1. **Provides Access to Generators**: Synthcity gives you easy access to many synthetic data generators in one place. It doesn't merge them but organizes and standardizes their use through a common interface.

2. **Simplifies Data Loading and Handling**: It helps users load real data, split it into training and testing sets, and prepare it for use with different generators, even for specific purposes like privacy or fairness.

3. **Training Generative Models**: Synthcity allows you to train any supported data generator on your dataset. This training helps the generator learn the patterns in your data to create realistic synthetic versions.

4. **Generates Synthetic Data**: Once a generator is trained, Synthcity uses it to create synthetic data. For example, it can create fake patient data for healthcare research while preserving the overall patterns in the real data.

5. **Benchmarks and Evaluates**: This is where Synthcity really stands out. It evaluates how well a generator performs by using built-in metrics. These metrics test:

   - **Fidelity**: How realistic the synthetic data is.
   - **Privacy**: How well the synthetic data protects sensitive information.
   - **Utility**: How useful the synthetic data is for tasks like training machine learning models.

6. **Facilitates Comparison**: Synthcity lets you easily compare multiple generators. It shows which generator works best for your specific need, like creating fairer data or boosting model performance.

- What Synthcity Does Not Do:
  - It doesn't combine data generators into one "super generator."
  - It doesn't just test the data generators—it helps you generate, evaluate, and use synthetic data for various tasks.

**30 Nov, 24**

### 1. Introduction

- **1. Why Good Data Matters**

  - High-quality data is crucial for AI, like fuel for a car. Without it, AI development faces big challenges, especially in important areas like healthcare or finance.
  - The three main problems are:

    - **Data scarcity**: Not enough data is available.
    - **Privacy**: Real data often contains sensitive, personal details.
    - **Bias**: Data can be unfair or unbalanced, favoring certain groups over others.

- **2. How Synthetic Data Helps**

  - **Synthetic data** is fake but realistic data created by computers.

    - It’s useful when real data is too small, private, or unfair. For example:
      - In healthcare, synthetic data can safely mimic patient data without exposing real patients’ details.

  - To create useful synthetic data, we need models that:

    - Match the patterns of the real data (**capture the data distribution**).
    - Meet specific needs, like privacy or fairness (**desired use cases**).

- **3. Current Challenges in Synthetic Data Research**

  - The field is **`fragmented`** (split into many small parts) because:

    - There are many **`data types`** (like tables, time series, or images).
    - Each type has specific **`use cases`** (e.g., making data fair, protecting privacy, or generating extra data to train models better (**`augmentation`**)).
    - Researchers have focused on creating specialized models for narrow problems, but this causes four big issues:

      - **Challenge 1: Evaluating Models for Specific Needs**

        - Most tests only check how well synthetic data looks like real data (**`fidelity`**) but ignore other needs. - For example, does the synthetic data: - Work well with AI models (**`utility`**)? - Protect privacy?

      - New methods are needed to measure these things.

      - **Challenge 2: Using Models for Unintended Purposes**

        - Models are often designed for one job, like creating private data. But in real life, they’re used for many tasks, like **`privacy and augmentation together`**.
        - This can cause problems because the model wasn’t built for all these uses.

      - **Challenge 3: Comparing Many Models**

        - There are lots of synthetic data models, but they don’t work together easily:
          - Different input formats or software make testing hard.
        - Researchers waste time fixing these problems instead of focusing on the actual study.

      - **Challenge 4: Understanding Why a Model Works**

        - Synthetic data models are complex, with many parts like:
          - **Architecture** (the way the model is built).
          - **Objective function** (the goal the model tries to achieve).
          - **Hyperparameters** (settings that affect how the model works).
        - It’s hard to tell which part of the model improves performance, making research less clear.

- **4. How Synthcity Solves These Problems**

  **`Synthcity`** is a Python library designed to make working with synthetic data easier.

  - **Key Features**:

    - Works with different data types and use cases.
    - Offers tools to test synthetic data for **`fidelity`**, **`privacy`**, and **`utility`**.
    - Lets researchers compare models consistently, saving time and effort.
    - Has an easy interface for creating and testing tabular data (like spreadsheets).

- **5. What Synthcity Offers**

  - **Consistent Comparisons**: Simplifies testing multiple models.
  - **Useful Metrics**: Measures important things like privacy and utility.
  - **State-of-the-Art Tools**: Includes modern synthetic data generators.
  - **Flexibility**: Users can customize and add new features.

- **6. Examples of Synthcity in Action**
  - **Tabular Data Generation**: Creating realistic table-like data for testing AI.
  - **Data Augmentation**: Generating extra data to improve AI training when real data is limited.

### 2. The synthcity library

#### 2.1 Overview of the synthcity workflow

![fig 1](/image/Synthcity1.PNG)

- The Synthcity library simplifies the process of `creating` and `testing` synthetic data. It follows a `unified workflow`, meaning it works the same way for all data types (e.g., tables, time-series) and use cases (like privacy or augmentation). The workflow has `four main steps`:

  - **Step 1: Loading the Real Data**

    - **What happens?**  
      The real dataset is loaded using a tool called the `DataLoader`.
    - **Key Features**:
    - Works with different types of data, like spreadsheets (`tabular data`) or sequences over time (`time series`).
    - Lets users label important parts, like marking private data for privacy tools.
    - **Example**: Imagine loading patient records for healthcare research. You can specify that the "age" column is sensitive and should be handled carefully.

  - **Step 2: Training the Generator**

    - **What happens?**  
      A synthetic data generator is chosen and trained using a tool called the `Plugin`.
    - **How it works**:
    - The generator learns the patterns in the real data (like relationships between columns).
    - The `fit() method` trains the generator on the training part of the real data.
    - **Example**: A generator could learn how customers' spending patterns relate to their income.

  - **Step 3: Generating Synthetic Data**

    - **What happens?**  
      After training, the generator creates synthetic data using the `generate() method`.
    - **Extra Feature**: Some generators allow you to guide the output. For example, you could ask for synthetic data only for customers with high incomes (`conditional generation`).
    - **Example**: Once trained, the generator could create fake customer profiles for testing a new marketing strategy.

  - **Step 4: Evaluating Synthetic Data**

    - **What happens?**  
      The synthetic data is tested to see how good it is using the **Metrics** tool.
    - **Key Points to Check**:
    - **Fidelity**: Does it look like the real data?
    - **Privacy**: Does it protect sensitive information?
    - **Utility**: Can it be used to train AI as effectively as real data?
    - **Example**: If synthetic customer data is used to train a sales prediction model, does the model perform as well as it would with real data?

  - **Bonus: One-Step Benchmarking**

    - **Simplified Option**:  
      The `Benchmark` tool combines all four steps into one.
    - Load data, train the generator, create synthetic data, and evaluate—all with one command.
    - It gives you a report showing how the generator performed.

- **How Does It Work?**

  - **Real Data**: The real dataset is split into two parts:
  - **Training Data**: Used to teach the generator.
  - **Test Data**: Used to check how well the synthetic data matches the real data.
  - **Generator’s Goal**: Learn the patterns in the training data and create synthetic data that mimics these patterns.

**7 Dec, 24**

### 3 Comparison with existing libraries

![table 3](/image/synthcity/table3.PNG)

- **Comparison with Other Libraries**  
  Synthcity is compared with other popular libraries for synthetic data generation, such as:

  - **YData Synthetic**
  - **Gretel Synthetics**
  - **SDV**
  - **DataSynthesizer**
  - **SmartNoise**
  - **nbsynthetic**

- **Key Points of Comparison**

1. **Scope of Use Cases and Data Types**:

   - Synthcity supports many more use cases (e.g., privacy, fairness, augmentation) and data types (e.g., tables, time-series) than these libraries.
   - Other libraries often focus on just one specific problem or data type.

2. **Range of Generators**:

   - Synthcity includes both `deep generative models` (like GANs) and `traditional models`, offering more variety than others.

3. **Evaluation Tools**:
   - Synthcity has a `built-in evaluation system` to check the quality of synthetic data (e.g., how realistic or private it is).

- **Why Synthcity Stands Out**

  - Synthcity is designed as a `benchmark framework`, meaning it’s built to compare and test different models systematically, not just solve one problem.
  - Its broad range of tools and evaluation metrics makes it a unique and comprehensive option for synthetic data research.

    - A `benchmark framework` is like a tool designed to `compare and evaluate` many different options or models in a fair and organized way.

      For example:  
      Imagine you want to compare different phones (Apple, Samsung, Google) to find the best one for you. A benchmark framework would help you:

      1. Test each phone on the same things, like battery life, camera quality, and speed.
      2. Show you a clear comparison of their strengths and weaknesses.

      Similarly, **Synthcity** helps researchers:

      1. Compare many synthetic data models (tools that create fake data) in a consistent way.
      2. Test them for different tasks (e.g., privacy, fairness, or data quality).

      Unlike other tools that are built to solve just one problem (like creating private data or fixing bias), Synthcity is made for `evaluating and comparing all types of synthetic data models` systematically.

### 4 Illustrative case studies

Here’s both the **summary** and **explanation** for better understanding:

---

### **Why This Section Exists**

This section demonstrates **how Synthcity works in real-world scenarios**. It uses two specific examples (static tabular data and fairness/data augmentation) to:

1. Show the **type of problems Synthcity can solve**.
2. Highlight **how Synthcity simplifies and improves benchmarking** for synthetic data models.
3. Provide evidence of Synthcity’s capabilities compared to other tools.

---

### **Example 1: Generating Static Tabular Data**

#### **Why This Example?**

- Tabular data (structured rows and columns like spreadsheets) is very common in real-world projects (e.g., finance, healthcare).
- Researchers need to know which synthetic data generator produces the most **accurate** (realistic) and **useful** (usable for analysis) synthetic data.

#### **What It Does?**

1. **Models Compared**:  
   Synthcity benchmarks many algorithms, including:
   - **ARF (tree-based)**: Uses decision trees to understand and replicate data.
   - **GANs**: Models that create fake data by competing between two networks.
   - **VAEs**: Simplifies data to its core features and reconstructs it.
   - **Diffusion Models**: Creates data by refining it from random noise.
2. **Data Used**:

   - 18 datasets from OpenML, which are diverse in size (small and large) and complexity (few or many features).

3. **Evaluation Metrics Explained**:  
   To check synthetic data quality, these metrics are used:

   - **α-Precision**: Does the synthetic data match real data points closely?
   - **β-Recall**: Does it capture the diversity of real data?
   - **Authenticity**: Does the synthetic data look realistic overall?
   - **Detection Score**: Can people or models easily tell the difference between real and synthetic data? Lower is better.

4. **Results**:
   - Tree-based models like ARF performed surprisingly well, competing with deep learning models.
   - Suggests simpler models (e.g., tree-based) are worth exploring further.

---

### **Example 2: Fairness and Data Augmentation for Tabular Data**

#### **Why This Example?**

- In real-world datasets, some groups (minorities) may be **underrepresented**. Models trained on such data often perform poorly for these groups, leading to **bias**.
- **Data augmentation** (creating more synthetic examples for minority groups) can fix this issue and improve **fairness** (equal model performance for all groups).

#### **What It Does?**

1. **Dataset Used**:

   - COVID-19 data from Brazil with records of patients’ outcomes.
   - Majority groups: "Mixed" and "White."
   - Minority groups: "Black," "East Asian," and "Indigenous" (fewer than 10% of the dataset).

2. **Problem**:

   - Models predict outcomes poorly for minority groups because the training data has too few examples from these groups (**imbalance issue**).

3. **Models Compared**:  
   Synthcity tests several synthetic data generators for creating more data for minority groups:

   - **RadialGAN**: Specifically made for augmenting data across domains (e.g., minority vs. majority groups).
   - **TabDDPM, CTGAN, TVAE**: Modern data generators that create conditional synthetic data based on specific features.

4. **Evaluation Metrics Explained**:

   - **AUROC (Area Under the Receiver Operating Curve)**: Measures how well models predict outcomes. Higher scores mean better predictions.

5. **Results**:
   - Synthetic data improved predictions for minority groups across all models.
   - **TabDDPM** (a diffusion model) was the best performer, showing promise for fairness improvement.

---

### **Takeaways**

1. Synthcity can handle a wide range of tasks, including **data quality benchmarking** and **fairness improvement**.
2. It simplifies the process by providing pre-configured pipelines, saving time and avoiding common mistakes (e.g., data leakage).
3. These examples prove Synthcity is not just theoretical—it’s practical and impactful for real-world problems.
