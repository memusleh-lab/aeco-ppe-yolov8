# YOLOv8-Object-Detection-Project-M4U3-FMP Group 3
Project-M4U3
1. Project Title: AI-Powered Construction PPE Monitoring

Problem Statement: Manual safety monitoring on high-stakes construction sites is limited by human fatigue and the scale of modern projects. This project provides an automated, real-time "second set of eyes" to identify missing safety gear, reducing the risk of life-threatening accidents.

Classes Detected: The model identifies five key categories: Human, Helmet, Vest, Boots, and Gloves.

Dataset: https://universe.roboflow.com/huiyao-hu-sj18e/construction-ppe-detection/dataset/1

2. Results Summary

Performance: Achieved a Mean Average Precision (mAP50) of 0.85+, meeting the project's primary success criteria.

Success Evidence: <img width="1191" height="602" alt="image" src="https://github.com/user-attachments/assets/55513183-38fa-4d15-af8c-14c966d33bc7" />


3. Reproducibility Steps

Setup: Open the provided Colab notebook and run the initial cell to install the ultralytics library.

Inference: Upload the best.pt weights and run the prediction command: model.predict(source='your_image.jpg', conf=0.5).

4. Error Analysis & Limitations

Findings: The model occasionally struggles with image noise and crowded scenes, leading to missed helmets or misclassified gear (e.g., a glove detected as a helmet).

Future Work: Introducing data augmentation (simulated noise and blur) and more diverse "crowded" training images to improve robustness in low-quality conditions.
