# Drone Livestock Detection (YOLOv8)

This repository contains a complete end-to-end pipeline for detecting livestock (sheep) in aerial drone imagery using **Ultralytics YOLOv8**.  
It includes dataset information, training configurations, evaluation metrics, model outputs, and a Google Colab training notebook.

This project demonstrates how modern lightweight vision models can be applied to agricultural monitoring, automated livestock tracking, and UAV-based population analysis.

---

# 📚 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Dataset Details & Insights](#-dataset-details--insights)
- [Model Architecture](#-model-architecture)
- [Training Pipeline](#-training-pipeline)
- [Training Configuration](#-training-configuration)
- [Evaluation & Metrics](#-evaluation--metrics)
- [Results & Visualizations](#-results--visualizations)
- [Colab Notebook](#-colab-notebook)
- [Inference Instructions](#-inference-instructions)
- [Repository Structure](#-repository-structure)
- [Use Cases](#-use-cases)
- [Future Improvements](#-future-improvements)
- [Acknowledgements](#-acknowledgements)

---

# 🚁 Project Overview

Livestock management is increasingly adopting **drone-based automation** to monitor large herds in rough or inaccessible terrain.  
This project develops a **YOLOv8n-based object detection model** capable of detecting **sheep** from aerial images captured by UAVs.

The primary goals of this project:

- Detect livestock from a bird's-eye view  
- Handle shadows, occlusions, and environmental variation  
- Provide a lightweight detector that can run on edge hardware  
- Offer a reproducible training and evaluation pipeline  

---

# 📦 Dataset

The dataset used for this project is hosted on **Roboflow Universe**:

🔗 **Aerial Sheep Dataset**  
https://universe.roboflow.com/riis/aerial-sheep

### **Dataset Summary**
- **Total Images:** 1,727  
- **Annotations:** 55,435 bounding boxes  
- **Classes:** 1 (sheep)  
- **Split:**
  - Train: 1,203  
  - Valid: 290  
  - Test: 234  
- **Average objects per image:** 32.1  
- **Image Resolution:** 8.29–8.85 megapixels  
- **Median Resolution:** 3840 × 2160  
- **Aspect Ratio:** Primarily very wide images  

---

# 📊 Dataset Details & Insights

The dataset offers realistic aerial views with:

### Environmental Variations
- Harsh sunlight  
- Strong shadows  
- Tree occlusion  
- Rocky terrain  
- Grass of varying textures  

### Common Challenges
- Sheep blending into the background  
- Small object size in high-resolution frames  
- Crowded flock regions  
- Variable lighting conditions  

These conditions make the dataset well-suited for evaluating real-world performance.

---

# 🧠 Model Architecture

This project uses **YOLOv8n** ("nano" variant) from Ultralytics.

### Why YOLOv8n?
- Very lightweight  
- Real-time inference  
- Minimal GPU requirements  
- Strong performance for small-object detection  
- Good baseline before upgrading to YOLOv8s/m/l variants  

### YOLOv8 Features Used
- C2f blocks  
- SPPF layer  
- Auto-optimizer selection (AdamW)  
- Automatic mixed precision (AMP)  
- Built-in label caching and data loading optimizations  

---

# 🔧 Training Pipeline

Training was performed fully inside **Google Colab**, using:

- **Tesla T4 GPU**
- **Ultralytics 8.3.228**
- **Torch 2.8.0**
- **Python 3.12**

The pipeline includes:

1. Dataset import from Roboflow  
2. YOLOv8 environment setup  
3. Data caching for fast loading  
4. Augmentation setup  
5. Training and validation loops  
6. Saving best/last weights  
7. Final evaluation with full metrics  
8. Generation of confidence & PR curves  

---

# ⚙️ Training Configuration

### Core Parameters
- **Model:** `yolov8n.pt`  
- **Epochs:** 10  
- **Batch Size:** 64  
- **Image Size:** 448  
- **Optimizer:** AdamW (auto-chosen)  
- **AMP:** Enabled  
- **Train/Val Dataloaders:** 2 workers  

### Augmentations Applied
| Augmentation | Description |
|-------------|-------------|
| Blur | Slight motion blur simulation |
| Median Blur | Reduces noise & texture variation |
| CLAHE | Adaptive histogram equalization |
| HSV | Color and exposure variation |
| Horizontal Flip | Random mirroring |

### Output Weights
- **`weights/best.pt`**
- **`weights/last.pt`**

---

# 📈 Evaluation & Metrics

Final validation results:

| Metric | Score |
|--------|--------|
| **Precision** | 0.793 |
| **Recall** | 0.745 |
| **mAP50** | 0.782 |
| **mAP50-95** | 0.335 |

These results reflect strong performance for a lightweight model trained for only 10 epochs.

Typical YOLO trends observed:
- High mAP50 indicates accurate bounding boxes  
- Lower mAP50-95 expected for tiny objects in aerial imagery  

---

# 🖼 Results & Visualizations

⬇️ **PLACE OUTPUT IMAGES BELOW**  
*(Insert your inference/detection images here.)*  

You may include:
- Validation batch visualizations  
- Prediction results  
- Confidence distribution plots  
- PR curves  

---

# 📓 Colab Notebook

The full training workflow is available in the notebook:

