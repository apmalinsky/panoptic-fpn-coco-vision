# Panoptic Segmentation on COCO Dataset with Panoptic FPN

This repository implements a Panoptic Feature Pyramid Network (Panoptic FPN) for panoptic segmentation on the COCO dataset. The project combines instance and semantic segmentation tasks to achieve comprehensive scene understanding.

# Introduction
Panoptic segmentation is the task of assigning every pixel in an image to either an instance of an object or a "stuff" category, such as sky or road. This project utilizes the Panoptic FPN architecture with a ResNet-50 backbone to tackle the COCO dataset.

# Features
- Panoptic FPN architecture: Combines instance and semantic segmentation for end-to-end panoptic segmentation.
- ResNet-50 backbone: Robust feature extraction for improved model accuracy.
- Dual segmentation heads: Instance segmentation and semantic segmentation heads enable holistic scene understanding.
- COCO Dataset Support: Comprehensive evaluation on one of the most challenging datasets.

# Setup and Usage
This project is run in the form of a Juypter Notebook. You can download the file here: [COCO_Panoptic_Segmentation.ipynb](https://github.com/apmalinsky/AAI-521-FinalProject/blob/main/COCO_Panoptic_Segmentation.ipynb)<br />
You can either clone the repo and run it locally, or on Google Colab here: <br />
[COCO_Panoptic_Segmentation Colab Notebook](https://colab.research.google.com/drive/1ox9mnulhXUwGYLefNaVhB7IwLokRL8bn?usp=sharing)

# Results
After training on the subset of 20,000 COCO images using the Panoptic FPN model (with ResNet-50 as the backbone), the model achieved the following scores on the validation dataset:

PQ Score: 18.2 (moderate performance with room for optimization on certain classes).
SQ Score: 49.6 (excellent boundary segmentation).
RQ Score: 22.8 (challenges with instance differentiation, especially in cluttered scenes).

Here are some examples of the model in action:
<img width="1280" height="586" alt="image" src="https://github.com/user-attachments/assets/87c0a373-67aa-496b-b386-703487abbc59" />
<img width="1280" height="586" alt="image" src="https://github.com/user-attachments/assets/af17cb3f-3a10-42a9-a8ef-bfc7b3b0293e" />
<img width="1280" height="586" alt="image" src="https://github.com/user-attachments/assets/c4610c38-e209-4d0a-8103-01e114c17ab0" />

# Feedback and Observations

Strengths:
The Panoptic FPN model performed well in semantic segmentation tasks (e.g., classifying stuff classes like sky or road) due to its efficient multi-scale feature aggregation.
Pre-trained weights from the COCO dataset contributed to faster convergence and higher overall performance, even with a smaller dataset subset.

Areas for Improvement:
Instance differentiation accuracy (RQ) was relatively lower, particularly for objects with similar visual features or heavily overlapping instances. Future work could focus on augmenting training data with such cases.
Training on the full COCO dataset or using more advanced backbones (e.g., ResNet-101 or Swin Transformer) could potentially boost PQ and RQ scores.
Addressing computational constraints could allow for deeper exploration of hyperparameter optimization or more iterations for convergence.

# Challenges and Solutions
- Handling overlapping tasks: Used task-specific loss functions to balance instance and semantic segmentation.
- Data processing bottlenecks: Optimized data pipeline with multi-threading to improve training throughput.
- Model convergence: Applied a tailored learning rate schedule to prevent overfitting and enhance stability.

# Model Architecture
The Panoptic FPN architecture uses a ResNet-50 backbone for feature extraction, followed by an FPN module to handle multi-scale inputs. It features two specialized heads: one for ROI-based instance segmentation and another for dense semantic segmentation. This dual-head design allows for effective pixel-level and instance-level segmentation, achieving state-of-the-art panoptic segmentation performance on COCO.

# Acknowledgements
- COCO Dataset: https://cocodataset.org/
- Panoptic FPN Architecture: Based on research by Facebook AI.
