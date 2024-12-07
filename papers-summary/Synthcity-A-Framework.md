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

  - The field is `fragmented` (split into many small parts) because:

    - There are many `data types` (like tables, time series, or images).
    - Each type has specific `use cases` (e.g., making data fair, protecting privacy, or generating extra data to train models better (`augmentation`)).
    - Researchers have focused on creating specialized models for narrow problems, but this causes four big issues:

      - **Challenge 1: Evaluating Models for Specific Needs**

        - Most tests only check how well synthetic data looks like real data (`fidelity`) but ignore other needs. - For example, does the synthetic data: - Work well with AI models (`utility`)? - Protect privacy?

      - New methods are needed to measure these things.

      - **Challenge 2: Using Models for Unintended Purposes**

        - Models are often designed for one job, like creating private data. But in real life, they’re used for many tasks, like `privacy and augmentation together`.
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

  `Synthcity` is a Python library designed to make working with synthetic data easier.

  - **Key Features**:

    - Works with different data types and use cases.
    - Offers tools to test synthetic data for `fidelity`, `privacy`, and `utility`.
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

![fig 1](/image/synthcity/fig1.PNG)

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

#### 2.2 Evaluation for diverse use cases

![table 1](/image/synthcity/table1.PNG)

- Why Evaluate Synthetic Data?
  Synthetic data has many uses, like:
  - **Fairness**: Making sure models treat everyone equally.
  - **Privacy**: Protecting sensitive information.
  - **Data Augmentation**: Creating extra data to improve model training.

To ensure synthetic data works well for these goals, Synthcity evaluates it using specific metrics (measurement tools). Here's how it works for a basic task:

##### **2.2.1 Standard Data Generation**

This is the simplest use case: creating synthetic data that looks as much like the real data as possible. Synthcity uses `fidelity metrics` to check this.

- What is Fidelity?
  Fidelity measures how closely synthetic data matches real data. It's like comparing a copy of a painting to the original—how similar are they?

- How Synthcity Measures Fidelity:

  1. **Distributional Metrics**: These compare patterns in real and synthetic data.

  - **Jensen-Shannon Distance**: Measures how "far apart" the two data distributions are.
  - **Wasserstein Distance**: A metric for comparing how features in the data are distributed.
  - **Maximal Mean Discrepancy**: Tests if the synthetic data has the same overall "feel" as real data.

  _Example_: If you create synthetic sales data, these metrics check whether the total sales per month match the real data's pattern.

  2. **Detection Scores**: These test how easy it is to tell synthetic data apart from real data. If a classifier (a model that categorizes data) can easily separate them, the synthetic data might not be realistic enough.

  _Example_: If fake patient data is clearly distinguishable from real patient data, the generator needs improvement.

- Why Synthcity Does This:
  By using these metrics, Synthcity ensures that the synthetic data is a faithful representation of the real data, making it reliable for tasks like training machine learning models or testing new algorithms.

##### 2.2.2 Cross domain augmentation

- What is Cross-Domain Augmentation?  
  Sometimes, data comes from different sources or "domains" (like different countries or regions). One domain might have very little data (e.g., remote areas). **Cross-domain augmentation** involves creating extra synthetic data for the scarce domain by using knowledge from related domains.

- How Synthcity Handles Cross-Domain Augmentation

  1. **Goal**: To make up for data shortages in one domain by generating additional data using patterns learned from other domains.

  - _Example_: If there’s little healthcare data from rural areas but a lot from cities, Synthcity uses city data to help generate rural healthcare data.

  2. **How It Works**:

  - The system learns which features are `domain-specific` (unique to one domain) and which are `domain-agnostic` (common across domains). This helps the generator transfer knowledge across domains efficiently.

  3. **User-Friendly Interface**: With Synthcity, users can benchmark cross-domain augmentation tasks with just one command, saving time and effort.

- Measuring Success with "Utility"

  1. **Train-on-Synthetic, Evaluate-on-Real**:

  - A `predictive model` is trained using synthetic data (including the augmented data for the scarce domain).
  - The model is tested on real data from the scarce domain to see how well it performs.
  - _Example_: Train a model on synthetic patient data (augmented rural data) and test it on real rural patient data to predict health outcomes.

  2. **Predictive Models Supported**:

  - Synthcity works with popular models like `XGBoost`, `neural networks`, and traditional models like `linear regression`.

  3. **Baseline Comparison**:

  - Synthcity also shows the performance of a model trained without any data augmentation. This helps users compare whether the synthetic data actually improves results.

  4. **Automation and Error Prevention**:

  - Synthcity has a built-in pipeline that automates the process, reducing programming errors and complexity.

- Why Cross-Domain Augmentation is Important:

  - Solves the problem of `data scarcity` in specific domains.
  - Ensures predictive models perform better by filling in gaps in real-world data.
  - Helps in tasks like improving healthcare predictions for underrepresented groups.

##### 2.2.3 Synthetic data for ML fairness

- What is Fairness in ML?  
  When machine learning (ML) models work unfairly (e.g., predicting better for some groups but worse for others), it's often because the data they were trained on is biased or unbalanced. Synthcity helps address fairness by using `synthetic data` in two ways:

- 1. **Balancing Distribution**

  - **Problem**: Some groups (like minorities) might have less representation in the dataset. This can lead to biased ML models that don't perform well for these groups.

    - _Example_: In a dataset for job applications, there might be fewer records of women applying for technical roles, leading to biased hiring predictions.

  - **Solution**:
    - Generate synthetic data specifically for the underrepresented group (e.g., women) to balance the dataset.
    - This involves learning the conditional distribution **P(X|G)**, where **G** is the group label (e.g., gender, ethnicity).
    - The goal is to add more realistic examples for the minority group to make the dataset more balanced.

- 2. **Causal Fairness**

  - **Problem**: Real-world datasets often reflect societal biases (e.g., unequal healthcare access). Training ML models on such data can perpetuate these biases.

    - _Example_: A healthcare dataset might prioritize treatments for certain groups over others due to historical inequalities.

  - **Solution**:
    - Create synthetic data that removes these biases while still resembling the real data.
    - This requires learning a **bias-free distribution** (**P̂(X)**) that stays close to the original data distribution (**P(X)**) for accuracy but removes unfair patterns.
    - **Causality concepts** help identify and remove bias during data generation.
    - _Example_: Generating healthcare data that ensures equal treatment prediction regardless of income or ethnicity.

- Why is this Important?

  - Ensures ML models are **fair** and work well for all groups, not just the majority.
  - Synthetic data can help avoid discrimination in sensitive areas like hiring, healthcare, or credit scoring.
  - Synthcity provides tools for both methods (balancing and causal fairness) to make fairness testing and improvements easier.

##### 2.2.4 Synthetic data for privacy

- Why Privacy is Important in Data?  
  When creating synthetic data, it is crucial to protect sensitive information (e.g., names, addresses, medical records) to avoid privacy breaches. Synthcity addresses this using two main approaches:

- 1. **Differential Privacy (DP)**

  - **What is DP?**  
    A mathematical method to ensure privacy by adding `noise` (small random changes) to data or the data creation process. This makes it hard to trace any specific individual's data in the dataset.

  - **How does it work in synthetic data?**
    - Noise can be added to training algorithms, like changing gradients (adjustments during training) or using a noisy GAN discriminator (part of the model that evaluates generated data).
    - _Example_: A model generating patient data would add enough randomness so no one can figure out if a specific patient’s data is included, while still creating realistic health data.

- 2. **Threat Model (TM)**

  - **What is TM?**  
    A method designed to protect against specific privacy risks, such as:

    - **Membership inference**: Determining if someone’s data is part of the dataset.
    - **Attribute inference**: Guessing sensitive details (e.g., salary).
    - **Re-identification**: Identifying individuals in anonymized datasets.

  - **How does TM work?**
    - Uses techniques like regularization (fine-tuning the model to reduce overfitting) to lower the chances of privacy attacks.
    - _Example_: Making sure that even if someone knows part of your information, they cannot accurately guess the rest.

- Synthcity’s Privacy Tools

  - **Privacy Metrics**:

    - Synthcity uses standard privacy measures like:
      - **k-anonymity**: Ensuring that at least `k people` share the same characteristics (e.g., age, job) so individuals can't be singled out.
      - **l-diversity**: Making sure there’s enough diversity in sensitive attributes (e.g., health condition) to prevent guessing.

  - **Privacy Attack Simulations**:
    - Synthcity can simulate privacy attacks, such as `re-identification attempts`, to test if the synthetic data protects privacy.
    - The result of these tests helps measure how well the synthetic data preserves privacy.

- Why is this Important?

  - Protects sensitive data in areas like healthcare, finance, and personal records.
  - Ensures that synthetic data can be shared safely without risking individual privacy.
  - Synthcity makes it easy to evaluate and improve privacy protection in synthetic data generation.

##### 2.2.5 Evaluating off label use cases

- What is an Off-Label Use Case?  
  An `off-label use case` refers to using a generative model for purposes it wasn’t originally designed for. For example:

  - Evaluating the `privacy` of synthetic data generated by a model that wasn’t specifically built for privacy.
  - Checking the `fairness` of data created by a model designed for privacy (like one using Differential Privacy).

- How Synthcity Helps with Off-Label Evaluation

  1. **Flexible System Design**:

  - **Separate Modules**: Synthcity separates its generative models (`PlugIns`) and evaluation metrics (`Metrics`) into different components.
  - This means you can "mix and match" any model with any evaluation method.
  - _Example_: You can use a fairness evaluation metric on a model that wasn’t created with fairness in mind.

  2. **Consistent Interface**:

  - Synthcity provides a uniform way to combine different models and metrics, making it easy to run complex benchmark studies with minimal effort.

- Why is This Useful?

  - Allows researchers to test models in unexpected or creative ways.
  - Enables new research ideas, like exploring whether privacy-focused models are unintentionally fair or vice versa.
  - Simplifies benchmarking, saving time and reducing errors.

- Example for Better Understanding  
  Imagine a researcher working with a synthetic dataset generated by a **basic generative model** (no privacy or fairness features). They can still use Synthcity to:
  - Test how private this data is by simulating privacy attacks.
  - Check if the dataset is fair across different groups, even if fairness wasn't the model's focus.

#### 2.3 Baseline generative models

![table 2](/image/synthcity/table2.PNG)

- What Does Synthcity Do Here?  
  Synthcity is a `benchmarking framework` that includes a large collection of pre-built generative models. These models allow users to easily compare different methods without worrying about the technical details of implementation.

- Types of Generative Models in Synthcity

  1. **Deep Generative Models**:

  - These models are based on advanced machine learning techniques like `neural networks`.
  - Major families supported:
    - **GANs (Generative Adversarial Networks)**: Create data by making two models (generator and discriminator) compete with each other. Example: CTGAN (specialized for table-like data).
    - **VAEs (Variational Autoencoders)**: Use probabilities to generate data while learning how the real data is structured. Example: TVAE.
    - **Normalizing Flows (NF)**: Transform simple data distributions into more complex ones using mathematical functions. Example: FourierFlow for time-series data.
    - **Diffusion Models (DDPM)**: Start with random noise and refine it into meaningful data. Example: TabDDPM (for table data).

  2. **Non-Deep Generative Models**:

  - These models don't rely on neural networks and include:
    - **Bayesian Networks**: Models based on probabilities. Example: Predicting outcomes like weather or disease.
    - **Adversarial Random Forests (ARF)**: A tree-based generative model that competes with itself to generate data.

  3. **Data Modalities Supported**:

  - **Static Data**: Example: Tables like Excel sheets (e.g., TVAE, ARF).
  - **Time-Series Data**: Data over time, like stock prices (e.g., TimeGAN, FourierFlow).
  - **Censored Data**: Data with incomplete records, like medical trials (e.g., Survival GAN).

- How Synthcity Makes It Easy

  - **Unified Interface**: All generative models are implemented through a `PlugIn system`. This means users can easily add or test new models using the same framework.
  - **Comprehensive Tutorials**: Synthcity’s GitHub includes guides to help users add their own models step by step.

- Why Is This Important?

  - Provides a **one-stop solution** for testing and comparing synthetic data generators.
  - Covers a **wide variety** of methods and data types, making it suitable for diverse applications.
  - Saves time and effort for researchers by eliminating the need to reimplement existing methods.

- Example for Better Understanding  
  Imagine a researcher working with a dataset of heart patients. Synthcity lets them:

  - Compare a GAN-based model like CTGAN with a Bayesian network to see which one generates more realistic synthetic patient records.
  - Add their own generative model into Synthcity’s framework if it’s not already included.  
    This flexibility makes Synthcity a powerful tool for researchers in synthetic data.

#### 2.4 Architecture and hyper-parameters

- Purpose  
  Synthcity helps researchers `test and compare deep generative models` fairly by letting them:

  1. Choose different `network architectures` (how the model is structured).
  2. Adjust `hyper-parameters` (settings that control how the model learns).

- Key Features

  1. **Customizable Architectures**

  - Researchers can pick from various pre-built architectures for different types of data.
  - **Example**: For time-series data (e.g., stock prices or patient health trends), Synthcity supports 12 types of architectures, such as:
    - **LSTM (Long Short-Term Memory)**: Useful for data with sequences (e.g., predicting future stock prices).
    - **GRU (Gated Recurrent Unit)**: Like LSTM but simpler and faster.
    - **Transformer**: A model good at understanding relationships in data, used in chatbots like GPT.
    - **InceptionTime**: Specially designed for time-series data analysis.
  - For other types of data (e.g., tables), Synthcity provides additional architectures listed in the Appendix of the paper.

  2. **Flexible Hyper-parameters**

  - **Hyper-parameters** are settings that fine-tune a model’s behavior, like:
    - Learning rate: How fast the model learns.
    - Batch size: How much data the model processes at once.
  - **Synthcity Features for Hyper-parameters**:
    - Allows listing, adjusting, and testing all relevant settings.
    - Compatible with `hyper-parameter optimization libraries` like `Optuna`, which automates the process of finding the best settings.
    - Lets users try multiple settings and choose the best-performing combination.

  3. **Early Stopping Rules**

  - **What it is**: A method to stop training a model early if it's not improving, to save time and resources.
  - Synthcity lets users set and compare early stopping rules across models.

  - Why This Is Useful

    - Researchers can test **multiple setups** of the same model to understand what works best.
    - Makes comparing different models fair and consistent by ensuring they are optimized properly before evaluation.
    - Saves time by automating processes like hyper-parameter tuning and early stopping.

- Example for Better Understanding

  Imagine you’re testing two models to generate synthetic data:

  - **Model A**: Uses LSTM architecture and a learning rate of 0.01.
  - **Model B**: Uses Transformer architecture and a learning rate of 0.001.  
    With Synthcity, you can:

  1. Easily switch between architectures for testing.
  2. Optimize the learning rate for both models using `Optuna`.
  3. Set early stopping rules to avoid wasting time on training a model that isn't improving.  
     This way, you can figure out which model and settings work best without needing separate tools for each step.

#### 2.5 Data modalities

![fig 2](/image/synthcity/fig2.PNG)

- **What are Data Modalities?**

**Data modalities** describe the types and structures of data that Synthcity can handle. It supports various tabular data types, which include combinations of **continuous** (e.g., age), **categorical** (e.g., gender), **integer** (e.g., count), and **censored** features (used in survival analysis like tracking patient recovery times).

- 1. **Single Dataset**

A **single dataset** is like a single table (e.g., a Pandas DataFrame) containing rows (data points) and columns (features).  
 Synthcity organizes these by two axes:

- a. **Observation Pattern**

  This describes how data is collected over time:

  - **Static data**: Data doesn't change over time (e.g., a snapshot of customer profiles).
  - **Regular time series**: Data collected at consistent time intervals (e.g., daily stock prices).
  - **Irregular time series**: Data collected at random intervals (e.g., medical test results on different dates).  
    Synthcity supports all these types.

- b. **Feature Type**

  This defines the type of data in each column:

  - **Continuous**: Values like height or temperature.
  - **Categorical**: Fixed categories, like "yes" or "no."
  - **Integer**: Whole numbers like counts.
  - **Censored features**: Used in survival analysis, where each entry shows two values:

    - \( x \): How long something lasts (e.g., survival time).
    - \( c \): Whether the event was observed (1) or not (0).  
      Example: In healthcare, \( x = 100 \) (days survived), \( c = 0 \) (patient still alive).

- 2. **Composite Dataset**

A **composite dataset** combines multiple datasets.  
 Synthcity handles:

- **Static datasets from different domains**: For example, customer data from different regions.
- **Static and time-series datasets combined**:  
  Example: A patient’s medical record might include:

  - Static data: Age, gender, diagnosis.
  - Time-series data: Blood pressure readings over months.

- Future Enhancements  
  Synthcity plans to support additional data types, like:

  - Relational database-style data (data stored in interconnected tables).
  - Richly annotated images (e.g., images with labels).
  - Text data (e.g., articles or chat logs).

- Why This Matters  
  Synthcity makes it easy to work with various data types for tasks like generating synthetic data, testing models, and benchmarking, all within a consistent framework. Whether you have simple static data or complex combinations like time-series and static datasets, Synthcity supports it all.

### Future Work

- In future versions, we plan to include more data modalities including relational database-style data, richly annotated images, and texts

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
