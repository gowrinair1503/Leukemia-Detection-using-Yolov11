# Leukemia Detection Using YOLOv11

## Overview

This project presents an automated leukemia cell detection system using the YOLOv11 object detection framework. The objective is to accurately identify and classify leukemic cells in microscopic blood smear images as either **blast** (malignant) or **non-blast** cells. The study leverages transfer learning to adapt a pre-trained YOLOv11n model to the specialized domain of hematological image analysis.

---

## Objectives

- Detect leukemia cells in microscopic blood smear images.
- Classify cells as **blast** or **non-blast**.
- Evaluate the effectiveness of transfer learning for medical image analysis.
- Compare zero-shot performance with fine-tuned model performance.

---

## Dataset

The dataset is derived from the **All-IDB (Acute Lymphoblastic Leukemia Image Database)** and was annotated using Roboflow.

### Dataset Statistics

- Total Images: 487
- Total Labels: 487
- Classes: 2
  - Blast Cells
  - Non-Blast Cells
- Annotation Format: YOLO Bounding Boxes

### Annotation Details

Each annotation contains:
- Class ID
- Normalized x-center coordinate
- Normalized y-center coordinate
- Bounding box width
- Bounding box height

---

## Baseline: Zero-Shot Model

Before training, a pre-trained YOLOv11n model trained on the COCO dataset was tested directly on leukemia images.

### Observation

The model failed to recognize leukemia cells and misclassified them as common objects such as:

- Apple
- Donut
- Teddy Bear

This demonstrated the significant domain gap between natural images and medical microscopic images and highlighted the need for domain-specific training.

---

## Methodology

The project employs **Transfer Learning** using YOLOv11n.

### Workflow

1. Dataset Annotation using Roboflow
2. Data Preprocessing and Augmentation
3. Transfer Learning using YOLOv11n
4. Model Fine-Tuning
5. Performance Evaluation

The model was trained to detect:

- Blast Cells (Malignant)
- Non-Blast Cells

---

## Model Configuration

| Parameter | Value |
|------------|---------|
| Model | YOLOv11n |
| Epochs | 50 |
| Image Size | 640 × 640 |
| Batch Size | 16 |
| Optimizer | AdamW |
| Learning Rate | 0.001 |

---

## Technologies Used

- Python
- YOLOv11 (Ultralytics)
- Roboflow
- Google Colab
- OpenCV
- NumPy
- Pandas

---

## Results

The fine-tuned YOLOv11n model achieved excellent performance on the leukemia detection task.

| Metric | Score |
|----------|----------|
| mAP@50-95 | 96.7% |
| Precision | 99.6% |
| Recall | 99.9% |

### Class-wise Performance

| Class | mAP@50-95 |
|---------|---------|
| Blast Cells | 97.2% |
| Non-Blast Cells | 96.2% |

These results demonstrate the effectiveness of YOLOv11 for automated leukemia cell detection and classification.

---

## Project Workflow

```text
Microscopic Blood Images
            │
            ▼
Dataset Annotation
(Roboflow)
            │
            ▼
Data Augmentation
            │
            ▼
YOLOv11n Fine-Tuning
            │
            ▼
Model Validation
            │
            ▼
Performance Evaluation
            │
            ▼
Blast / Non-Blast Detection
