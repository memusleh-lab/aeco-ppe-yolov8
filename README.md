# AECO PPE Detection – YOLOv8

---

## 1. AECO Problem Framing

**Use case:** Hard-hat detection on construction sites to support PPE compliance monitoring.

**Why this matters:** Construction sites present significant safety risks. Detecting workers without hard hats can assist supervisors in identifying potential violations early.

**Success Criteria:**
- Primary metric: High Recall (to reduce false negatives)
- Secondary metrics: Precision and mAP50 / mAP50–95
- Operational requirement: Human verification required before enforcement

---

## 2. Class List + Label Rules

### Classes
- 0: hard_hat
- 1: no_hard_hat

### Label Rules
- Tight bounding boxes around visible helmets.
- If partially occluded, label only the visible portion.
- Do not label extremely small, ambiguous, or blurred objects.
- Avoid guessing when object identity is unclear.

---

## 3. Dataset Reference

**Source:** Roboflow  
**Dataset Link:** [INSERT ROBOFLOW LINK HERE]  
**Format:** YOLOv8  
**Split:** 80% Train / 20% Validation  
**Dataset Version:** v__ (insert version number)

---

## 4. Model & Training Configuration

- Model variant: yolov8n (or yolov8s)
- Epochs: __
- Batch size: __
- Image size (imgsz): __
- Ultralytics version: __

Weights link: [Insert GitHub Release or external link]

---

## 5. Results Summary (Validation)

**Precision:** __  
**Recall:** __  
**mAP50:** __  
**mAP50–95:** __  

### Key Takeaways
- Strong detection performance under standard lighting conditions.
- Reduced performance when helmets are partially occluded or small.
- Model prioritizes recall to reduce missed safety violations.

---

## 6. How to Reproduce (Google Colab)

1. Open `/notebooks/02_train_eval.ipynb` in Google Colab.
2. Enable GPU (Runtime → Change runtime type → GPU).
3. Run all cells from top to bottom.
4. Outputs generated:
   - Training metrics (Precision / Recall / mAP50 / mAP50–95)
   - Saved curves in `/results/curves/`
   - Prediction samples in `/results/evidence/`

If GPU is unavailable:
- Run a short verification training (5 epochs).
- Load provided trained weights for inference.

---

## 7. Reproducibility Checklist

- Dataset link and version documented
- YOLO model variant specified
- Training parameters (epochs/batch/imgsz) specified
- Ultralytics version documented
- Weights link provided
- Training curves saved in `/results/`
- Validation and new-image predictions included

---

## 8. Governance & Licensing

This model supports PPE monitoring but does not replace human safety supervision.

False negatives are critical in this application. All detections must be reviewed by a human operator before enforcement.

License: [MIT / Apache / Internal Use Only]  
Dataset rights: [Public / Licensed / Owned – specify source]
