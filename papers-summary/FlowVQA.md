`16 Nov, 24`

# FlowVQA: Mapping Multimodal Logic in Visual Question Answering with Flowcharts

- `Paper link` : (https://arxiv.org/abs/2406.19237)
- `All resource` : (https://flowvqa.github.io/)

## Abstract

### Visual Question Answering (VQA)

- Visual Question Answering (VQA) refers to a task where an AI system is given an image and a question about that image, and it must provide the correct answer based on the visual content.

##### How it Works:

1. `Input`:
   - An `image`: This could be a photo, chart, flowchart, or diagram.
   - A `question`: A natural language query about the image, such as “What is the color of the car?” or “What is the highest value in this bar chart?”
2. `Output`: The AI gives a response, such as a word, phrase, or even a sentence that answers the question.

##### Example:

- `Image`: A picture of a cat sitting on a sofa.
- `Question`: "What is the animal in the image?"
- `Answer`: "Cat."

##### Applications:

- `Charts/Diagrams`: Interpreting flowcharts or graphs.
- `Medicine`: Analyzing medical images (like X-rays) based on questions.
- `Education`: Helping students understand visuals in textbooks.
- `Accessibility`: Assisting visually impaired individuals by answering questions about their environment.

In short, VQA combines computer vision (to "see" the image) and natural language processing (to understand the question and generate the answer).

### Multimodal logic:

- Multimodal logic is a branch of logic that deals with reasoning across multiple "modes" or types of information. Each mode represents a different way of interpreting or reasoning about data, such as `possibility`, `necessity`, `knowledge`, `time`, or `even modalities like vision and language`\*\*.

- In Simple Terms: Multimodal logic is about combining and working with `multiple kinds of reasoning` or `sources of information` to draw conclusions.

##### Example in AI:

- In `multimodal AI`, where models process text, images, and other data types, `multimodal logic` helps the system:

1. Reason about visual information (e.g., "What’s in this image?")
2. Combine it with textual data (e.g., "Does the caption match the image?")
3. Make a decision based on both.

##### Why It’s Useful:

- `Human-like Understanding`: Humans naturally combine different types of information (e.g., seeing a traffic light and reading road signs). Multimodal logic helps machines do the same.
- `Improved Reasoning`: Models using multimodal logic can make more accurate and robust decisions by considering all available information.

##### Applications:

- `Autonomous Vehicles`: Combining sensor data (like images, radar) and maps to make driving decisions.
- `Visual Question Answering (VQA)`: Interpreting charts or flowcharts by linking text and visuals logically.
- `Robotics`: Using touch, vision, and sound to navigate and interact with the environment.

In short, `multimodal logic` enables reasoning across different types of data, improving decision-making and comprehension in AI systems.

### Visual grounding:

- Visual grounding is the process of connecting or linking language (words or phrases) to specific elements in an image or visual context. It allows AI models to "understand" how parts of a sentence relate to objects, regions, or elements in a picture.

##### Example:

- `Input`: A picture of a cat on a sofa and the sentence, "The cat is sleeping on the sofa."
- `Visual Grounding`: The AI identifies the cat in the image as the "cat" mentioned in the sentence and the sofa as the "sofa" in the text.

In short, `visual grounding` is how AI ties words to what they represent in a picture, enabling better comprehension of combined visual and language data.

### Spatial reasoning

- Spatial reasoning is the ability to understand, analyze, and reason about objects in space, including their positions, relationships, shapes, and movements. It’s about how things are arranged and how they interact with each other in a given area.

##### Key Concepts:

1. `Position`: Where an object is located (e.g., “The ball is to the left of the chair”).
2. `Relationships`: How objects relate to one another (e.g., “The cup is on the table”).
3. `Movement`: How objects move through space (e.g., “The car is moving toward the building”).
4. `Shapes and Sizes`: Understanding dimensions and forms (e.g., “This puzzle piece fits into that space”).

##### Examples of Spatial Reasoning:

- Solving puzzles like jigsaw puzzles or mazes.
- Understanding maps and navigating directions.
- Analyzing how objects in a room fit together or interact.

##### In AI and NLP:

In tasks like `visual question answering (VQA)` or interpreting diagrams:

- Spatial reasoning helps an AI understand questions like “Which object is closest to the door?” or “What is to the left of the square?”

## FlowVQL:

- The abstract introduces `FlowVQA`, a new tool designed to test how well AI models can answer questions about flowcharts.

- Key points:

1. `Problem`: Existing tests for visual question answering aren't good at evaluating skills like understanding visuals (like flowcharts) and reasoning about spatial or logical information.
2. `Solution`: FlowVQA provides a new, carefully created dataset of `2,272 flowchart images` and `22,413 questions` that challenge AI to solve tasks like finding information, making decisions, and following logical steps.
3. `Testing`: The researchers used both free and advanced AI models to see how well they perform with this dataset.
4. `Conclusion`: FlowVQA is a valuable tool for improving AI's ability to reason visually and logically, making future models smarter and better at understanding complex visuals like flowcharts.

In short, this research creates a new way to test and improve AI’s reasoning skills with flowcharts!

## Introduction

This part of the research paper discusses the challenges and gaps in evaluating `Vision-Language Models (VLMs)` for `Visual Question Answering (VQA)` and reasoning tasks:

1. `Focus of Existing Benchmarks`:

   - Current tests mainly check how well `pre-trained VLMs` can extract information from images.
   - They don't test the models' ability to understand `complex spatial relationships` (e.g., where objects are located in relation to each other) or `visual logical reasoning` (e.g., following a sequence of steps based on the image).

2. `Lack of Research`:

   - There's limited work on evaluating `spatial path-following` (understanding and reasoning about movement or navigation in an image) or `visual sequential reasoning` (analyzing events or steps in order).

3. `About VQA`:
   - VQA (introduced in 2017) asks models to answer questions based on images. While useful, it mainly assesses `basic spatial reasoning` and `visual information extraction` but doesn't thoroughly test more complex reasoning abilities.

- In Simple Terms: This paper highlights that current tests for Vision-Language Models focus on basic tasks like extracting image details but don't evaluate more advanced reasoning skills, such as understanding spatial relationships or following sequences in images. The researchers suggest these areas need more attention.

This section discusses `Visual Grounding (VG)` in `Visual Question Answering (VQA)` systems and highlights some common issues with current models:

1. `What is Visual Grounding (VG)?`

   - It's the ability of a model to link specific parts of an image to the question it's answering (e.g., identifying the relevant region in a picture when answering a query).

2. `Problem with Current VQA Models`:

   - Many models either rely too much on irrelevant parts of the image or ignore the visual information entirely, depending instead on pre-trained knowledge (facts already stored in the model) to answer questions.

3. `Existing Benchmarks`:

   - Current tests evaluate how models use `pre-trained knowledge` to answer questions about images, rather than testing their ability to truly understand and rely on visual information.

4. `The Goal of This Research`:
   - The researchers aim to test how well visual language models (VLMs) can answer questions by `only using visual information` in the image, without relying on any pre-existing knowledge.

- In Simple Terms:This research focuses on checking whether AI models can genuinely "look" at images to answer questions rather than relying on memorized knowledge, addressing a common weakness in VQA systems.

- This part explains that the research focuses on `flowcharts`, which are more complex than regular images because they involve:

1. `Intricate Structures`:

   - Flowcharts have a detailed and organized layout with interconnected components (e.g., boxes, arrows, paths).

2. `Path Reconstruction`:
   - Understanding flowcharts requires following the paths or steps logically to interpret the process they represent.

- In Simple Terms: The research highlights that working with flowcharts is much harder than simply analyzing images because it involves understanding their structure and tracing logical steps, not just recognizing objects.

### A crucial question:

This question asks whether `modern Vision Language Models (VLMs)` are capable of handling the unique challenges posed by `flowcharts`, specifically:

1. `Structural Understanding`:

   - Can the models comprehend the layout and connections between elements in a flowchart (e.g., boxes, arrows, paths)?

2. `Semantic Understanding`:

   - Can the models understand the meaning or purpose of the text and symbols within the flowchart (e.g., instructions, labels)?

3. `Macroscopic Context`:

   - Can the models understand the `overall purpose or big picture` of the flowchart?

4. `Granular Context`:
   - Can they also focus on the `details` within specific elements (e.g., understanding individual steps in the process)?

- In Simple Terms: The question asks if VLMs can fully interpret `both the structure and meaning` of flowcharts, while understanding the `big picture` and `small details` at the same time, given that flowcharts are visually simple yet conceptually complex.

### FlowVQA dataset

- This part describes the `FlowVQA dataset` and the findings from testing Vision Language Models (VLMs) on it:

1. **What is FlowVQA?**

   - A dataset with `2,272 flowcharts` (created using Mermaid.js and human input) sourced from workflow-related content like `Instructables`, `WikiHow`, and `code resources`.
   - It includes `22,413 question-answer (Q/A) pairs` to test different reasoning skills, such as:
     - `Information localization`: Finding specific details.
     - `Fact retrieval`: Extracting facts.
     - `Scenario deductions`: Inferring logical outcomes.
     - `Flow reasoning`: Following paths in a process.
     - `Topological understanding`: Understanding the layout/structure.

2. **How was it created?**

   - Generated through a `machine and human verification process` to ensure high quality.
   - Up to `51% of samples were discarded` if they didn’t meet standards of complexity, coherence, or challenge.

3. **What did testing reveal?**
   - VLMs (both open-source and proprietary) `struggled` with visual and spatial reasoning tasks in FlowVQA.
   - Models showed `directional bias` (favoring certain patterns) and inconsistent performance on flowcharts of different lengths.

- In Simple Terms: The researchers created a detailed dataset of flowcharts and Q/A pairs to test how well AI models can understand and reason about flowcharts. The models had a hard time performing these tasks, especially with following logic or handling different flowchart sizes and complexities. This shows the challenge of reasoning with visual and structural information.

- Here’s a simpler explanation:

1. **What is FlowVQA?**

   - A dataset with `2,272 flowcharts` and `22,413 questions and answers` about them.
   - The questions test skills like finding information, understanding steps, and following paths in the flowcharts.

2. **How was it made?**

   - The flowcharts were created by combining machine tools and human checks.
   - Half of the samples were removed to ensure only high-quality, challenging ones were included.

3. **What did the tests show?**
   - AI models (VLMs) struggled to answer the questions, especially with understanding flowcharts and reasoning about their structure.
   - They performed unevenly, especially on flowcharts of different sizes or complexities.

- In Short: The researchers made a flowchart-based test to see how well AI can understand and reason about them. The results showed that current AI models aren’t very good at it yet!

### Contribution

This part summarizes the `main contributions` of the research:

1. **New VQA Focus**:

   - They introduced `Visual Question Answering (VQA)` specifically for `flowcharts`, emphasizing skills like `visual logic` (understanding flow) and `spatial reasoning` (analyzing structure).
   - This fills a gap in previous AI benchmarks.

2. **Framework Creation**:

   - They developed a method to create challenging and accurate `questions and answers` based on flowcharts, starting from text descriptions and verifying quality thoroughly.

3. **FlowVQA Dataset**:

   - A new dataset with `2,272 flowcharts` and `22,413 Q/A pairs` covering four types of questions, created using the above framework.

4. **Model Testing**:
   - They tested both `open-source` and `closed-source` `Vision Language Models (VLMs)` using different techniques to guide and improve their answers.
   - They found issues like `bias` (favoring certain patterns) and uneven performance on flowcharts of varying sizes.

- In Simple Terms: The researchers built a new flowchart-based test (FlowVQA), created challenging questions for it, and analyzed how AI models handle flowcharts. They found that current AI struggles with flowchart reasoning and structure.

## Details of the construction of FlowVQA

This section explains how the `FlowVQA dataset` was created, focusing on the sources of data and the steps involved:

![fig:2](/image/FlowVQA2.PNG)

This image explains the `two-step process` used to create high-quality flowcharts for the FlowVQA dataset. Here's what it shows:

##### Step 1: Generating Structured Summaries

1. **Input Data**:
   - Texts from `WikiHow`, `Instructables`, and `FloCo` are used as raw material.
2. **Structured Summaries**:
   - A `GPT model` (like ChatGPT) processes the input data to create `structured step-by-step instructions` with control codes (e.g., decisions, actions).
   - These summaries break down complex tasks into a normalized flow for easier conversion into flowcharts.
     **Example**:
   - The process of "Becoming a VFX Artist" is broken into clear steps, including decisions like "Can you fully join the VES?"

##### Step 2: Generating Flowcharts

1. **Mermaid Live Script**:

   - Another `GPT model` is prompted to convert the structured summaries into `Mermaid.js syntax`, which is used for creating flowcharts.
   - Mermaid.js provides a way to visually represent the steps and decisions from the summaries.

2. **Mermaid Compiler**:
   - The `Mermaid.js script` is then compiled into a high-resolution `flowchart image`.
   - This step ensures that the generated flowcharts are both visually clear and logically accurate.

- **Quality Control**:

- A `cross-verification mechanism` is used to check the correctness of both the summaries and flowcharts.

- **In Simple Terms**:

1. They take instructional content (e.g., from WikiHow or FloCo) and break it into step-by-step instructions using GPT.
2. These instructions are turned into flowchart diagrams using a tool called Mermaid.js.
3. Finally, everything is checked to ensure it’s accurate and easy to understand.

![fig:3](/image/FlowVQA3.PNG)

This table summarizes the `resources used in the FlowVQA dataset` for generating flowcharts and their corresponding Mermaid.js scripts.

##### **Understanding the Table**

1. **Columns (WikiHow, Instructables, FloCo)**:

   - These are the `sources` from which the input data is collected:
     - `WikiHow`: Step-by-step guides for everyday tasks.
     - `Instructables`: DIY blogs for creative projects.
     - `FloCo`: Flowchart-to-code dataset with coding-related examples.

2. **Rows**:

   - `Source Texts`:

     - The number of original text documents (e.g., WikiHow articles, Instructables blogs, FloCo code snippets) used as raw material for generating flowcharts.
     - Example: 1,914 articles from WikiHow were processed.

   - `Mermaid.js Scripts`:
     - The number of scripts generated from the source texts using Mermaid.js (a tool for creating diagrams from text).
     - Example: 1,500 flowcharts were generated from WikiHow articles.

- **What is Happening Here?**

1. **Why Source Texts?**

   - The texts (like step-by-step instructions or code snippets) are the `foundation` for creating flowcharts.
   - These texts provide the `content` (steps, decisions, and processes) that can be visualized in a flowchart.

2. **What are Mermaid.js Scripts?**
   - Mermaid.js is a tool that uses simple `text-based scripts` to create flowcharts and diagrams.
   - The scripts define the structure of the flowchart, like the steps, connections, and decisions.
   - These scripts are then compiled to produce `visual flowcharts`.

- **Why This Process Is Needed?**

- `Source texts` are necessary because they contain the `raw instructions or processes` that need to be visualized.
- `Mermaid.js scripts` are used to convert these texts into `flowchart diagrams`, which can be used to create the `FlowVQA benchmark` for training and evaluating AI models.
- This ensures a structured and visual representation of complex processes, making it easier to assess the AI's ability to understand and reason about flowcharts.

#### 2.1 Flowchart Sources

This section explains how the **FlowVQA dataset** was constructed and the sources used:

1. **Data Sources**:

   - Text data was collected from three main places:
     - `WikiHow articles`: Step-by-step guides for everyday tasks.
     - `Instructables DIY blogs`: Instructions for making or building things.
     - `FloCo code snippets`: Simple examples connecting flowcharts to code.

2. **Categorization**:

   - WikiHow and Instructables were grouped by topic (e.g., cooking, crafting), while FloCo was placed in a "code" category.

3. **Quality Assurance**:

   - High-quality FloCo snippets were `manually selected` to ensure consistent standards across all data sources.
   - Generated flowcharts from FloCo were compared with the original samples to fine-tune the prompts and ensure accuracy.

4. **Final Dataset**:
   - The team sampled `1,268 WikiHow articles`, `789 Instructables blogs`, and `475 FloCo examples`.
   - All samples went through a `human verification process` to ensure their quality and usability.

- In Simple Terms: The dataset was built by collecting step-by-step instructions from WikiHow, Instructables, and FloCo, organizing them by category, and carefully verifying the generated flowcharts to ensure they were accurate and useful.

**17 Nov, 24**

![fig:4](/image/FlowVQA4.PNG)

This image shows a table with statistics about a dataset used for "FlowVQA," which appears to involve questions
related to flowcharts. Here’s an explanation of each column and row in the table:

##### Columns:

- **Source**: Refers to the origin of the flowcharts. The sources listed here are WikiHow, Instructables, and Code.
- **# Samples**: Indicates the number of flowchart samples present from each source.
- **Avg. NPF (Nodes Per Flowchart)**: The average number of nodes (or steps) in each flowchart for a given source.
- **Avg. EPF (Edges Per Flowchart)**: The average number of edges (connections) between nodes per flowchart.
- **Avg. Width (Pixels)**: The average width of the flowchart images in pixels.
- **Avg. Height (Pixels)**: The average height of the flowchart images in pixels.
- **Ratio**: The aspect ratio of the flowcharts, represented as width to height.
- **# Qs.**: The number of questions generated or available related to the flowcharts.

##### Rows:

- **WikiHow**: This row provides statistics about the flowcharts sourced from WikiHow. For example, there are 1,121 flowchart samples, with an average of 21.83 nodes per flowchart and an aspect ratio of 1:3.54.
- **Instructables**: This row represents data from flowcharts sourced from Instructables, with 701 samples and a slightly higher aspect ratio of 1:4.23.
- **Code**: Represents flowcharts derived from code-related sources, with 450 samples and a smaller average number of nodes and edges compared to other sources.
- **Full**: Provides overall averages and totals for the entire FlowVQA dataset, summing up all sources.

**19 Nov, 24**

**22 Nov, 24**

#### 2.2 Flowchart Generation

![fig:3](/image/FlowVQA3.PNG)

- **Overview:**
  The goal is to turn any process description (from articles, books, or other documents) into a visual flowchart. Since real-world flowchart examples are rare and inconsistent, they built their own method to create these flowcharts systematically. This process has **two main steps**.

- **Step-by-Step Summary:**

1. **The Challenge:**

   - Real-world flowcharts from books or documents aren't widely available or standardized.
   - They needed a better dataset to make flowchart creation reliable and detailed.

2. **The Approach:**

   - They break the process into **two steps**:
     - **Step 1:** Use a tool like GPT-4 to summarize the source text into a **pseudo-code format** (a structured way to describe the flow).
     - **Step 2:** Convert the pseudo-code into a **Mermaid.js script** (a coding language for creating flowcharts).

3. **How it Works:**

   - Templates and special control tags are added to guide GPT-4 in both steps.
     (Templates and special control tags are **structured guidelines** or **instructions** provided to GPT-4 to help it produce consistent and accurate outputs during the two steps of the process.
     `Template`:Pre-defined formats or examples that show GPT-4 how the output should look.
     `Why are they used?`: To ensure that GPT-4 produces outputs in a consistent format.
     `Control Tags`: Special keywords, symbols, or markers added to the prompts)

   - Mermaid.js scripts are compiled into high-quality flowchart images (PNG format).

4. **Exclusions:**

   - They remove scripts that have minor syntax or rendering errors. (It means that during the process, if any scripts have minor issues—such as coding errors (syntax) or problems in how the flowchart looks (rendering)—those scripts are excluded. This ensures that only properly formatted and visually correct flowcharts are included in the final dataset.)

5. **Dataset:**
   - The final dataset contains flowcharts generated using this method, with Table 1 and Figure 2 showing statistics and the pipeline for this process.
   - Detailed prompts for each step are listed in the appendix.

![fig:2](/image/FlowVQA2.PNG)

#### 2.3 Question Answer Creation

- **Overview:**
  They created four types of questions to test how well a model understands flowcharts. These questions focus on finding facts, solving problems, understanding decisions, and analyzing flowchart structure.
  **Question Types with Examples:**

1. **T1: Fact Retrieval**

   - **What it does:**  
     Simple questions that ask for specific information directly from the flowchart.
   - **Example:**  
     _“What is the first step in the process?”_  
     If the flowchart is about troubleshooting a computer issue, the answer could be:  
     _“Check if the computer is powered on.”_

2. **T2: Applied Scenario**

   - **What it does:**  
     Questions that use a real-world situation and ask for reasoning based on the flowchart.
   - **Example:**  
     _“If a user encounters a slow internet connection, what steps should they follow to fix it?”_  
     The answer could involve reasoning, like:  
     _“Check if the modem is on. If yes, restart it. If the issue persists, contact the service provider.”_

3. **T3: Flow Referential**

   - **What it does:**  
     Questions about specific parts of the flowchart and how decisions affect the flow.
   - **Example:**  
     _“If the condition ‘Password Incorrect’ is true, what happens next?”_  
     The answer might describe the next decision or path:  
     _“The user is prompted to reset their password or try again.”_

4. **T4: Topological**
   - **What it does:**  
     Questions about the overall structure or connections in the flowchart.
   - **Example:**  
     _“How many decision points are in the flowchart?”_  
     If the flowchart has three decision nodes, the answer could be:  
     _“Three decision points: Login Check, Payment Confirmation, and Error Handling.”_

- **How Questions Are Made:**
  - **T1–T3:** GPT-4 is used to create these questions and generate three versions of each answer for flexibility.
  - **T4:** The flowchart is converted into a graph (using a matrix) to create structural questions with template-based answers.

![fig:5](/image/FlowVQA5.PNG)

#### 2.4 Human Verification Pipeline and Platform:

![fig:6](/image/FlowVQA6.PNG)

- **Summary:** To ensure high-quality flowcharts and question-answer pairs, the authors set up a **human verification process** involving expert reviewers and a custom-built platform. Here's a simplified breakdown:

- **Verification Process:**

1. **Team of Experts:**

   - Five expert reviewers check all flowcharts and Q/A pairs for quality, logic, and alignment with context.
   - They use strict rules to ensure thorough reviews.

2. **Annotation Platform:**

   - A custom tool is used where flowcharts and Q/A pairs can be viewed side-by-side.
   - Reviewers give scores for individual components and an overall quality score.
   - Any flowcharts or Q/A pairs below the quality threshold are removed.

3. **Exclusions:**

   - Topological questions are not reviewed on the platform since they are automatically generated with a fixed template.

4. **Supervision:**

   - Two supervisors double-check the reviewers’ work to ensure consistency and fairness.

5. **Timeline:**

   - The entire verification process takes 10 days.

6. **Final Dataset:**
   - Only high-quality flowcharts and Q/A pairs that meet the standards are included in the final dataset.

![fig:7](/image/FlowVQA7.PNG)

This table shows the number of flowchart samples and Q/A types (T1, T2, T3) before and after the verification process. Here's the breakdown:

1. **Flowchart Samples:**

   - Before: 2,532
   - After: 2,272
   - **10.3% were removed** during verification.

2. **T1 (Fact Retrieval Questions):**
   - Before: 8,932
   - After: 4,532
   - **49.3% were removed.**
     etc.

- **Key Insight:**  
  A significant portion of the data was filtered out, especially for Q/A pairs, to ensure only high-quality samples made it into the final dataset.

**23 Nov, 24**

### Experimental Evaluation

- **Summary of the Research Questions:** The experiments aim to test and improve how well `visual language models (VLMs)` handle flowchart-based tasks. Here’s a simplified breakdown of the questions:

1. **RQ1:**

   - Are current models (VLMs) good at analyzing flowcharts, or do they struggle with the challenges in this dataset?
   - Can this dataset help improve these models in the future?

2. **RQ2:**

   - Does the model's performance depend on:  
     a) Where the flowchart comes from,  
     b) The type of question (e.g., fact-based, reasoning),  
     c) How complex the flowchart is?

3. **RQ3:**

   - Can we improve model performance on flowchart-related tasks using special instructions or training techniques?
   - Does fine-tuning VLMs with the `FlowVQA dataset` make them better at answering flowchart-related questions?

4. **RQ4:**
   - Do current VLMs show any bias in the way they analyze flowcharts (e.g., favoring certain directions or paths)?

- **Simplified Explanation:**

This section highlights the challenges smaller models face and evaluates how well different models perform on `FlowVQA`, a dataset that requires visual reasoning with complex flowcharts.

- **Key Points:**

1. **Challenges for Smaller Models:**

   - **Flowchart complexity:** High-resolution and visually complex flowcharts make it hard for smaller models to perform well.
   - **Poor results:** Widely used open-source models like **LLaVA**, **OpenFlamingo**, and others perform very poorly on FlowVQA (less than 10% accuracy).
   - **Reasons for failure:**
     - **Small vision encoders:** These models distort flowchart images, especially with high aspect ratios.
     - **Weak reasoning abilities:** Even if the model interprets the image, it struggles with logical and reasoning tasks.

2. **Models Used for Comparison:**
   - **Proprietary (closed-source) models:**
     - **GPT-4V:** Known for its strong multimodal understanding.
     - **Gemini Pro:** Another advanced proprietary model for visual understanding.
   - **Open-source models:**
     - **CogAgent-VQA:** A specialized 18-billion-parameter model fine-tuned for visual question answering (VQA) tasks, capable of handling high-resolution inputs (1120x1120).
     - **InternLM-X-Composer2:** Uses a novel **PLORA** method to improve vision processing while preserving text reasoning abilities.
     - **QwenVL-Chat:** Features a position-aware adapter that captures long image contexts effectively, even after resizing the flowcharts.

- **Key Idea:**
  - Smaller models struggle with FlowVQA due to their limited vision encoding and reasoning abilities.
  - Advanced proprietary and specialized open-source models are evaluated to see if they can handle the dataset’s complexity better.

![fig: 8](/image/FlowVQA8.PNG)

This table provides information about **open baseline models** (visual language models or VLMs) used for evaluation in the study. It lists three open-source models and describes their components and input capabilities.

- **Explanation of Columns:**

  1.  **Open Model:**

      - The names of the models evaluated:
      - **CogAgent-VQA**
      - **InternLM-X-Composer2**
      - **Qwen-VL-Chat**

  2.  **LM (Language Model):**

      - The language model component used for text understanding in each VLM:
      - **CogAgent-VQA:** Vicuna-7B
      - **InternLM-X-Composer2:** Intern-LM2-7B
      - **Qwen-VL-Chat:** Qwen-VL-7B

  3.  **VM (Vision Model):**

      - The vision model component that processes image inputs:
      - **CogAgent-VQA:** ViT-4.4B (a large vision transformer)
      - **InternLM-X-Composer2:** ViT-304M (a smaller vision transformer)
      - **Qwen-VL-Chat:** ViT-1.9B (medium-sized vision transformer)

  4.  **Norm. Res. (Normalized Resolution):**
      - The resolution of input images normalized for the vision model:
      - **CogAgent-VQA:** 1120x1120 (can handle large, high-resolution images).
      - **InternLM-X-Composer2:** 490x490 (medium resolution).
      - **Qwen-VL-Chat:** 448x448 (lower resolution compared to others).

- **Key Insights:**

- **CogAgent-VQA** handles the highest image resolution, making it better suited for tasks requiring high-detail image processing.
- The **language models (LM)** and **vision models (VM)** vary in size and capacity, influencing their performance in multimodal tasks.
- Normalized resolution indicates the size of images these models are optimized to process effectively.

### **1. LLaVA (Liu et al., 2023b):**

- **What it does:** A model for multimodal tasks, but struggles with high-resolution flowchart images.
- **Limitation:** Distorts images due to small vision encoder and lacks reasoning ability.

---

### **2. OpenFlamingo (Awadalla et al., 2023):**

- **What it does:** An open-source multimodal model, not specialized for flowcharts.
- **Limitation:** Performs poorly on complex visual reasoning tasks like FlowVQA.

---

### **3. BLiPv2 (Li et al., 2023a):**

- **What it does:** Another general-purpose model for multimodal tasks.
- **Limitation:** Has trouble analyzing high-aspect-ratio flowcharts.

---

### **4. mPLUG-OWL (Ye et al., 2023b):**

- **What it does:** A vision-language model that focuses on text-image tasks.
- **Limitation:** Struggles with flowcharts due to weak reasoning capabilities.

---

### **5. Sphinx (Lin et al., 2023):**

- **What it does:** An advanced model, but not optimized for flowchart reasoning.
- **Limitation:** Limited understanding of complex flowchart data.

---

### **6. GPT-4V (OpenAI, 2023):**

- **What it does:** A proprietary model known for strong multimodal abilities.
- **Strength:** Can handle complex flowchart reasoning better than open-source models.

---

### **7. Gemini Pro (Anil et al., 2023):**

- **What it does:** Another closed-source model with advanced visual understanding.
- **Strength:** Designed for high-level visual question-answering tasks.

---

### **8. CogAgent-VQA (Hong et al., 2023):**

- **What it does:** A specialized open-source model for visual tasks, tuned for GUI and VQA.
- **Strength:** Handles high-resolution inputs (1120x1120) well, useful for flowcharts.

---

### **9. InternLM-X-Composer2 (Dong et al., 2024):**

- **What it does:** Uses a novel method (**PLORA**) to focus on image tokens while maintaining text reasoning skills.
- **Strength:** Balances vision and language understanding effectively.

---

### **10. QwenVL-Chat (Bai et al., 2023):**

- **What it does:** An instruction-tuned model with a **position-aware adapter**.
- **Strength:** Captures long image contexts even when flowcharts are resized.

## what is Baseline Evaluation?

- Baseline evaluation is the process of establishing a starting point or reference performance for a system, model, or dataset. It helps measure how well a system performs against basic standards or simpler models before introducing more advanced methods or improvements.

1. **Purpose:**

   - To set a benchmark for comparison.
   - It shows whether new techniques or models improve performance beyond the simplest approaches.

2. **How it’s done:**

   - A straightforward or standard model (e.g., a simple algorithm or existing method) is applied to the task or dataset.
   - The results of this baseline model are recorded and used for comparison with other, more sophisticated methods.

3. **In Research:**
   - Baseline evaluations are critical for proving the effectiveness of new ideas, techniques, or models.

- **Example:**  
  If you’re testing a new visual question answering model, the baseline might be a simple model that performs basic matching between text and image without deeper reasoning. Comparing your advanced model to the baseline shows how much better your approach is.

#### 3.1 Baseline Evaluation

- This section describes `four methods` used to test how well models (VLMs) can answer flowchart-based questions:

  1.  **Zero-Shot:**

      - The model answers questions directly without prior training, using only a small instruction to guide it.

  2.  **Zero-Shot CoT (Chain of Thought):**

      - The model explains its reasoning step-by-step (rationale) before giving the final answer.

  3.  **Text-Only Few-Shot CoT with Reasoning Directives:**

      - The model is given several examples (few-shot learning) that include:
      - The question.
      - Guidance on reasoning steps (Directional Stimulus Tags).
      - A step-by-step explanation (rationale).
      - The final answer.
      - This approach helps the model break down complex questions logically.

  4.  **Fine-Tuning:**
      - The model is trained (fine-tuned) on a specific dataset (FlowVQA) and then tested to see if this improves performance.

These methods aim to analyze how well models handle flowchart questions and improve their reasoning capabilities.

## Here's a simple explanation of `Zero-Shot`, `Zero-Shot CoT`, and related methods:

---

##### 1. Zero-Shot:

- **What it is:**  
  The model is tested directly on a new task without being trained or shown any examples beforehand.
- **Analogy:**  
  Imagine being asked to solve a puzzle you've never seen before, relying only on your general knowledge.
- **Example:**  
  A model sees a flowchart and is simply asked, "What happens if Step A fails?" It must answer directly without prior task-specific training.

---

#### 2. Zero-Shot CoT (Chain of Thought):

- **What it is:**  
  Similar to Zero-Shot, but the model is asked to first explain its reasoning step-by-step before providing the answer.
- **Why it helps:**  
  Explaining the process often improves accuracy by forcing the model to think through the question logically.
- **Analogy:**  
  Instead of just solving a puzzle, you narrate how you're solving it step-by-step before giving the answer.
- **Example:**  
  The model is asked, "What happens if Step A fails?" It explains why Step B would be affected before concluding with the answer.

---

#### 3. Few-Shot Learning:

- **What it is:**  
  The model is shown a few examples of similar tasks/questions with their correct answers before being tested on new questions.
- **Why it helps:**  
  Seeing examples helps the model understand the task better.
- **Analogy:**  
  Imagine being shown how to solve a few puzzles before solving a new one.
- **Example:**  
  The model sees 2-3 questions about a flowchart, each with explanations and answers, before being asked a new question.

---

#### 4. Few-Shot CoT (Chain of Thought):

- **What it is:**  
  Combines Few-Shot Learning and CoT reasoning. The model is shown examples where reasoning is broken down step-by-step, helping it learn to explain its own reasoning.
- **Why it works:**  
  Teaching logical thinking via examples improves performance.
- **Example:**  
  A model is shown examples like:
  - **Question:** What happens if Step X fails?
  - **Explanation:** Step Y depends on X, so if X fails, Y won’t execute.
  - **Answer:** Y won’t execute.  
    Afterward, it applies this process to new questions.

---

#### 5. Fine-Tuning:

- **What it is:**  
  The model is trained on a large dataset tailored to the task (like FlowVQA for flowcharts) to improve its understanding and performance.
- **Analogy:**  
  Imagine practicing solving puzzles of the exact same type before being tested.
- **Example:**  
  The model is trained on many flowchart questions with answers and then tested on similar questions.

---

#### **Key Difference:**

- **Zero-Shot:** No prior examples or training for the task.
- **Few-Shot:** A few examples are given to guide the model.
- **CoT:** Focuses on explaining reasoning step-by-step before answering.
- **Fine-Tuning:** Trains the model deeply on the task with a large dataset.

#### 3.2 Evaluation Method

Here’s a simplified explanation of the evaluation method described:

1. **AI Models as Evaluators:**

   - They use three AI models (**GPT-3.5**, **Llama-2 70B**, and **Mixtral 8x7B**) to evaluate answers generated by other models.
   - These evaluators compare the answers to three correct "gold standard" answers without considering additional context.

2. **Evaluation Process:**

   - The evaluator models analyze the responses step-by-step (using **Chain of Thought reasoning**) to decide if the answers are correct or incorrect.
   - This is treated like checking if two short texts are similar, but with smarter reasoning instead of just matching words.

3. **Final Judgment:**

   - The final decision on correctness is made by a majority vote among the three evaluator models.

4. **Fine-Tuning:**
   - They fine-tune the Qwen-VL-chat model using a method called **LORA** on high-performance GPUs.
   - Fine-tuning is carefully done to preserve the original model's knowledge while improving it for the specific task.

In short: Evaluator models verify the correctness of generated answers by reasoning, and fine-tuning improves model performance without erasing its existing abilities.

#### 3.4 Baseline Results and discussion

![fig: 9](/image/FlowVQA9.PNG)

Here’s a simple summary of the section:

1. **Challenges in FlowVQA:**

   - FlowVQA is a tough dataset, and all tested models show room for improvement.
   - The best result is **68.42% accuracy** using GPT-4 with a "few-shot directive-based" approach.

2. **Few-Shot Directives Work Well:**

   - Using reasoning examples (few-shot directives) improves performance for most models:
     - **+7% improvement** for GPT-4.
     - **+12% improvement** for Gemini-Pro.
   - **CogAgent-VQA** doesn’t improve because it struggles to generate reasoning directives.

3. **Proprietary Models Perform Better:**

   - Proprietary models (like GPT-4) perform much better than open-source ones (like Qwen-VL-chat).
   - GPT-4 is **30% better** than Qwen-VL-chat with few-shot directives.

4. **Fine-Tuning Helps:**

   - Fine-tuning Qwen-VL-chat improves its performance:
     - **+3% for Zero-Shot prompting.**
     - **+11% for Zero-Shot CoT prompting.**
   - Complex question types (T2, T3, T4) improve more with fine-tuning than simple fact retrieval (T1).

5. **Question Type Performance:**

   - Models do better on simpler questions (T1: fact retrieval, T2: applied scenarios).
   - Performance drops for harder questions (T3: flow-referential, T4: topological reasoning).

![fig: 10](/image/FlowVQA10.PNG)

6. **Complex Flowcharts Are Harder:**
   - Flowcharts with more nodes (complex structure) lead to worse model performance.
   - More nodes = more visual information = harder reasoning.

In short: **Few-shot prompting** and **fine-tuning** improve model performance, but FlowVQA remains challenging, especially for complex flowcharts and reasoning-heavy questions.

#### 3.4 Directional Bias

![fig: 11](/image/FlowVQA11.PNG)

Here’s a simplified summary of the section:

1. **What is Directional Bias?**

   - Researchers tested whether models are biased toward the standard top-to-bottom layout of flowcharts.
   - To check this, they flipped 1,500 flowcharts upside down ("Bottom-Top"), where the start is at the bottom and the end is at the top.

2. **Findings:**

   - Even top-performing models (like GPT-4) struggled with these inverted flowcharts.
   - GPT-4's accuracy dropped by **15%**, showing that models rely on the typical flowchart direction for reasoning.

3. **Reason for Bias:**

   - Models' training data lacks diverse layouts, leading to over-reliance on standard flowchart structures.
   - They fail to fully "understand" the image context, causing performance drops when layouts change.

4. **Future Improvements:**
   - Adding diverse and flipped examples during training could help reduce this bias.

**In short:** Models have a "directional bias," meaning they rely on the usual flowchart layout (top-to-bottom) and perform poorly when this layout is reversed.

#### 4. Related Work

Here’s a simplified summary of the section:

1. **Progress in Vision-Language Models (VLMs):**

   - Recent benchmarks test how well VLMs combine visual and textual information for tasks like answering questions about documents (TextVQA, DocVQA), charts (ChartQA, InfographicQA), or solving math problems with visuals (MathVista).

2. **Problems with Previous Flowchart QA Research:**

   - Earlier work on flowchart-based questions had significant issues, such as:
     - Using fake flowcharts with random content.
     - Focusing only on simple structural questions.
     - Relying on basic multiple-choice answers, which don't test deep reasoning.
   - Other studies focused on tasks like recognizing flowchart objects or converting them to code, but these often had poor-quality data or limited usefulness.

3. **What Makes This Work Different:**
   - The authors created a **new benchmark** for flowchart QA with complex, realistic flowcharts and diverse question types.
   - Their dataset is designed to push VLMs to perform both **visual reasoning** and **textual understanding** effectively.

**In short:** This study improves on earlier work by introducing a robust, practical benchmark that tests VLMs on realistic, complex flowcharts with varied and challenging questions.

#### 5. Conclusion and Future Work

Here’s a simple summary of the **Conclusion and Future Work** section:

- **Conclusion:**

  - The study evaluates how well current multimodal models (VLMs) handle **FlowVQA**, a challenging dataset with 2,272 flowchart images and 22,413 Q/A pairs.
  - Models struggle with reasoning on complex flowcharts, showing weaknesses in architecture, prompting strategies, and visual grounding.
  - Testing with inverted flowcharts revealed **directional bias**, as models performed worse when flowcharts were flipped, showing a lack of true understanding.

- **Future Work:**

  1.  **Improving Flowchart Reasoning:**
      - Build VLMs specifically for flowcharts and enhance reasoning abilities.
  2.  **Graph-Based Models:**
      - Use the graph structure of flowcharts to improve model architecture and reasoning.
  3.  **Adversarial Probes:**
      - Test models with trickier questions (e.g., misleading or noisy flowcharts) to make them more robust.
  4.  **Multiple Tasks:**
      - Use FlowVQA for other tasks like generating code (Mermaid.js) from flowcharts or vice versa.
  5.  **NeuroSymbolic AI:**
      - Combine neural and symbolic reasoning methods to handle flowcharts more effectively.

- **Limitations:**

  - Not all models were fine-tuned due to limited resources, so the results may not fully reflect their potential.
  - The focus on English limits the dataset’s diversity and global applicability.
  - As this is a new problem area, further research is needed for deeper insights.

**In short:** Current models struggle with flowcharts due to their complexity, but FlowVQA opens many opportunities for improving reasoning, graph-based approaches, and multi-task training. Future work can address resource constraints and expand the dataset's linguistic diversity.
