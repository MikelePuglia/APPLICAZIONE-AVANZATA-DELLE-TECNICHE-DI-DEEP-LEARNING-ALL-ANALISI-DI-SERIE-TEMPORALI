# Results Summary

## Key Findings
1. **U-Net Performance:**
   - Excellent performance in minimizing error metrics (MSE and MAE), especially with GASF and Markov datasets.
   - Struggled slightly with RGB images but maintained overall good reconstruction performance.

2. **CNN Performance:**
   - High classification accuracy (99%) on GADF and RGB datasets.
   - Struggled with GASF and Markov datasets, with accuracy stagnating around 50%.

3. **Vision Transformers (ViT) Performance:**
   - Competed closely with CNN, achieving high accuracy (99%) on GADF and RGB datasets.
   - Demonstrated strong precision on GADF datasets, effectively reducing false positives.

4. **Transformation Effectiveness:**
   - GADF and RGB transformations provided the richest temporal and spatial information.
   - GASF and Markov were less effective for classification tasks.

---

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
   - Accuracy stagnated at around 50%, suggesting difficulty in capturing meaningful patterns.
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
