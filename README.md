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
- [Acknowledgements](#-acknowledgements)

---

#  Project Overview

Livestock management is increasingly adopting **drone-based automation** to monitor large herds in rough or inaccessible terrain.  
This project develops a **YOLOv8n-based object detection model** capable of detecting **sheep** from aerial images captured by UAVs.

The primary goals of this project:

- Detect livestock from a bird's-eye view  
- Handle shadows, occlusions, and environmental variation  
- Provide a lightweight detector that can run on edge hardware  
- Offer a reproducible training and evaluation pipeline  

---

#  Dataset

The dataset used for this project is hosted on **Roboflow Universe**:

🔗 **Aerial Sheep Dataset**  
https://universe.roboflow.com/riis/aerial-sheep

## Dataset Summary
- **Total Images:** 1,727  
- **Annotations:** 55,435 bounding boxes  
- **Classes:** 1 (sheep)  
- **Split:**
  - Train: 1,203  
  - Valid: 290  
  - Test: 234  
- **Average Objects/Image:** 32.1  
- **Image Resolution:** 8.29–8.85 megapixels  
- **Median Resolution:** 3840 × 2160  

---

#  Dataset Details & Insights

The dataset offers realistic aerial views with:

## Environmental Variations
- Harsh sunlight  
- Strong shadows  
- Tree occlusion  
- Rocky terrain  
- Grass of varying textures  

## Common Challenges
- Sheep blending into the background  
- Small object size in high-resolution frames  
- Crowded flock regions  
- Variable lighting conditions  

---

# 🧠 Model Architecture

This project uses **YOLOv8n** ("nano" variant) from Ultralytics.

## Why YOLOv8n?
- Very lightweight  
- Real-time inference  
- Minimal GPU requirements  
- Strong performance for small-object detection  
- Good baseline before upgrading further  

## YOLOv8 Features Used
- C2f blocks  
- SPPF layer  
- AdamW optimizer (auto-selected)  
- Automatic mixed precision (AMP)  
- Label caching & optimized dataloaders  

---

# Training Pipeline

Training was performed in **Google Colab** using:

- **Tesla T4 GPU**
- **Ultralytics 8.3.228**
- **Torch 2.8.0**
- **Python 3.12**

## Pipeline Steps
1. Dataset import  
2. YOLOv8 setup  
3. Data caching  
4. Augmentations applied  
5. Training (10 epochs)  
6. Saving weights  
7. Final validation  
8. Curve generation  

---

#  Training Configuration

## Core Parameters
- **Model:** `yolov8n.pt`  
- **Epochs:** 10  
- **Batch Size:** 64  
- **Image Size:** 448  
- **Optimizer:** AdamW  
- **AMP:** Enabled  

## Augmentations Used

| Augmentation | Purpose |
|-------------|---------|
| Blur | Motion blur simulation |
| Median Blur | Noise reduction |
| CLAHE | Contrast enhancement |
| HSV | Color/brightness variation |
| Horizontal Flip | Mirror augmentation |

## Output Weights
- `weights/best.pt`  
- `weights/last.pt`

---

# 📈 Evaluation & Metrics

| Metric | Score |
|--------|--------|
| **Precision** | 0.793 |
| **Recall** | 0.745 |
| **mAP50** | 0.782 |
| **mAP50-95** | 0.335 |

---

# Results & Visualizations

<img width="667" src="https://github.com/user-attachments/assets/3a5be979-e6c0-4f04-9891-88fba4d727d6" />
<img width="670" src="https://github.com/user-attachments/assets/ec0210a2-a124-4322-9ae5-c71d5d92ecf5" />
<img width="667" src="https://github.com/user-attachments/assets/c9838dd4-bfa3-46ff-abcd-37c5a1034e6d" />

---

# Colab Notebook

🔗 **Google Colab Notebook:**  
https://colab.research.google.com/drive/1gL1J5PHfEaeRqdVnNoMy8k-WBHwfxsO7?usp=sharing

This repository includes the `.pdf` versions of the notebook.

---

# Acknowledgements

- **Roboflow Universe – Aerial Sheep Dataset**  
  https://universe.roboflow.com/riis/aerial-sheep

- **Google Colab Notebook of the drone_livestock.ipynb**  
  https://colab.research.google.com/drive/1gL1J5PHfEaeRqdVnNoMy8k-WBHwfxsO7?usp=sharing

- **Ultralytics YOLOv8**  
  https://github.com/ultralytics/ultralytics

- **Google Colab GPU Environment**

## Done by - Amirtha Ganesh R 
### contact me @ - amirthaganeshramesh@gmail.com 
