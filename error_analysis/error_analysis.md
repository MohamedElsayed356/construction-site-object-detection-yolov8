# YOLOv8 Construction Site Object Detection - Error Analysis

## 1. Validation Performance

The YOLOv8n model was trained for 50 epochs.

Validation set:
- Images: 28
- Object instances: 135
- Precision: 0.856
- Recall: 0.643
- mAP@50: 0.714
- mAP@50-95: 0.422

Class-level results:
- Excavator:
  - Precision: 0.820
  - Recall: 0.695
  - mAP@50: 0.759
  - mAP@50-95: 0.479

- Worker:
  - Precision: 0.893
  - Recall: 0.592
  - mAP@50: 0.670
  - mAP@50-95: 0.365


## 2. Dataset Limitation

The validation split contains no annotated examples of:

- Grader
- Truck

Therefore, reliable validation metrics for these two classes cannot be
calculated from the current validation set.

This represents an important class-distribution limitation.


## 3. Unseen Image Evaluation

The trained model was tested on 25 completely unseen construction-site
images.

Results:

- Images with detections: 19
- Images without detections: 6
- Total detections: 50

Detected objects:

- Excavator: 25
- Grader: 6
- Truck: 1
- Worker: 18

Confidence statistics:

- Mean confidence: 0.601
- Median confidence: 0.545
- Minimum confidence: 0.253
- Maximum confidence: 0.982

Confidence distribution:

- 0.25-0.49: 21 detections
- 0.50-0.74: 11 detections
- 0.75-1.00: 18 detections


## 4. Observed Error Patterns

Visual inspection of the inference results indicates several limitations.

### Missed detections

Some objects were not detected, especially under:

- low-light conditions
- partial occlusion
- long viewing distances
- unusual viewing angles

Six of the 25 unseen images produced no detections.


### Low-confidence detections

21 of the 50 detections had confidence values between 0.25 and 0.49.

These predictions should be interpreted cautiously.


### Worker detection

Workers were generally detected successfully, but small or distant workers
sometimes produced low-confidence predictions.


### Equipment classification

Construction equipment showed occasional classification uncertainty.

Visually similar heavy equipment may be confused, particularly when:

- partially visible
- viewed from unusual angles
- overlapping other equipment


## 5. Recommended Improvements

Future model iterations should:

1. Increase the number of training images.
2. Improve class balance.
3. Add grader and truck examples to the validation set.
4. Include more night and low-light images.
5. Include more partially occluded objects.
6. Add more varied camera angles and distances.
7. Review low-confidence predictions manually.
8. Consider training a larger YOLOv8 model for comparison.


## Conclusion

The model demonstrates useful construction-site object detection capability,
particularly for excavators and workers.

However, the validation dataset is strongly imbalanced and does not provide
adequate validation evidence for grader and truck classes.

The unseen-image test confirms that the model can generalize to new
construction-site photographs, while also revealing limitations related to
lighting, occlusion, viewing angle, class balance, and object scale.