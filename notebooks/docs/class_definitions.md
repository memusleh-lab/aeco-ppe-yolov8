# Class Definitions  
YOLOv8 PPE & Worker Detection – AECO Safety Application  
M4U3 Final Major Project – Group 3

---

## 1. Overview

This document defines the object classes used in the YOLOv8 object detection model for construction site safety monitoring.

The model detects multiple Personal Protective Equipment (PPE) elements and workers to support safety compliance analysis in AECO environments.

---

## 2. Class List

| Class ID | Class Name | Description |
|----------|------------|-------------|
| 0 | boots | Protective safety boots worn by construction workers. |
| 1 | gloves | Protective safety gloves worn by workers. |
| 2 | helmet | Protective hard hat worn by workers. |
| 3 | human | A visible worker or person present in the construction site image. |
| 4 | vest | High-visibility safety vest worn by workers. |

---

## 3. Annotation Guidelines

The following labeling principles were applied during dataset preparation:

- Bounding boxes tightly enclose the visible PPE item or person.
- Partial visibility (occlusion) is annotated when the object remains identifiable.
- Each instance is labeled separately when multiple workers or PPE items appear.
- Small objects with extremely low resolution were avoided to reduce noise.
- Ambiguous or visually unclear objects were not labeled.

---

## 4. Class-Specific Considerations

### Boots
- Annotated when clearly visible on a worker’s feet.
- Not labeled when fully occluded or outside the image boundary.

### Gloves
- Annotated when visible on worker hands.
- May be difficult under occlusion or low lighting.

### Helmet (Hard Hat)
- Annotated when visibly worn.
- Partial occlusion is labeled if helmet contour is distinguishable.
- Critical safety-related class.

### Human
- Represents the worker presence.
- Used to provide contextual detection of PPE compliance.

### Vest
- High-visibility safety vest.
- Reflective or bright-colored garments labeled accordingly.

---

## 5. Safety Context

This multi-class detection approach enables:

- Identification of PPE compliance
- Contextual understanding of worker presence
- Potential extension toward automated compliance monitoring

In safety-critical applications:
- Missed detection of PPE (false negatives) carries higher risk.
- Model outputs should be reviewed by human supervisors before enforcement decisions.

---

## 6. Known Limitations

- Small PPE items may be harder to detect at long distances.
- Occlusion (scaffolding, machinery) can reduce detection reliability.
- Lighting conditions significantly impact detection accuracy.
- The dataset may not cover all construction site environments.

---

End of Class Definitions
