# Error Analysis
YOLOv8 PPE (Hard-Hat) Detection – AECO Safety Application  
M4U3 Final Major Project – Group 3



## 1. Overview

This document summarizes observed model failures during validation and new-image inference testing. The analysis focuses on safety-relevant misclassifications, particularly false positives and false negatives.

In a construction safety context, false negatives (missed detection of missing PPE) are considered higher risk than false positives.

---

## 2. False Positives (Incorrect Detection of “No Hard Hat”)

### FP1 – Partially Occluded Helmet

**Observation:**  
The model classified a worker wearing a hard hat as "no_hard_hat" when the helmet was partially occluded by scaffolding.

**Possible Cause:**  
The dataset contained limited examples of partially occluded helmets. The model may rely heavily on full visible helmet contours.

---

### FP2 – White Object Mistaken for Helmet

**Observation:**  
A bright reflective object near the worker’s head was detected as a helmet.

**Possible Cause:**  
The model may be associating bright or circular shapes near head regions with hard hats due to color/shape bias in training data.

---

### FP3 – Motion Blur

**Observation:**  
In a slightly blurred image, the model incorrectly flagged a compliant worker as non-compliant.

**Possible Cause:**  
The dataset likely lacked sufficient examples of motion blur, reducing robustness to real-world camera movement or fast worker motion.

---

## 3. False Negatives (Missed Detection of “No Hard Hat”)

### FN1 – Small Object / Distant Worker

**Observation:**  
A distant worker without a hard hat was not detected.

**Possible Cause:**  
Small object scale relative to image size. YOLO models may struggle when objects occupy very few pixels.

**Risk Level:** High (safety-critical).

---

### FN2 – Similar Head Color to Background

**Observation:**  
A worker without a hard hat was missed when hair color blended with background tones.

**Possible Cause:**  
Insufficient training diversity for skin tones, hair colors, and background similarity conditions.

**Risk Level:** High.

---

### FN3 – Extreme Lighting Condition

**Observation:**  
Under strong backlighting, the model failed to detect the absence of a hard hat.

**Possible Cause:**  
Dataset may not include enough high-contrast or silhouette-style examples.

**Risk Level:** High.

---

## 4. Root Cause Themes

Across errors, several themes were identified:

- Limited variation in lighting conditions
- Limited examples of occlusion
- Insufficient small-object samples
- Potential color/shape bias
- Environmental variation not fully represented

---

## 5. Prioritized Data Improvements (Concrete Actions)

### 1. Add Small-Scale & Distant Worker Samples (Highest Priority)

- Collect or augment images where workers occupy <5% of image area.
- Apply multi-scale training or mosaic augmentation.
- Increase small-object representation in dataset.

**Reason:** Directly reduces high-risk false negatives.

---

### 2. Increase Occlusion & Lighting Diversity

- Add images with:
  - Partial helmet visibility
  - Scaffolding interference
  - Backlighting and shadow-heavy scenes
- Apply brightness/contrast augmentation.

**Reason:** Improves robustness to real site conditions.

---

### 3. Expand Background & Appearance Diversity

- Include varied:
  - Skin tones
  - Hair types
  - Background colors
  - Helmet colors
- Reduce overfitting to specific visual patterns.

**Reason:** Reduces both FP and FN errors caused by visual bias.

---

## 6. Safety Interpretation

Given the AECO safety application:

- False negatives are considered more critical than false positives.
- Model configuration should prioritize recall over precision.
- Human verification is required before disciplinary action.
- The model should function as a decision-support tool, not an autonomous enforcement mechanism.

---

## 7. Conclusion

The model demonstrates strong overall detection capability but exhibits limitations in small-object detection, occlusion handling, and extreme lighting conditions.

Future improvements should focus on dataset expansion and targeted augmentation strategies to enhance robustness and reduce safety-critical false negatives.

---

End of Error Analysis
