# Governance Checklist – YOLOv8 PPE Detection Model

## 1. Intended Use

This model is designed as an assistive screening tool for detecting Personal Protective Equipment (PPE) in construction environments.

Detected classes:
- Human
- Helmet
- Vest
- Gloves
- Boots

The intended purpose is to support safety monitoring workflows by highlighting potential non-compliance cases for human review.

---

## 2. Out-of-Scope / Prohibited Uses

This model MUST NOT be used for:

- Structural safety certification
- Legal compliance enforcement without human verification
- Automated disciplinary action
- Biometric identification of workers
- Worker tracking or surveillance analytics
- Life-safety certification decisions

This system is a screening tool only and does not replace professional safety officers.

---

## 3. Screening vs Certification Distinction

This model performs object detection only.

It:
- Identifies potential PPE presence or absence.
- Flags possible compliance issues.

It does NOT:
- Certify that a site is safe.
- Confirm regulatory compliance.
- Guarantee worker protection.

Human verification is mandatory before acting on outputs.

---

## 4. Risk Assessment (False Positives vs False Negatives)

### False Positives (FP)
Examples:
- Background objects detected as PPE.
- Reflective surfaces misclassified as safety vests.
- Duplicate detections of boots.

Impact:
- Minor operational inefficiency.
- Unnecessary review effort.

Severity: Low to Moderate.

---

### False Negatives (FN)
Examples:
- Small gloves not detected.
- Helmet missed under occlusion.
- Low-light conditions reduce confidence.

Impact:
- Potential safety risk if PPE non-compliance is missed.
- False sense of compliance.

Severity: High in safety-critical environments.

Mitigation:
- Model threshold tuning.
- Additional dataset expansion.
- Mandatory human review.

---

## 5. Privacy & Data Protection

### Data Source
Dataset sourced from Roboflow construction PPE dataset.

### Personally Identifiable Information (PII)
- No facial recognition performed.
- No identity labeling included.
- No biometric identification used.

If individuals appear in images:
- Identities are not recorded.
- The model detects objects, not individuals.

The system complies with the principle of Data Minimization (GDPR Article 5).

---

## 6. Bias & Dataset Limitations

Potential limitations:

- Limited weather variation.
- Limited lighting variation.
- Limited camera angles.
- PPE style variations may not be fully represented.

Model performance may degrade outside the training distribution.

Recommendation:
Additional data collection before deployment in new geographic regions or site types.

---

## 7. Deployment Constraints

Tested Environment:
- Google Colab (Tesla T4 GPU)
- Academic setting

Not tested for:
- Edge deployment
- Real-time production use
- Large-scale multi-camera systems

Performance characteristics may vary in industrial environments.

---

## 8. Model Transparency

Model Architecture:
- YOLOv8 (Ultralytics)
- Pretrained backbone
- Fine-tuned on PPE dataset

Training:
- 30 epochs
- 640 image size
- 80/20 train-validation split

Metrics reported:
- Precision
- Recall
- mAP50
- mAP50–95

Full reproducibility instructions available in README.

---

## 9. Human-in-the-Loop Requirement

This model must operate under human supervision.

Operational policy:
- All flagged detections reviewed by safety personnel.
- Model outputs treated as advisory.
- No automatic enforcement actions.

---

## 10. Safety Disclaimer

This model is an assistive tool for preliminary screening only.

It produces false positives and false negatives.

It must NOT be used as the sole verifier for life-safety decisions.

Human oversight is mandatory.

---

## 11. Licensing & Data Rights

- Code License: MIT License
- Dataset: Roboflow (educational use)
- No proprietary or confidential data included

---

## 12. Regulatory Considerations

This system may fall under "AI-assisted workplace monitoring."

If deployed in the EU:
- GDPR compliance required.
- Worker consent may be required.
- Compliance with EU AI Act high-risk category should be assessed.

This academic prototype has not undergone regulatory certification.
