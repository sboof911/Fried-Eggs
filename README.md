# 🥚 Fried Eggs Classifier

A computer vision project for classifying different types of fried eggs based on visual and semantic features.  
Full dataset, trained models, and notebooks available on [Kaggle](https://www.kaggle.com/code/sbooof/fried-eggs-classifier).

---

## 📌 Project Description

This project tackles a niche image classification task: classifying images of **fried eggs** into one of six categories:

| Label | Description                                                                 |
|-------|-----------------------------------------------------------------------------|
| 0     | Good fried eggs (three yolks, parsley centered, well-cooked, cohesive look)|
| 1     | Overcooked or overturned fried eggs                                         |
| 2     | Fried eggs with **two yolks**                                               |
| 3     | Fried eggs with a **broken yolk**                                           |
| 4     | Fried eggs with **four yolks**                                              |
| 5     | Misplaced or missing ingredients, bad composition, or undercooked eggs      |

---

## 📂 Dataset & Resources

- 📦 **All resources (datasets, models, notebooks)**:  
  👉 [Kaggle Project Page](https://www.kaggle.com/code/sbooof/fried-eggs-classifier)

---

## ⚙️ Pipeline Overview

### 1. **Manual Annotation**
- A sample of the dataset was annotated using **CVAT** to detect relevant objects (e.g., yolks, parsley, plate, etc.).

### 2. **Instance Segmentation**
- A **YOLOv8 instance segmentation** model was trained on the annotated data.
- It was then used to automatically detect objects in the rest of the dataset.

### 3. **Label Assignment**
- A semi-automated algorithm was developed to assign classification labels (0–5) to images based on object detection results.

### 4. **Preprocessing**
- Images were cropped using the **"plate"** bounding box coordinates.
- Resizing and transformation were applied to prepare for model input.
- **Masks** were generated per detection to help the classification model.

### 5. **Dataset Class**
- A custom `Dataset` class was implemented to:
  - Load images and their corresponding masks
  - Apply transformations using `torchvision.transforms`

### 6. **Model Training**
- A pretrained **ResNet** model from `timm` was fine-tuned on the processed dataset.

### 7. **Prediction**
- A custom prediction function:
  - Retrieves the masks for a given image
  - Applies the necessary transformations
  - Feeds the image and masks into the trained model to predict the class

---

## 🧠 Technologies Used

- Python
- PyTorch / Torchvision
- YOLOv8 (Ultralytics)
- OpenCV / PIL
- CVAT (annotation)
- `timm` (model zoo)
- Kaggle Notebooks

---
