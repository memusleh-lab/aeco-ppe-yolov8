# YOLOv8-Object-Detection-Project-M4U3-FMP Group 3
Project-M4U3

**Inference_Baseline**
YOLOv8_Object_Detection_PPE_Inference_Baseline_M4U3.ipynb

**Training_Evaluation**
YOLOv8_Object_Detection_Training&evaluation_M4U3.ipynb

## 1. Project Title: AI-Powered Construction PPE Monitoring

Problem Statement: Manual safety monitoring on high-stakes construction sites is limited by human fatigue and the scale of modern projects. This project provides an automated, real-time "second set of eyes" to identify missing safety gear, reducing the risk of life-threatening accidents.

Classes Detected: The model identifies five key categories: Human, Helmet, Vest, Boots, and Gloves.

Dataset: https://universe.roboflow.com/huiyao-hu-sj18e/construction-ppe-detection/dataset/1

## 2. Problem Statement

This project develops a YOLOv8 object detection model for Construction PPE Detection in AECO environments.

The goal is to detect:
- Human
- Helmet
- Vest
- Boots
- Gloves

The system supports safety compliance screening in construction environments.

## 3. Dataset

- Source: Roboflow – Construction PPE Detection
- Format: YOLOv8
- Train/Validation split: 80/20
- Image size: 640x640

## 4. Model Configuration

- Model: YOLOv8s (Small)
- Epochs: 30
- Image size: 640
- Batch size: default (Colab GPU)
- Ultralytics version: 8.4.x
- Environment: Google Colab (Tesla T4 GPU)
  

## 5. Results Summary

Validation Performance (Performance: Achieved a Mean Average Precision (mAP50) of 0.85+, meeting the project's primary success criteria.):

- Precision: ~0.90+
- Recall: ~0.85+
- mAP50: ~0.90
- mAP50–95: ~0.75

Training curves available in `/results/`.

### Key Observations:
- Strong detection for helmets and vests
- Slightly lower performance for gloves (small object size)
- Stable convergence over 30 epochs
  
Success Evidence: <img width="1191" height="602" alt="image" src="https://github.com/user-attachments/assets/55513183-38fa-4d15-af8c-14c966d33bc7" />


## 6. Reproducibility Steps

To reproduce results:

1. Click **Open in Colab**
2. Runtime → Restart Runtime
3. Run All Cells
4. Model will:
   - Install dependencies
   - Download dataset
   - Train for 30 epochs
   - Generate evaluation metrics
   - Save prediction outputs

Inference: Upload the best.pt weights and run the prediction command: model.predict(source='your_image.jpg', conf=0.5).

## 7. Error Analysis & Limitations

Findings: The model occasionally struggles with image noise and crowded scenes, leading to missed helmets or misclassified gear (e.g., a glove detected as a helmet).

Future Work: Introducing data augmentation (simulated noise and blur) and more diverse "crowded" training images to improve robustness in low-quality conditions.

## 8. Governance & Limitations

This model is an assistive screening tool only.

It:
- Produces false positives
- Produces false negatives
- Must NOT be used as the sole verifier for life-safety decisions.

See `/docs/governance_checklist.md` for full governance review.


## 9. License

### MIT License – Academic use.
### Dataset rights - Public
