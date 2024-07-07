# Animal Image Classification

This repository contains the implementation of a neural network model for classifying animal images. The dataset includes four classes: "bear", "elephant", "leopard", and "zebra". The primary goal is to improve upon a baseline model through experimentation with different architectures, hyperparameters, and techniques such as transfer learning, data augmentation, and regularization.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Baseline Model](#baseline-model)
- [Controlled Experiments](#controlled-experiments)
- [Proposed Models](#proposed-models)
- [Repeatability](#repeatability)
- [Requirements](#requirements)
- [Results](#results)
- [Contributors](#contributors)
- [License](#license)

## Project Overview

The objective of this project is to develop and refine a neural network model for classifying animal images into four distinct classes. The approach involves starting with a baseline model and iteratively improving it through controlled experiments.

## Dataset

The dataset used in this project is contained in `animal-dataset.zip` and includes labeled images of bears, elephants, leopards, and zebras.

## Baseline Model

We begin with a baseline model comprising an initial neural network architecture and a set of hyperparameters. This model serves as the starting point for further improvements.

## Controlled Experiments

To enhance the baseline model, various controlled experiments are conducted. Each experiment modifies the baseline model in one of the following ways:

- **Transfer Learning**: Utilizing pre-trained models (mandatory).
- **Different Architectures**: Trying out alternative neural network architectures.
- **Data Augmentation**: Applying data augmentation techniques.
- **Regularization**: Implementing regularization methods to prevent overfitting.
- **Hyperparameter Tuning**: Adjusting hyperparameters such as learning rate, batch size, and number of layers.
- **Other Modifications**: Exploring additional changes that might improve performance.

Each candidate model is trained for the same number of epochs, and the results are compared by plotting training and validation losses. Findings and comments are shared for each modification.

## Proposed Models

Based on the results of controlled experiments, new models are proposed. These models may combine multiple successful modifications, such as combining transfer learning with data augmentation. The proposed models are trained, and the results are compared with previous models. Final evaluations and conclusions are summarized.

## Repeatability

To ensure reproducibility, the following practices are implemented:

- **Setting Random Seeds**: Initializing random number generator seeds for all randomness modules used.
- **Environment Reproducibility**: Specifying the versions of all dependencies.
- **Deterministic Processes**: Avoiding processes reliant on external factors, such as operating system or computation power.

## Requirements

To run the code in this repository, you need the following dependencies:

- Python 3.x
- TensorFlow
- NumPy
- Matplotlib

## Results

The results of the experiments and proposed models are documented within the notebook, including plots of training and validation losses, and final evaluation metrics.

## Contributors

- Muhammed Efe İncir

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
