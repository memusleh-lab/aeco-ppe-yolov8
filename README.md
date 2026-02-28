# AECO PPE Detection – YOLOv8

## Problem Framing

Use case: Hard-hat detection on construction sites to support PPE compliance monitoring.

Goal: Detect presence or absence of hard hats in site imagery to assist safety supervisors in identifying potential violations.

Operational priority: False Negatives are critical. Missing a worker without a hard hat poses a direct safety risk. The model prioritizes high recall.

---

## Classes

- 0: hard_hat
- 1: no_hard_hat

Label rules:
- Tight bounding boxes around visible helmets
- If occluded, label only visible portion
- Do not label extremely small or ambiguous objects

---

## Dataset

Source: Roboflow (YOLO format export)  
Split: 80/20 train/validation  
Dataset version: v__ (fill this)

---

## Model

YOLOv8 variant: yolov8n (or s – fill yours)  
Epochs: __  
Image size: __  
Batch size: __  

---

## Results (Validation)

Precision: __  
Recall: __  
mAP50: __  
mAP50-95: __  

Key Takeaways:
- Strong detection under normal lighting
- Misses small or heavily occluded helmets
- Occasional confusion with bright background objects

---

## How to Reproduce in Colab

1. Open notebook in Colab
2. Enable GPU
3. Run all cells
4. Metrics and plots will be generated automatically

---

## Reproducibility Checklist

- Dataset link/version included
- Model variant documented
- Training parameters documented
- Ultralytics version documented
- Weights link provided

---

## Governance & Risk

This system supports safety monitoring but does not replace human supervision.

False negatives (missed violations) are critical. Human verification is required before enforcement actions.
