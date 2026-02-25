# Real-Time Dynamic Trajectory Analysis of Spherical Projectiles
## A YOLO-Based Basketball Tracking System

---

## 📌 Overview

This project presents a comparative evaluation of lightweight object detection architectures for real-time basketball trajectory tracking.  

The system distinguishes between two visually overlapping classes:
- `rim`
- `basketball`

The primary objective was to analyze model performance under challenging dataset conditions including severe class imbalance and high semantic overlap.

Three architectures were evaluated:

- YOLOv8n  
- YOLOv5n  
- MobileNet-SSD  

---

## 🎯 Problem Statement

Detecting a basketball and rim simultaneously presents two major challenges:

1. **Class Imbalance (2.2:1 ratio)**  
   The `rim` class significantly outnumbers the `basketball` class.

2. **High Semantic Overlap**  
   Both classes occupy similar spatial regions, especially during scoring events.

These constraints introduce classification ambiguity and degrade minority-class performance.

---

## 🎥 Video / Photos


https://github.com/user-attachments/assets/4eb07054-9494-495c-ba3c-496a854cb27a

<img width="653" height="369" alt="trajectory_frame1" src="https://github.com/user-attachments/assets/fb198d69-3fbc-46c4-8dff-f0917a792a8c" />

<img width="1572" height="834" alt="trajectory_frame2" src="https://github.com/user-attachments/assets/1971c162-d1d4-4b72-b6a0-115bb35f7371" />


---

## 🏗 Methodology

### Dataset
- Custom dataset with annotated `rim` and `basketball` classes  
- Severe class imbalance (2.2:1)  
- Challenging visual scenarios (motion blur, occlusion, spatial overlap)

### Models Evaluated
- YOLOv8n
- YOLOv5n
- MobileNet-based SSD

### Evaluation Metrics
- mAP@0.5
- Precision–Recall curves
- Convergence rate (epochs)
- Class-wise misclassification analysis

---

## 📊 Key Results

| Model         | mAP@0.5 | Convergence | Observations |
|--------------|---------|------------|--------------|
| YOLOv8n      | 0.787   | 25 epochs  | Best overall performance |
| YOLOv5n      | Lower   | Slower     | Moderate precision |
| MobileNet-SSD| Lowest  | —          | Underperformed |

### Observations

- YOLOv8n achieved highest mAP@0.5 (0.787)
- Minority class (`basketball`) misclassified as `rim` ~50% of the time
- Performance bottleneck identified as **dataset-bound**, not model-bound

Precision–Recall curves (see Figures) show consistent dominance of the `rim` class across all architectures.

---

## 🔄 Real-Time Trajectory Inference

The final system uses YOLOv8n detections to:

- Extract bounding box coordinates
- Compute centroid positions across frames
- Track motion trajectory
- Detect swish events (ball passing cleanly through rim)
- Highlight ball centroid during scoring

This enables automated event detection in live video feeds.

---

## 🧠 Key Insight

The primary limitation was not architectural capacity but dataset constraints:

- Class imbalance
- Semantic overlap
- Spatial co-location

Future performance improvements should focus on:

- Data-centric augmentation
- Loss reweighting strategies
- Two-stage detection pipelines
- Synthetic dataset generation

---

## 🛠 Tech Stack

- Python
- YOLOv8n / YOLOv5n
- MobileNet-SSD
- OpenCV
- PyTorch
- Custom annotated dataset

---

## 📁 Project Structure
/dataset
/models
/training
/inference
/evaluation
README.md
---

## 🚀 Applications

- Sports analytics
- Automated scoring systems
- Real-time motion tracking
- Object trajectory analysis
- Experimental object detection benchmarking

---

## 👨‍💻 Authors

Developed as part of academic research in Computer Engineering.  

Contributors:
- Eshan Shukla
- Kushagra Sinha
- Jash Khatri
- Supriya Agarwal

---

## 📌 Conclusion

YOLOv8n demonstrated superior performance among lightweight models. However, diagnostic evaluation revealed that classification errors stem primarily from dataset limitations rather than architectural weaknesses.

This study highlights the importance of **data-centric optimization** in real-time detection systems.
