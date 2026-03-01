# Error Analysis

## False Positives

1. Background objects occasionally detected as PPE.
2. Reflective materials misclassified as vests.
3. Distant boots occasionally detected twice.

## False Negatives

1. Small gloves not detected in some images.
2. Partial occlusion reduces helmet detection.
3. Low lighting affects confidence.

## Recommended Improvements

1. Increase dataset size for gloves.
2. Add more low-light training samples.
3. Use YOLOv8m for improved accuracy.
