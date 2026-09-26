# Construction Site Object Detection using YOLOv8

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MohamedElsayed356/construction-site-object-detection-yolov8/blob/main/notebook/M4U3_Construction_Site_Object_Detection_YOLOv8.ipynb)

## M4U3 Computer Vision Assignment

This project develops and evaluates a YOLOv8 object-detection model for
construction-site monitoring.

The model was trained to detect four object classes:

- Excavator
- Grader
- Truck
- Worker

The repository is designed to support reproducibility in Google Colab
without requiring a Roboflow API key or private credentials.

---

## Project Objectives

The main objectives are to:

1. Train a YOLOv8 object-detection model on construction-site imagery.
2. Evaluate model performance using validation metrics and curves.
3. Test the trained model on completely unseen construction-site images.
4. Analyse model errors and limitations.
5. Document dataset governance and licensing.
6. Provide a reproducible Google Colab workflow.

---

## Dataset

The dataset was prepared in YOLOv8 object-detection format.

### Classes

| ID | Class |
|---|---|
| 0 | excavator |
| 1 | grader |
| 2 | truck |
| 3 | worker |

### Dataset Split

- Training images: 330
- Validation images: 28

The validation set contains annotated examples of excavators and workers,
but no annotated grader or truck instances. This limitation is considered
when interpreting validation performance.

### Frozen Dataset

For reproducibility, the exact dataset snapshot used for this project is
published as a public GitHub Release asset.

This allows the notebook to download the dataset without:

- Roboflow credentials
- API keys
- Colab Secrets

---

## Model

The project uses *YOLOv8n - Ultralytics*.

Training configuration:

- Epochs: 50
- Image size: 640
- Hardware used: NVIDIA Tesla T4 GPU
- Framework: Ultralytics YOLOv8

The trained model is available in:

weights/best.pt

---

## Validation Results

| Metric | Result |
|---|---:|
| Precision | 0.856 |
| Recall | 0.643 |
| mAP@50 | 0.714 |
| mAP@50-95 | 0.422 |

### Class Performance

| Class | Precision | Recall | mAP@50 | mAP@50-95 |
|---|---:|---:|---:|---:|
| Excavator | 0.820 | 0.695 | 0.759 | 0.479 |
| Worker | 0.893 | 0.592 | 0.670 | 0.365 |

Reliable validation metrics cannot be reported for grader and truck because
the validation split contains no annotated instances of these classes.

---

## Training Curves and Metrics

Key evidence includes:

- metrics/results.csv
- metrics/confusion_matrix.png
- metrics/confusion_matrix_normalized.png
- metrics/BoxPR_curve.png
- metrics/BoxF1_curve.png
- metrics/BoxP_curve.png
- metrics/BoxR_curve.png
- metrics/labels.jpg
- training_curves/results.png

---

## Unseen Image Evaluation

The trained model was tested on **25 completely unseen construction-site
images**.

### Results

- Images tested: 25
- Images with detections: 19
- Images without detections: 6
- Total detections: 50

### Detected Objects

| Class | Detections |
|---|---:|
| Excavator | 25 |
| Grader | 6 |
| Truck | 1 |
| Worker | 18 |

### Confidence Statistics

- Mean confidence: 0.601
- Median confidence: 0.545
- Minimum confidence: 0.253
- Maximum confidence: 0.982

Prediction evidence is included in:

unseen_evidence/

---

## Validation Inference Evidence

Predictions on the 28 validation images are included in:

validation_evidence/

---

## Error Analysis

Detailed error analysis is provided in:

error_analysis/error_analysis.md

Observed limitations include:

- missed detections
- low-confidence predictions
- small or distant workers
- partial occlusion
- unusual viewing angles
- low-light conditions
- class imbalance
- limited validation representation for grader and truck

---

## Governance and Licensing

Dataset governance, licensing information, responsible-use considerations,
and model limitations are documented in:

governance/GOVERNANCE.md

The dataset metadata identifies the source dataset license as:

*Creative Commons Attribution 4.0 International (CC BY 4.0)*

---

## Repository Structure

    .
    |-- README.md
    |-- requirements.txt
    |-- notebook/
    |-- metrics/
    |-- training_curves/
    |-- validation_evidence/
    |-- unseen_evidence/
    |-- error_analysis/
    |-- governance/
    `-- weights/

---

## Reproducing the Project in Google Colab

The intended reproducibility workflow is:

1. Open the project notebook in Google Colab.
2. Enable a GPU runtime.
3. Install the required dependencies.
4. Download the frozen dataset from the GitHub Release.
5. Extract the dataset.
6. Configure the dataset paths.
7. Train YOLOv8 for 50 epochs.
8. Evaluate the trained model.
9. Generate validation inference.
10. Run inference on new construction-site images.

The frozen dataset workflow does not require private credentials.

---

## Requirements

Main Python dependencies are listed in:

requirements.txt

Core dependencies:

- Ultralytics
- PyYAML

---

## Key Limitations

The dataset is relatively small and class-imbalanced.

The validation split contains no grader or truck annotations, which limits
class-specific validation for those categories.

Performance may also vary due to:

- lighting
- occlusion
- camera angle
- object scale
- image quality
- differences between construction sites

The model should therefore be treated as an educational computer-vision
prototype rather than a safety-critical construction monitoring system.

---

## Future Improvements

Potential improvements include:

- collecting additional construction-site images
- improving class balance
- adding grader and truck examples to validation
- increasing low-light and night imagery
- increasing examples of occluded objects
- testing larger YOLOv8 variants
- comparing different confidence thresholds
- expanding the dataset across different construction environments

---

## Project Summary

This project demonstrates an end-to-end computer-vision workflow for
construction-site object detection using YOLOv8.

The repository includes:

- frozen reproducible dataset
- YOLOv8 training workflow
- quantitative validation results
- training curves
- confusion matrices
- validation inference evidence
- unseen-image inference evidence
- error analysis
- governance and licensing documentation
- trained model weights

The repository is structured so that the experiment can be reviewed and
reproduced in Google Colab.
