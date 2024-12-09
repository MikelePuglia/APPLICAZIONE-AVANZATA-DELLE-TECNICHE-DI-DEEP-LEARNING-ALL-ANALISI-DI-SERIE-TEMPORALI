# Methodology

## Introduction
This project focuses on applying deep learning techniques to advanced time series analysis. The methodology includes:
1. Simulating time series data using stochastic models.
2. Transforming time series into images through advanced techniques.
3. Leveraging deep learning models such as Convolutional Neural Networks (CNN), Vision Transformers (ViT), and U-Net for classification tasks.

This approach aims to demonstrate the effectiveness of these models in capturing complex temporal dynamics.

---

## Data Processing
### Data Generation
- Time series data were simulated using the **Vasicek model**, widely used in finance to model interest rate dynamics.
- Parameters for simulation:
  - Mean reversion speed (**κ**): 0.1
  - Long-term mean (**θ**): 0.05
  - Volatility (**σ**): 0.2
  - Time step (**dt**): 1/1000

**Dataset Composition:**
- Four datasets were created, each containing 160,000 images of size 32x32 pixels.
- Labels:
  - `1`: If the last value of the series is greater than the first.
  - `0`: Otherwise.

---

### Data Transformation
Time series were divided into windows of 32 values and transformed into images using two main techniques:

1. **Gramian Angular Field (GAF):**
   - Converts time series into a Gramian matrix, representing angular relationships.
   - Produces two variants:
     - **GASF (Gramian Angular Summation Field)**: Encodes summation relationships.
     - **GADF (Gramian Angular Difference Field)**: Encodes difference relationships.

2. **Markov Transition Field (MTF):**
   - Captures the transition dynamics between different quantiles of the time series.

3. **RGB Images:**
   - Combines GASF, GADF, and MTF into a single RGB image (each channel corresponds to one transformation).

These transformations enhance feature extraction by converting one-dimensional temporal data into two-dimensional visual representations.

---

## Model Architectures

### U-Net
- **Purpose:** Originally developed for biomedical image segmentation, U-Net was adapted for classification tasks in this study.
- **Architecture:**
  - **Encoder:** Convolutional layers reduce spatial dimensions while extracting features.
  - **Decoder:** Upsampling layers restore the original spatial dimensions.
  - Skip connections between encoder and decoder layers preserve high-resolution details.
- **Use Case in This Project:** U-Net was applied to specific datasets for experimental comparison with CNN and ViT.

### Convolutional Neural Networks (CNN)
- **Architecture Details:**
  - Multiple convolutional and pooling layers to extract hierarchical features.
  - Dense layers at the end for classification.
- **Image Types:**
  - GASF, GADF, MTF, and RGB.
- **Strengths:** Known for their robust pattern recognition capabilities in visual data.

### Vision Transformers (ViT)
- **Architecture Details:**
  - Divides images into fixed-size patches.
  - Processes patches using self-attention mechanisms to capture global relationships.
  - Particularly effective for capturing complex dependencies across an entire image.
- **Advantages over CNN:** Ability to learn global features from the first layers, making them ideal for diverse datasets.

---

## Training Process

### Preprocessing
1. Images were normalized to improve convergence.
2. Data augmentation techniques (rotation, flipping) were applied to prevent overfitting.

### Training Configuration
- **Loss Functions:**
  - **Binary Crossentropy:** For binary classification tasks.
  - **Mean Squared Error (MSE):** For regression-based experiments.
- **Optimizer:** Adam with an adaptive learning rate scheduler.
- **Metrics:** 
  - Accuracy (for classification).
  - Mean Absolute Error (MAE, for error analysis).

### Model Evaluation
- **Training/Validation Split:** 80/20 split for training and validation sets.
- **Test Dataset:** Separate test set used for final evaluation.

---

## Implementation Details

### Frameworks and Tools
- **Libraries:** TensorFlow, Keras, PyTS, Matplotlib, and Scikit-learn.
- **Hardware:** Trained on NVIDIA GPUs with optimized data pipelines for efficient performance.

### Challenges
- Computational complexity due to the large number of image transformations.
- Fine-tuning ViT models required careful optimization of hyperparameters to balance accuracy and runtime.

---

## Summary
This project showcased the potential of combining advanced data transformations (GAF, MTF) with state-of-the-art deep learning architectures (CNN, U-Net, ViT). The experiments validated the models' capability to accurately classify time-series-derived images and highlighted new opportunities for using vision-based techniques in temporal data analysis.