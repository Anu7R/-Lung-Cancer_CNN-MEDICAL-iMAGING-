This project aims to detect lung tumors from DICOM-format CT scans using deep learning. It includes data preprocessing, patch extraction, CNN-based classification, and evaluation.

1. Dataset Overview
Source: DICOM CT scans from 10 sample cases (SC0001 to SC0010) Annotation CSV: Contains tumor coordinates for baseline and follow-up studies (x1, y1, z1, x2, y2, z2) Goal: Classify 2D image patches as Tumor or Non-Tumor

2. Preprocessing Steps
Tumor Patch Extraction
Extracted 5 patches from each tumor coordinate (baseline + follow-up)
Applied coordinate jittering for local variation
Final: ~912 tumor patches
Non-Tumor Patch Extraction
Randomly sampled patches from healthy tissue
Ensured patches do not overlap tumor areas
Balanced dataset through undersampling/augmentation
3. Data Augmentation
Applied 10–15 random augmentations per tumor patch:
Flipping (horizontal/vertical)
Brightness/contrast adjustment
Final dataset:
Tumor: 1,241 patches
Non-Tumor: 812 patches
Total: 2,053
4. Model Architecture
CNN Model
ResNet50 (pretrained on ImageNet)
+ Global Average Pooling
+ Dense(128, relu)
+ Dense(1, sigmoid)
