# Governance and Licensing

## Dataset Source

The dataset used in this project was obtained from Roboflow Universe.

Dataset:
Construction Site Object Detection

Roboflow dataset version:
Version 1

Dataset format:
YOLOv8 Object Detection

The frozen dataset used for this experiment is also published as a
GitHub Release asset so that the notebook can be reproduced without
requiring a Roboflow API key or private credentials.


## License

According to the metadata supplied with the exported dataset, the dataset
is licensed under:

Creative Commons Attribution 4.0 International (CC BY 4.0)

Users of the dataset should comply with the attribution requirements of
the original dataset license.


## Reproducibility

The project uses a frozen dataset snapshot hosted as a public GitHub
Release asset.

This approach ensures that:

- no Roboflow API key is required
- no private credentials are required
- the exact dataset version used for training can be retrieved
- a third party can reproduce the notebook in a fresh Google Colab session


## Data Governance Considerations

The dataset contains construction-site imagery including:

- workers
- excavators
- graders
- trucks

Because construction-site images may contain identifiable individuals,
vehicles, equipment, or project information, the dataset should be used
responsibly and only for legitimate educational, research, or approved
project purposes.

The object-detection model should not be treated as a safety-critical
decision system without additional validation.


## Model Limitations

The training and validation data are limited in size and class balance.

In particular, the validation set contains no annotated grader or truck
instances. Therefore, the available validation results cannot establish
reliable performance for those classes.

Predictions may also be affected by:

- lighting conditions
- occlusion
- viewing angle
- object distance
- image quality
- class imbalance


## Human Oversight

Model predictions should be reviewed by a human when used in practical
construction workflows.

The model is intended as a computer-vision demonstration and should not
replace professional judgement, site supervision, or established safety
procedures.


## Model and Software

The project uses the Ultralytics YOLOv8 object-detection framework.

The repository should document the software dependencies required to
reproduce the training and inference workflow.


## Reproducibility Principle

A third party should be able to:

1. Open the notebook in Google Colab.
2. Install the required Python packages.
3. Download the frozen dataset from the public GitHub Release.
4. Train the YOLOv8 model.
5. Evaluate the model.
6. Reproduce validation predictions.
7. Run inference on new images.

No private API credentials are required for the frozen dataset workflow.