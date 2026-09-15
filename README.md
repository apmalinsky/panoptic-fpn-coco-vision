# Panoptic Segmentation Engine on COCO Dataset

An implementation of a Panoptic Feature Pyramid Network (Panoptic FPN) for comprehensive scene understanding, combining instance and semantic segmentation tasks on the COCO dataset. Developed as part of the Applied Artificial Intelligence Program at the University of San Diego (USD).

## 🚀 Project Overview
Panoptic segmentation unifies semantic segmentation (classifying "stuff" categories like sky or road) and instance segmentation (detecting distinct object instances like cars or people). This project utilizes a **Panoptic FPN** architecture with a **ResNet-50** backbone to process multi-scale inputs and execute dual-head pixel-level and instance-level segmentation.

## 🛠️ Key Features & Architecture
* **Panoptic FPN Architecture:** Combines feature extraction and multi-scale pyramids for end-to-end scene parsing.
* **ResNet-50 Backbone:** Leverages robust feature extraction for improved structural accuracy.
* **Dual-Head Design:** Specialized heads dedicated to ROI-based instance segmentation and dense semantic segmentation.
* **Task Optimization:** Utilizes task-specific loss balancing and custom learning rate schedules to enhance stability and prevent overfitting.

## 📊 Results & Validation Metrics
Trained on a subset of 20,000 COCO images, the model achieved the following performance benchmarks on the validation set:
* **PQ (Panoptic Quality) Score:** 18.2 *(moderate baseline with clear paths for optimization)*
* **SQ (Segmentation Quality) Score:** 49.6 *(demonstrating excellent boundary definition)*
* **RQ (Recognition Quality) Score:** 22.8 *(highlighting challenges with instance differentiation in cluttered scenes)*

## 🖼️ Model in Action
| Prediction Sample 1 | Prediction Sample 2 | Prediction Sample 3 |
| :---: | :---: | :---: |
| ![Sample 1](https://github.com/user-attachments/assets/87c0a373-67aa-496b-b386-703487abbc59) | ![Sample 2](https://github.com/user-attachments/assets/af17cb3f-3a10-42a9-a8ef-bfc7b3b0293e) | ![Sample 3](https://github.com/user-attachments/assets/c4610c38-e209-4d0a-8103-01e114c17ab0) |

## 💻 Setup and Usage
This project is executed via Jupyter Notebook. You can access it through:
* **Local Notebook:** [COCO_Panoptic_Segmentation.ipynb](https://github.com/apmalinsky/panoptic-fpn-coco-vision/blob/main/COCO_Panoptic_Segmentation.ipynb)
* **Google Colab:** [Run on Colab](https://colab.research.google.com/drive/1ox9mnulhXUwGYLefNaVhB7IwLokRL8bn?usp=sharing)

## ⚠️ Challenges and Solutions
* **Handling Overlapping Tasks:** Utilized task-specific loss functions to effectively balance and optimize both instance and semantic segmentation streams.
* **Data Processing Bottlenecks:** Optimized the data loading pipeline using multi-threading to maximize GPU utilization and improve training throughput.
* **Model Convergence:** Implemented a tailored learning rate schedule and regularization techniques to prevent overfitting and enhance training stability.
  
## 🔍 Engineering Insights & Limitations
* **Strengths:** High efficiency in semantic segmentation ("stuff" classes) driven by multi-scale feature aggregation and pre-trained COCO weight transfer.
* **Areas for Improvement:** Instance differentiation (RQ) drops in heavily cluttered or overlapping object scenes, presenting clear avenues for data augmentation or upgrading to a ResNet-101 / Swin Transformer backbone.

## 📚 Acknowledgments
* **Dataset:** [COCO Dataset](https://cocodataset.org/)
* **Architecture:** Based on Panoptic FPN research by Facebook AI Research (FAIR).
