# AECO Governance Checklist

## Project
*Construction Site Object Detection using YOLOv8*

*Module:* M4U3 - Computer Vision

### Team Members
- Mohamed Elsayed Shaban
- Nadiah Mohammed Aldossary
- Ibrahim Mohammed Adam
- Razan Hanbali

---

## 1. Data Provenance

- *Source:* Roboflow Universe public construction-site object-detection dataset.
- *Dataset Version:* Version 1.
- *Frozen Dataset:* A fixed dataset snapshot is published through the project's GitHub Release to support reproducibility.
- *Dataset Format:* YOLO object-detection format.
- *Target Classes:* Excavator, Grader, Truck, Worker.
- *Training Images:* 330.
- *Validation Images:* 28.
- *Image Size:* 640 × 640 pixels.
- *License:* CC BY 4.0.
- *Reproducibility:* The frozen dataset can be downloaded directly from the GitHub Release without requiring a Roboflow API key or private credentials.

---

## 2. PII Handling and Privacy

- Construction-site imagery may potentially contain workers and other identifiable visual information.
- The purpose of this project is object detection, not worker identification or biometric recognition.
- The model does not attempt to identify individual workers.
- Personal identity is not required for the intended object-detection task.
- Future real-world deployment should apply data-minimization principles and appropriate privacy controls.
- Where identifiable faces, license plates, or other unnecessary PII are present, appropriate anonymization or blurring should be considered before operational use.

---

## 3. Risk Statement

### High-Impact False Negative

A false negative may cause the model to miss a worker, excavator, truck, or other target object.

For safety-related applications, a missed worker or machine could result in an unsafe situation not being flagged for human review.

Therefore, model detections must not be treated as a replacement for professional site supervision or established safety procedures.

### High-Impact False Positive

A false positive may incorrectly identify an object as a worker or construction machine.

This could result in unnecessary alerts, incorrect monitoring information, or unnecessary manual inspection.

False-positive predictions must therefore be reviewed by a human before operational decisions are made.

---

## 4. Model Limitations

The current model has known limitations, including:

- Missed detections.
- Low-confidence predictions.
- Small or distant workers.
- Partial occlusion.
- Challenging viewing angles.
- Low-light and night conditions.
- Class imbalance within the dataset.
- Limited validation representation for Grader and Truck.

The validation split contains annotated instances primarily for Excavator and Worker. Therefore, reliable class-specific validation metrics are not claimed for Grader and Truck.

Future development should include a more balanced dataset and a validation split containing representative examples of all four target classes.

---

## 5. Human-in-the-Loop

The model is intended as an *assistive screening and monitoring tool only*.

All safety-critical or operational decisions must be verified by qualified personnel.

The model must *NOT* be used as the sole verifier for:

- Worker safety compliance.
- Hazard identification.
- Equipment movement decisions.
- Access-control decisions.
- Construction safety certification.
- Any other life-safety decision.

Human review remains mandatory.

---

## 6. Model Performance

Final validation results:

| Metric | Result |
|---|---:|
| Precision | 0.856 |
| Recall | 0.643 |
| mAP@50 | 0.714 |
| mAP@50-95 | 0.422 |

The model was additionally evaluated on *25 completely unseen construction-site images*.

- Images with detections: 19
- Images without detections: 6
- Total detections: 50
- Mean confidence: 0.601

These results demonstrate useful detection capability while also confirming the need for human review and further dataset improvement.

---

## 7. Reproducibility and Handover

The project repository contains:

- Final Google Colab notebook.
- README with Quick Start instructions.
- Frozen dataset reference.
- Training metrics and curves.
- Confusion matrices.
- Validation inference evidence.
- Unseen-image inference evidence.
- Error analysis.
- Governance documentation.
- Trained best.pt model weights.
- requirements.txt.
- Project LICENSE.

The notebook was tested using *Run All* in Google Colab and completed successfully.

The final repository audit achieved:

*9/9 PASSED*

The repository also provides an *Open in Colab* button for direct browser-based reproduction.

---

## 8. Licensing

### Project Code and Documentation

The original software, code, documentation, and project materials produced by the project team are released under the *MIT License*, as defined in the repository LICENSE file.

### Dataset

The source dataset is separately licensed under *CC BY 4.0*.

The project license does not replace or modify the original dataset license.

---

## 9. Responsible-Use Statement

> This model is an assistive tool for preliminary screening only. It can produce false positives and false negatives. It must NOT be used as the sole verifier for life-safety decisions.

Any future deployment should include:

- Human verification.
- Appropriate privacy controls.
- Representative field validation.
- Continuous performance monitoring.
- Documented model limitations.
- Dataset and model version control.
- Periodic review for bias, drift, and changing site conditions.

---

## Governance Status

*Data Provenance:* Documented  
*Privacy / PII:* Reviewed  
*Risk Statement:* Documented  
*Model Limitations:* Documented  
*Human-in-the-Loop:* Required  
*License:* Documented  
*Reproducibility:* Verified  
*Repository Audit:* 9/9 PASSED
