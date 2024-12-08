**8 Dec, 24**

# Mulberry Leaf Disease Detection Using CNN-Based Smart Android Application

## Abstract

1. **Background**:

   - Mulberry leaves are the main food for silkworms, which produce silk.
   - Mulberry trees can easily catch diseases, spreading fast and causing big losses.
   - It's hard to check for diseases manually on large farms.

2. **Solution**:

   - The researchers used computer vision (a technology where computers can "see" and analyze images) to detect leaf diseases early.
   - This could save up to 90% of the production loss caused by diseases.

3. **Data Collection**:

   - They collected **1,091 images** of mulberry leaves from two regions in Bangladesh.
   - The leaves were grouped into three categories:
     - Healthy leaves.
     - Leaves affected by rust (a common fungal disease).
     - Leaves affected by spots (another disease).
   - These images were divided into training, testing, and validation sets for machine learning experiments.

4. **Preprocessing and Augmentation**:

   - The team increased the number of images from 1,091 to **6,000 images** using techniques like flipping, rotating, and creating synthetic (computer-generated) versions of the original images.
   - This helps the model learn better.

5. **Models Used**:

   - They tested three popular **pre-trained convolutional neural networks (CNNs)**, which are models that specialize in analyzing images:
     - **MobileNetV3Small** (lightweight and fast).
     - **ResNet50** (deep and accurate).
     - **VGG19** (older but strong).

6. **Modifications**:

   - Four extra **convolutional layers** (these process image features step by step, like detecting edges, textures, etc.) were added to each model.
   - The new layers had 512, 128, 64, and 32 output channels (these numbers represent the layers' capacity to learn details).

7. **Performance Comparison**:

   - The modified **MobileNetV3Small** was the best:
     - **Precision**: 97.0% (correctly identifying diseased vs. healthy leaves).
     - **Recall**: 96.4% (catching most of the diseased leaves).
     - **F1-Score**: 96.4% (balance of precision and recall).
     - **Accuracy**: 96.4% (overall correctness).
   - This means it’s both fast and accurate, making it ideal for practical use.

8. **Smartphone App**:

   - They built a mobile app using this model, making it easy for farmers to identify leaf diseases on the go.

9. **Validation**:

   - They used **Grad-CAM visualization**, a technique that highlights which part of the image the model focuses on when making decisions.
   - Experts confirmed the model's focus areas matched actual disease symptoms.

10. **Conclusion**:
    - The study shows that this improved MobileNetV3Small model can efficiently and accurately detect mulberry leaf diseases.
    - It outperforms other existing methods and is practical for real-world farming.
    - **Explainable AI (XAI)**: Making AI decisions easy to understand, so humans trust the model.

- Key Terms Simplified:
  - **Convolutional Neural Network (CNN)**: A computer model that mimics how our eyes process images step by step.
  - **Pretrained Model**: A model already trained on general images, then fine-tuned for specific tasks (like mulberry leaves).
  - **Grad-CAM**: A tool to visualize which part of the image the model "looks at" to make decisions.

## Introduction

1. **About Mulberry Trees**:

   - **Mulberry trees** (Morus alba) are native to China but are grown worldwide for their various uses.
   - The tree is important for food (fruits, teas), medicines (antioxidant and anti-inflammatory properties), and silk production.

2. **Role in Sericulture (Silk Production)**:

   - Mulberry leaves are the **only food** for silkworms, which produce silk.
   - High-nutrient varieties like **S-36 and BR-2** are best for silkworm growth, improving the **quality and quantity of silk**.
   - Healthy leaves have essential nutrients like proteins, chlorophyll, and carotenoids, which help silkworms grow and make silk.

3. **Impact of Diseases**:

   - **Fungal diseases** (like rust and leaf spot) reduce the nutritional value of leaves, affecting protein, amino acids, and chlorophyll levels.
   - **Bacterial diseases** lower sugar and vitamins in leaves, impacting silk quality.

4. **Data for Study**:

   - Since no existing image dataset of mulberry diseases was available, researchers collected **leaf images** from a garden in **Rajshahi, Bangladesh**.
   - A **sericulture expert** labeled them into three groups:
     - Healthy.
     - Rust-affected.
     - Spot-affected.
   - The study focused on two common winter-season diseases in Bangladesh.

5. **Study Goals**:  
   The research aimed to:

   - **Improve model performance** by using **data augmentation** (creating new images by flipping, rotating, etc.).
   - Use **Transfer Learning (TL)**: Starting with a pretrained model and fine-tuning it to detect mulberry diseases.
   - Ensure the model’s predictions were understandable with **Grad-CAM**: A technique that shows which parts of an image the model used for its decision (e.g., focusing on diseased spots).

6. **Structure of the Paper**:
   - Section II: Previous research in this area.
   - Section III: Details of the methods used.
   - Section IV: Results of the model and comparisons with other studies.
   - Section V: Discussion and future improvements.
   - Section VI: Final conclusions.

- Key Terms Explained:
  - **Data Augmentation**: Adding new images by modifying existing ones (e.g., flipping or rotating) to improve the training of models.
  - **Transfer Learning**: Using a pre-trained model and adapting it to a new task, saving time and improving accuracy.
  - **Grad-CAM**: A tool to highlight image areas the model focuses on, ensuring it makes logical decisions.

## Literature Review

![table 1](/image/Mulberry-Leaf-with-CNN/table1.PNG)

- didn't read this section

## Materials and methods

![fig 1](/image/Mulberry-Leaf-with-CNN/fig1.PNG)

- **Objective**:
  The study aimed to improve the **MobileNetV3Small** model for classifying mulberry leaf diseases by adding extra processing layers to its original design.

### **A. Image Collection**:

![fig 2](/image/Mulberry-Leaf-with-CNN/fig2.PNG)
![table 2](/image/Mulberry-Leaf-with-CNN/table2.PNG)

1. **Dataset Details**:
   - Images of mulberry leaves were collected from regions in **Rajshahi, Bangladesh** (Mirganj, Bagha, and Vodra).
   - **Expert Categorization**: A specialist with 10+ years of experience classified the leaves into:
     - **Healthy**: 440 images.
     - **Rust-affected**: 489 images.
     - **Spot-affected**: 162 images.
   - All images were high resolution (4,000 × 6,000 pixels).
   - Table 2 and Figure 2 in the paper detail this dataset.

### **B. Data Preprocessing**:

Before training the model, preprocessing made the images suitable for analysis. Steps included:

1. **Dataset Scaling/Resizing**:

   - Images were resized to **124 × 124 pixels** to reduce storage needs and speed up processing.

2. **Normalization**:
   - Pixel values were converted from **0-255** to a smaller range (**0-1**) by dividing each value by 255.
   - This ensures consistent data input for the model.

- **Image Augmentation**:

![fig 3](/image/Mulberry-Leaf-with-CNN/fig3.PNG)

**Augmentation** was used to create more training data, improving the model's ability to learn. Techniques included:

1. **Rotation**: Images were rotated by up to 30 degrees.
2. **Flipping**: Images were randomly flipped horizontally or vertically.
3. **Affine Transformations**: Small changes were made, such as:
   - Rotations (5–15 degrees).
   - Shifts (moving the image slightly left/right or up/down).
   - Scaling (resizing by 70–80%).

- **Why Augmentation?**:

  - The original dataset was **too small** (764 training images).
  - Augmentation increased the dataset to **6,000 images** evenly split into three categories.
  - Each category had 2,000 images for a balanced and realistic training set.
  - This helped the model learn better and perform well on unseen data.

- **Results**:

By creating more diverse and balanced images, the training dataset became large, rich, and representative, which improved the model's accuracy and reliability.

- Key Terms Explained:

  - **Preprocessing**: Preparing raw data (e.g., resizing, normalizing) to make it suitable for analysis.
  - **Normalization**: Scaling pixel values so they are small and consistent, helping the model process images efficiently.
  - **Augmentation**: Expanding the dataset by creating variations of the original images (like flipping or rotating).
  - **Affine Transformation**: Slight changes like shifting or resizing to make the model handle different orientations and sizes better.

### C. Modified Pre-trained Model

Here’s a simple, step-by-step summary of the **Modified Pretrained Model Architecture** section:

---

### **Objective**:

The study used existing models (**MobileNetV3Small**, **VGG19**, and **ResNet50**) to classify mulberry leaf diseases. It enhanced these models by adding layers to make them more accurate and suitable for the task.

---

### **1. Base Models**:

The study used **pretrained models** (models already trained on large datasets) as starting points. Here's why these models were chosen:

- **MobileNetV3Small**:

  - Lightweight, fast, and ideal for mobile/embedded devices.
  - Uses **depth-wise separable convolutions** (special layers that process images efficiently).
  - Example: It’s like using a smaller yet highly efficient car for city roads instead of a bulky truck.

- **VGG19**:

  - A deep model with 19 layers, known for its simplicity.
  - Processes images step-by-step through **convolution** (extracts patterns from images).

- **ResNet50**:
  - Uses **residual connections** (shortcuts that help avoid problems when training very deep models).
  - Example: If solving a tough puzzle, this model uses shortcuts to remember earlier steps.

---

### **2. Added Convolutional Layers**:

Extra layers were added to improve feature detection for specific tasks.

- **Why Add Layers?**:

  - Original models are generic. The new layers help capture details specific to mulberry leaves.
  - Example: A general camera can take pictures of anything, but adding a special lens helps focus on specific objects.

- **Details of Added Layers**:
  - **Four convolutional layers** with decreasing channels (512 → 128 → 64 → 32).
  - Each layer uses:
    - **ReLU activation** (helps the model learn non-linear patterns).
    - **Batch Normalization** (improves speed and stability).
    - **Dropout** (prevents overfitting by randomly ignoring parts of the model during training).

---

### **3. Fully Connected Layers**:

After the convolutional layers:

- The features (patterns learned from the images) are flattened into a vector.
- This vector is passed through **fully connected layers**, which map features to the final classes (healthy, rust, or spot).
- A **Dropout layer** is added to ensure the model generalizes well.

---

### **4. Forward Propagation**:

- The input (image) passes through:
  - Base MobileNetV3Small model.
  - Added convolutional layers.
  - Fully connected layers.
- The result: Class probabilities (e.g., how likely an image is healthy or diseased).

---

### **5. Training**:

- **Loss Function**: Measures how far the model’s predictions are from the actual labels. Used **Cross-Entropy Loss** (common for classification).
- **Optimizer**: Used **ADAM** (adjusts the model weights efficiently during training).
- Goal: Combine MobileNetV3Small’s lightweight design with the added layers’ power for better disease classification.

---

### Key Takeaways:

- **MobileNetV3Small** is a compact and efficient base, especially for mobile apps.
- Adding layers allows the model to learn more specific patterns for leaf diseases.
- The training process balances accuracy and speed, ensuring the model works well even with limited computing power.

---

This section focuses on modifying existing models to make them more suitable for the specific task of classifying mulberry leaf diseases.
