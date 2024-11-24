**2 Nov, 24**

# ChartAssistant: A Universal Chart Multimodal Language Model via Chart-to-Table Pre-training and Multitask Instruction Tuning

**GitHub Repository**: [ChartAssistant Code and Data](https://github.com/OpenGVLab/ChartAst)

# Abstract

- Charts elements consist of graphical elements (e.g., bars, lines) and textual components (e.g., labels, legends).
- Chart elements are challenging for general-purpose multimodal models.
- Vision-language models trained on charts struggle with generalization.
- **ChartAssistant** is a chart-based vision-language model.
- **ChartSFT**: A comprehensive dataset covering diverse chart-related tasks with basic (e.g., bars and pies) and specialized (e.g., radars, bubbles) chart types. It undergoes a two-stage training process:

  - **Pre-training** on chart-to-table parsing to align chart and text.
  - **Multitask instruction-following fine-tuning**.

- ChartAssistant achieves significant performance gains over the state-of-the-art UniChart and Chartllama methods.

![My Image](/image/chartAssistant1.png)

In simple terms, the image compares two approaches to using AI for understanding charts and tables. Here’s an easy breakdown of what each approach does and what key terms mean:

**Previous Work (Part a in the image):**
Multitask Instruction Tuning: This is a process where a model is trained to handle multiple tasks (e.g., answering questions about visual data or solving math problems) by giving it specific instructions for each task. The model learns to follow instructions in both text and image formats, making it flexible across various tasks.

**Task-specific Fine-tuning:**

- After the initial training, the model is further refined for each specific task, like "Visual Question Answering" (Visual QA) or "Math Question Answering" (Math QA). This fine-tuning focuses on making the model better at individual tasks.

- In the previous approach, the model is trained and fine-tuned separately for each task. This makes it work well for specific applications but requires extra training steps for each new task.

**ChartAssistant (Part b in the image):**

- Alignment Pre-training: Before jumping into multitasking, ChartAssistant first "aligns" the data by converting charts into structured text or tables. This pre-training helps the model understand the chart’s information in a form it can easily work with, making it better at understanding relationships within the data.

- Multitask Instruction Tuning: Just like the previous model, ChartAssistant learns to handle various tasks with instructions, but since it already "understands" the chart data better, it can handle these tasks more effectively.

In summary, **ChartAssistant** is designed to be more efficient and accurate by first learning how to read charts as tables. Then, it uses this understanding to tackle multiple tasks without needing as much specific fine-tuning for each one. This approach makes it versatile for tasks like visual and math question answering.

**Key Takeaways:**

- Multitask Instruction Tuning: Teaching a model to follow different types of instructions for multiple tasks.
- Alignment Pre-training: A step where the model learns to interpret chart data by converting it into text or tables first.
- Fine-tuning: Additional training focused on improving the model's performance for specific tasks.

In essence, **ChartAssistant** takes an extra initial step (alignment pre-training) to get a deeper understanding of charts, making it more effective in handling a range of tasks compared to previous methods.

# Introduction

- Comparison of Approaches

The image compares two approaches to using AI for understanding charts and tables:

### Previous Work (Part a in the image)

- **Multitask Instruction Tuning**: This process trains a model to handle multiple tasks (e.g., answering questions about visual data or solving math problems) by giving it specific instructions for each task. The model learns to follow instructions in both text and image formats, making it flexible across various tasks.
- **Task-specific Fine-tuning**: After initial training, the model is further refined for each specific task, like "Visual Question Answering" (Visual QA) or "Math Question Answering" (Math QA). This fine-tuning improves the model's performance for individual tasks.

In the previous approach, the model is trained and fine-tuned separately for each task. This works well for specific applications but requires extra training steps for each new task.

### ChartAssistant (Part b in the image)

- **Alignment Pre-training**: Before multitasking, ChartAssistant "aligns" data by converting charts into structured text or tables. This pre-training helps the model understand chart information better, making it more effective in recognizing relationships within the data.
- **Multitask Instruction Tuning**: Similar to previous models, ChartAssistant learns to handle various tasks with instructions. However, since it already understands chart data better, it can handle these tasks more effectively.

**Summary**: ChartAssistant is designed to be more efficient and accurate by first learning to read charts as tables. Then, it uses this understanding to tackle multiple tasks without needing as much specific fine-tuning for each one, making it versatile for tasks like visual and math question answering.

### Key Takeaways

- **Multitask Instruction Tuning**: Teaches a model to follow different types of instructions for multiple tasks.
- **Alignment Pre-training**: A step where the model interprets chart data by converting it into text or tables first.
- **Fine-tuning**: Additional training focused on improving the model's performance for specific tasks.

In essence, **ChartAssistant** takes an extra initial step (alignment pre-training) to achieve a deeper understanding of charts, making it more effective in handling a range of tasks compared to previous methods.

### Why Chart Comprehension is Challenging

Chart comprehension is challenging due to:

- **Intricate Visual Marks**: Complicated elements like lines, bars, and symbols.
- **Implicit Numerical Information**: Numerical data that needs to be inferred.
- **Complex Spatial Relationships**: The positioning of elements (e.g., axes and labels) requires spatial reasoning and numerical understanding.

Interpreting charts requires specialized knowledge, spatial reasoning, and numerical understanding.

### Models:

- **LLaVA**: General-purpose multimodal model trained on natural images, which struggles with chart-related tasks due to specific complexities and relationships unique to charts.
- **MatCha, UniChart**: These models undergo multitask instructional tuning and task-specific fine-tuning, exhibiting good performance on several downstream tasks.

#### A simplified overview of the `MatCha` and `UniChart` models, highlighting their `main strengths (pros)`, `weaknesses (cons)`, and characteristics.

### MatCha

**Characteristics**:

- **Multitask Instructional Tuning**: Trained to perform well across multiple chart-related tasks by learning from different instruction-based inputs.
- **Chart-Text Alignment Focus**: Emphasizes the importance of aligning charts with their associated textual information to improve understanding.

**Pros**:

- **Good at Multitask Performance**: It performs reasonably well on various tasks related to visual question answering, chart reading, and analysis.

**Cons**:

- **Limited Task Coverage**: MatCha does not cover a wide enough range of chart types or tasks, limiting its effectiveness across different kinds of charts.
- **Poor Generalization**: Due to a lack of diverse training data, it struggles to generalize beyond the specific tasks it’s trained on.
- **Need for Fine-Tuning**: It still requires additional task-specific fine-tuning to perform well on new or complex tasks.

### UniChart

**Characteristics**:

- **Multitask Instructional Tuning and Fine-Tuning**: Like MatCha, it’s also trained to handle various chart-related tasks with instructional tuning, followed by fine-tuning to improve specific skills.

**Pros**:

- **Good Task Performance**: UniChart performs well on several downstream tasks, similar to MatCha, due to its multitask tuning approach.

**Cons**:

- **Lacks Chart-Text Alignment**: UniChart does not effectively align the chart elements with structured textual data, which limits its ability to understand complex relationships within charts.
- **Limited Data Annotations**: It lacks annotated data on specialized charts (like box plots) and image-text relationships, making it weaker in areas involving visual comprehension and mathematical reasoning.
- **Requires Fine-Tuning**: Like MatCha, it also needs specific fine-tuning for new tasks to perform effectively, which impacts flexibility.

### Summary of `MatCha` and `UniChart`:

Both **MatCha** and **UniChart** models are well-tuned for various chart-related tasks but have notable limitations:

- **Pros**: They perform well on multiple tasks with multitask instructional tuning and task-specific fine-tuning.
- **Cons**: They lack comprehensive chart-text alignment, have limited data coverage for specialized charts, and rely heavily on fine-tuning, which affects their generalization abilities.

### ChartAssistant

- A new multimodal model --> improve generalization
- `ChartAssistant` is trained on a large-scale chart-specific
  instruction-tuning benchmark dubbed `ChartSFT`

**12 Nov, 24**

- ChartAssistant --> two variant --> `ChartAst-D` and `ChartAst-S`
- **ChartAst-D** --> built upon Donut --> a vision-language model --> for visual
  document understanding.
- **ChartAst-S** --> built upon SPHINX --> a vision-language model --> for universal multimodal comprehension

**ChartAst-D**:

- **Built on Donut**: Donut is a vision-language model, meaning it can process both visual (images) and textual information. It's relatively small, with 260 million parameters (a parameter is a part of the model that learns from data).
- **Purpose**: Donut is used here for tasks related to visual document understanding, like recognizing and analyzing text and structure in documents.
- **Pros**: Lightweight, so it’s faster and uses less memory.
- **Cons**: May not be as powerful for complex tasks compared to larger models.

**ChartAst-S**:

- **Built on SPHINX**: SPHINX is a much larger (13 billion parameters) vision-language model, designed for complex multimodal tasks (processing both images and text with high accuracy).
- **Dynamic Resolution Processing**: This allows the model to adjust to different image qualities, which improves its ability to understand various charts.
- **Mixed Visual Encoders**: Different "encoders" help the model interpret diverse aspects of visual data, enhancing its adaptability to different types of charts.
- **Pros**: Greater robustness and usability; performs well across various chart-related tasks.
- **Cons**: Larger model, so it may require more computing power and memory.

In essence, **ChartAst-D** is lighter and faster, good for straightforward tasks, while **ChartAst-S** is powerful and versatile, suited for complex chart analysis but requires more resources.

**15 Nov, 24**

##### Data annotation

Data annotation is the process of labeling or tagging data to make it understandable
for machine learning models.

In simple terms:

- **For images**: You might label objects (e.g., drawing boxes around cars in a photo).
- **For text**: You could tag parts of speech (like labeling nouns and verbs) or identify specific topics.
- **For audio**: You might transcribe spoken words or mark specific sounds.

**Purpose**: By adding labels, you help a model learn patterns, so it can eventually make predictions or
classifications on new, unlabeled data.

**Example**: If you're building a model to recognize cats in photos, you would annotate (label) pictures
with “cat” or “not cat.” The model then learns what “cat” features look like based on these examples.

##### Benchmark:

A benchmark in this context refers to a standard dataset or set of tasks that researchers use to evaluate and compare the performance of different models or systems.

In simple terms:

- **Benchmark for Models**: A benchmark provides a "test" for models, allowing them to show how well they perform on specific tasks, like understanding or interpreting charts.
- **Purpose**: By using the same benchmark, researchers can compare models fairly, as they're tested on the same data and tasks.

**Example**: In chart understanding, a benchmark might include a variety of charts (like bar graphs or pie charts) with annotated information. Models are then evaluated on how accurately they interpret these charts compared to the expected answers.

Here, it sounds like existing benchmarks for chart-based tasks have limitations, so the team is making improvements to the way data is annotated to make the benchmark more useful and accurate.

### what new to this paper: what extraordinary about this paper tasks

- at first constructed `ChartSFT` --> by collecting instruction-following data --> from various chart-related task
- **Instruction-following data** is data created to help a machine learning model understand and carry out
  specific instructions or tasks given by users.

- a simplified breakdown of what the team does to improve the model’s performance in chart understanding:

1. **Add More Diverse Data for Chart-to-Table Translation**:
   - They collect data that includes instructions for converting charts into tables on various topics.
2. **Create "Chain-of-Thought" Annotations for Numerical Questions**:
   - They add step-by-step reasoning (called "chain-of-thought") to help the model understand and solve
     questions involving numbers in charts, boosting its math reasoning skills.
3. **Add a Task for Answering Questions About Specific Chart Elements**:
   - They design questions that require the model to identify and understand specific elements in a chart,
     which improves the model's ability to interpret visual parts and their relationships.
4. **Include More Chart Types (e.g., Radar and Box Plots)**:
   - They add specialized charts like radar and box plots to make the model more flexible and better able to
     handle different chart types.

**Overall**: These improvements create a larger and more varied dataset with more precise annotations,
allowing the model to perform better on a wider range of chart-related tasks than previous benchmarks.

##### Contributions of this paper:

The contributions of this paper can be summarized as
follows:

1. We present ChartAssistant, a vision-language model for chart comprehension and reasoning. ChartAssistant is
   versatile enough to solve various chart-related tasks across a wide range of chart types.
2. We build a chartspecific visual instruction-following benchmark dubbed `ChartSFT`. ChartSFT surpasses existing
   chart-based benchmarks with its larger instruction-following data corpus, a broader range of tasks and chart
   types, and more comprehensive data annotations.

![task of chartAssistant](/image/chartAssistant2.PNG)

## Related Work

### 2.1 Multimodal Foundation Model

- mainly focused on natural images

### 2.2. Chart-specific Vision-Language Model

- Some methods modify vision-language models for chart-related tasks or develop plugin for LLM to understand the chart.
- MatCha extends Pix2Struct by integrating mathematical reasoning and chart data extraction tasks, excelling at chart question answering and chart summarization.
- UniChart undergoes multitask instruction tuning for more chart-related tasks, establishing itself as the most versatile and effective chart vision-language model currently available.

## ChartSFT

- constructed a large-scale chart-specific instruction-tuning
  benchmark called ChartSFT
- Our ChartSFT consists of 39M pieces of chart-text annotated data
- ChartSFT contains charts with both base and specialized types
- Overall, our ChartSFT encompasses nine types of charts
- we also generate some charts with base types from arXiv tables and data augmentation techniques (e.g. various APIs and figure parameters). In particular, we use ChatGPT to suggest the proper
  chart type given each table data from arXiv.

### Chart with Base Types

- We collect instruction-following data with base chart types (i.e. bars, lines, dot-lines, and pies)
- 5 chart-rated tasks, including chart-to-table translation, chart numerical QA, chart referring QA, chart open-ended QA, and chart summarization
