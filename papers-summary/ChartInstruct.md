**26 Oct, 24** and **23 Oct, 24** `Saturday`

# ChartInstruct:Instruction Tuning for Chart Comprehension and Reasoning

- **link** : (https://arxiv.org/abs/2403.09028)
- **Github link** : (https://github.com/vis-nlp/ChartInstruct)

## Abstract

Charts are widely used to analyze data and answer questions. Recently, tasks like chart question-answering and summarization have gained attention. Existing methods usually fine-tune models designed for vision or language tasks, but these are limited to specific tasks.

To address this, the researchers created **ChartInstruct**, a dataset with 191,000 instructions from 71,000 charts, designed for teaching models how to work with charts. They developed two systems:

1. **End-to-end model**: Combines a chart image processor with a language model.
2. **Pipeline model**: Extracts chart data into tables first, then uses a language model for reasoning.

These systems achieved top results on multiple tasks and showed the ability to handle many real-world chart-related problems, making them more versatile than previous models.

#### Simple Definitions:

1. **Fine-tuning**:

   - Teaching an existing AI model to perform a specific task by training it on new, smaller datasets related to that task.
   - Example: A general language model fine-tuned on medical text to answer health-related questions.

2. **Instruction Tuning**:

   - Training a model to follow specific types of instructions by providing examples of tasks in a structured way.
   - Example: Teaching a model to answer questions, summarize, or explain charts based on given prompts.

3. **End-to-End Model**:

   - A single system that handles everything from start to finish.
   - Example: Taking a chart image, understanding it, and directly generating a response in one process.

4. **Pipeline Model**:

   - A multi-step system where each step does a specific task in sequence.
   - Example: First extract data from a chart into a table, then process the table to answer questions.

5. **Vision Encoder**:
   - A tool that helps a model "see" and understand images (like charts or photos) by converting visual information into a format the model can use.
   - Example: Recognizing chart elements like bars, lines, or labels.

In short: Fine-tuning and instruction tuning are ways to customize models for tasks. End-to-end models are all-in-one solutions, while pipeline models break tasks into steps. A vision encoder helps models understand images.

## Introduction

![fig: 1](/image/ChartInstruct1.PNG)

Charts, like bar and line graphs, are important for analyzing data and making decisions, but understanding them and answering complex questions about them can be difficult. Researchers have worked on tools to help with tasks like answering questions about charts, summarizing them, and checking facts. Early methods used models trained for general tasks but weren’t great at understanding specific chart features like bars, legends, or axes.

Some newer models are designed for charts but focus on a narrow set of tasks or types of charts, limiting their real-world usefulness. A better approach is `instruction tuning`, which has been successful in making models like ChatGPT better at following user instructions for a wide range of tasks. However, this method hasn’t been fully applied to charts yet.

This paper introduces `ChartInstruct`, a large `dataset` created from 157 websites with a variety of chart styles. Using advanced AI models like GPT-4, it generates 191,000 instructions for different chart-related tasks, aiming to build a versatile tool for understanding and reasoning about any type of chart.

- Charts are different from regular visual data, so a structured approach is needed to train AI models to handle them effectively. This paper introduces two innovative systems for chart analysis:

  1. **Improved Vision-Language Model (VLM)**:

  - It upgrades an existing system (LLaVA) by replacing its image processor with a specialized **UniChart vision encoder**, designed for charts.
  - Two types of language models are tested for understanding and generating responses:
    - **Llama2 (decoder-only)**
    - **Flan-T5-XL (encoder-decoder)**

  2. **Two-Step Pipeline**:

  - First, extract the chart's data into a table.
  - Then, use a language model to process the data and answer questions or provide insights.

- These models are evaluated on four major chart analysis tasks and achieved top results. Human evaluations confirm their effectiveness in understanding charts and solving real-world problems.

- Key Contributions:

  1. A new dataset of real-world charts with diverse tasks.
  2. Two systems specifically designed for chart analysis.
  3. Open-source tools and dataset for further research.

  In short, this research provides powerful tools for AI to better understand and work with charts in various real-world scenarios.

**24 Nov, 24**
![fig: 1](/image/ChartInstruct1.PNG)

Here’s a simple example for each task shown in the image:

- **1. Chart Summarization**

  **Task:** Summarize the information in a chart.  
   **Example:**  
   A bar chart shows the population of a city from 2000 to 2020, increasing from 1 million to 3 million.  
   **Output:** The population of the city grew steadily from 2000 to 2020, tripling in size.

- **2. Chain-of-Thought Reasoning**

  **Task:** Use step-by-step reasoning to answer a question based on a chart.  
   **Example:**  
   A line chart shows car sales in 2019: January had 100 sales, and December had 200 sales.  
   **Question:** How many more cars were sold in December compared to January?  
   **Output:** Subtract sales in January from sales in December: 200 - 100 = 100. The answer is 100 more cars.

- **3. Open-Ended Question Answering**

  **Task:** Answer a question based on chart trends without strict numerical focus.  
   **Example:**  
   A chart shows a sharp increase in online shopping during 2020.  
   **Question:** Why did online shopping increase in 2020?  
   **Output:** Online shopping likely increased due to the COVID-19 pandemic, which limited physical store access.

- **4. Coding Abilities**

  **Task:** Write a small code snippet based on chart data.  
   **Example:**  
   **Question:** Find the month with the highest sales from this data: {Jan: 10, Feb: 20, Mar: 15}.  
   **Output (Python code):**

  ```python
  sales = {"Jan": 10, "Feb": 20, "Mar": 15}
  max_month = max(sales, key=sales.get)
  print(max_month)  # Output: Feb
  ```

- **5. Fact Checking**

  **Task:** Verify a claim based on a chart.  
   **Example:**  
   A pie chart shows 60% of students prefer online classes, 40% prefer in-person.  
   **Claim:** Most students prefer in-person classes.  
   **Output:** The claim is false. The chart shows that most students prefer online classes (60%).

- **6. Anomaly Detection**

  **Task:** Identify unusual trends in chart data.  
   **Example:**  
   A line chart shows consistent growth in sales from 2010 to 2020, except for a drop in 2015.  
   **Output:** 2015 shows an anomaly with a sales drop, unlike the consistent growth trend.

- **7. Chart Title Extraction**

  **Task:** Extract or create a title for a chart.  
   **Example:**  
   A chart shows smartphone usage from 2010 to 2020.  
   **Output:** **"Growth in Smartphone Usage Over a Decade"**

- **8. Data Correlation**

  **Task:** Identify relationships between data trends.  
   **Example:**  
   A chart shows higher exercise levels correlate with lower obesity rates.  
   **Question:** What does the chart suggest about exercise and obesity?  
   **Output:** The chart suggests that increased exercise levels are associated with lower obesity rates.

- **9. Future Forecasting**

  **Task:** Predict future trends based on chart data.  
   **Example:**  
   A chart shows a company's revenue growing by 10% yearly from 2015 to 2020.  
   **Question:** What is the expected revenue in 2021 if the trend continues?  
   **Output:** If revenue grows by 10% again, it will be 1.1 times the 2020 value.
