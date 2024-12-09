# APPLICAZIONE-AVANZATA-DELLE-TECNICHE-DI-DEEP-LEARNING-ALL-ANALISI-DELLE-SERIE-TEMPORALI

## Description
This repository contains the code, datasets, and results related to a master's thesis on the application of deep learning techniques for advanced time series analysis. The project focuses on using deep learning models such as **Convolutional Neural Networks (CNN)** and **Vision Transformers (ViT)** for the classification of time series transformed into images through innovative techniques like **Gramian Angular Field (GAF)**, **Markov Transition Field (MTF)**, and **RGB**.

## Repository Structure
The structure of the repository is as follows:

- **`methodology.md`**: Detailed description of the methodologies used in the project.
- **`results_summary.md`**: Summary of the obtained results, including performance metrics.
- **`references.md`**: List of the main sources and references used in the project.
- **`requirements.txt`**: List of dependencies required to run the code.

### Main Folders
- **`datasets/`**: Contains raw and pre-processed datasets. The notebooks in this folder generate and manipulate the time series data.
- **`models/`**: Contains notebooks for training U-Net, CNN, and ViT models.
- **`results/`**: Contains the results of training, including logs and graphical visualizations.
- **`config/`**: Configuration files and global parameters used in the project (e.g., paths, hyperparameters).

## Installation
To run the project locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
   ```

2. **Install the dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   This command will install all the necessary libraries to run the code.

## Usage

### Dataset Generation
Run the notebooks in the `datasets/` folder to generate and preprocess the data. These notebooks contain the code to simulate time series and transform them into images using GAF, MTF, and other techniques.
- **`dataset_creation.ipynb`**: Generating time series data.
- **`data_simulation.ipynb`**: Simulating the time series for different datasets.
- **`data_manipulation.ipynb`**: Data manipulation and pre-processing.

### Model Training
The notebooks for model training can be found in the `models/` folder. 
- U-Net, CNN, and ViT models are trained on different image transformations.
- Each notebook contains comments and instructions for training the models.

### Results Visualization
Use the notebooks in the `results/` folder to generate graphs and visualizations of the results obtained during training.
- **`data visualization.ipynb`**: Creates graphs to visualize model performance.
- **`log_test_results/`**: Contains test results.
- **`log_train_history/`**: Contains training history logs.

## Main Results
Below are the key results obtained with the various models for different types of images:

## Results on Train and Validation Sets

### U-Net
| Image Type | MSE           | MAE        |
|------------|---------------|------------|
| GADF       | 9.3 × 10⁻⁶    | 0.0021     |
| GASF       | 2.9 × 10⁻⁶    | 0.0011     |
| Markov     | 2.5 × 10⁻⁶    | 0.0006     |
| RGB        | 2.95 × 10⁻⁵   | 0.0031     |

### CNN
| Image Type | Accuracy (%) | Loss      |
|------------|--------------|-----------|
| GADF       | 99.0         | 0.0055    |
| GASF       | 49.9         | 0.690     |
| Markov     | 49.0         | 0.690     |
| RGB        | 99.0         | 0.0040    |

### ViT
| Image Type | Accuracy (%) | Loss      |
|------------|--------------|-----------|
| GADF       | 99.0         | 0.0075    |
| GASF       | 50.0         | 0.690     |
| Markov     | 50.0         | 0.600     |
| RGB        | 99.0         | 0.0135    |

---

## Results on Test Set

### U-Net
| Image Type | MSE           | MAE        |
|------------|---------------|------------|
| GADF       | 9.2 × 10⁻⁵    | 0.0021     |
| GASF       | 2.8 × 10⁻⁶    | 0.0011     |
| Markov     | 1.7 × 10⁻⁶    | 0.00054    |
| RGB        | 2.9 × 10⁻⁶    | 0.0031     |

### CNN
| Image Type | Accuracy (%) | Loss      |
|------------|--------------|-----------|
| GADF       | 99.0         | 0.0060    |
| GASF       | 50.0         | 0.690     |
| Markov     | 49.0         | 0.690     |
| RGB        | 99.0         | 0.0120    |

### ViT
| Image Type | Accuracy (%) | Loss      |
|------------|--------------|-----------|
| GADF       | 99.0         | 0.0110    |
| GASF       | 50.0         | 0.690     |
| Markov     | 50.0         | 0.600     |
| RGB        | 99.0         | 0.0230    |

---

## Observations

1. **Challenges with GASF and Markov:**
   - Accuracy stagnated around 50%, suggesting difficulty in capturing meaningful patterns.
   - These transformations provided limited information for classification tasks.

2. **Strength of GADF and RGB:**
   - High classification accuracy, with rich temporal and spatial features.
   - RGB images benefited significantly from the GADF channel, capturing local variations effectively.

3. **Model-Specific Strengths:**
   - **U-Net:** Strong performance in reconstruction tasks with minimal errors.
   - **CNN:** Higher recall, reducing false negatives on RGB datasets.
   - **ViT:** Higher precision, particularly effective on GADF datasets.

---

## Considerations on Errors

- **GASF and Markov:** Simplistic representations struggled to encode enough meaningful data for classification.
- **RGB's Dependence on GADF:** GADF played a crucial role in RGB images, as removing it drastically reduced performance.
- **Ambiguity in GAF Representations:** GAF's cosine-based transformation could fail to distinguish time series with inverted signs. RGB images resolved this issue by integrating sine and cosine information.

---

## Future Directions

1. **Advanced Statistical Models:**
   - Explore more sophisticated simulation models to capture richer dynamics.

2. **Real Data Experiments:**
   - Test models on real-world time series to evaluate robustness and practical relevance.

3. **Expanded Classification Tasks:**
   - Implement multi-class or more nuanced labelling to understand underlying dynamics.

4. **Hybrid Architectures:**
   - Combine CNN's pattern recognition with ViT's global attention for a more robust solution.

---

In conclusion, while GADF and RGB transformations excelled, future work should explore improved representations and hybrid model architectures for further advancements.
