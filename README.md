# ISIC 2017 Lesion Classification

## Background
This project is my first attempt at [ISIC 2017: Skin Lesion Analysis Towards Melanoma Detection](https://challenge.kitware.com/#phase/5840f53ccad3a51cc66c8dab)

The challenge involves classification tasks on the following skin lesions:
* Melanoma – malignant skin tumor, derived from melanocytes (melanocytic)
* Nevus – benign skin tumor, derived from melanocytes (melanocytic)
* Seborrheic keratosis – benign skin tumor, derived from keratinocytes (non-melanocytic)

The two independent binary classification tasks are as follows:
1. Melanoma vs Nevus and Seborrheic keratosis
2. Seborrheic keratosis vs Melanoma and Nevus

## Setup & Installation
Follow [Fast.ai's guide](https://course.fast.ai/start_gcp.html) to set up a Google Cloud Platform (GCP) instance to run the notebooks in the repo.

Get the training, validation, and test data from [Udacity's repo](https://github.com/udacity/dermatologist-ai).

## Data Preparation
Run `create_normalized_dataset.ipynb` to normalize the dataset using a color constancy algorithm called Shades of Gray.

It assumes that your original dataset is organized as follows:
```bash
data/
├── models
├── test
│   ├── melanoma
│   ├── nevus
│   └── seborrheic_keratosis
├── train
│   ├── melanoma
│   ├── nevus
│   └── seborrheic_keratosis
└── valid
    ├── melanoma
    ├── nevus
    └── seborrheic_keratosis
```
and a directory called `modified_data` exists in the parent directory of `data`.

## Training & Evaluation
Run `isic_2017_lesion_classification.ipynb` to train and evaluate the CNN which is a modified pre-trained ResNet-152.

Submissions to the competition are evaluated by ROC AUC for:
* Melanoma classification
* Seborrheic keratosis classification
* Melanoma and seborrheic keratosis classifications combined (mean value)

My results are as follows:
* Melanoma classification: 0.75
* Seborrheic keratosis classification: 0.83
* Mean value: 0.79
