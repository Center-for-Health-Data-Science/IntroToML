# Predicting cancer from images

## The data

The PatchCamelyon (PCam) dataset is a benchmark set for medical image classification. The original dataset consists of 327.680 color images (96 x 96px) derived from histopathological scans of lymph node sections. Images are labelled with [0,1] referring to the presence of metastatic tissue. Below you can see examples from PCam.


<img src="https://github.com/Center-for-Health-Data-Science/IntroToML/blob/main/projects/histopathology_images/pcam.jpeg" width="800">

This figure and the data are taken from  [this repo](https://github.com/basveeling/pcam) and shows example images from PCam, with green boxes showing tumor tissue which gives a label of 1.

We provide a subset of this data, comprising 5% of the original data in a train-validation-test split. The training data now consists of 13108 images and both validation and test set contain 1639 images. Don't expect the model performances to be great with this small dataset, but it is a nice way to get started. You could always go to the full dataset and try out your model on that. Because image data can be challenging to get started with, we also provide the Dataset class with how to load the data in the starter notebook [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Center-for-Health-Data-Science/IntroToML/blob/HEAD/projects/histopathology_images/pcam_start.ipynb).

## The task

You are free to do whatever you want with this data, as long as it has something to do with training and evaluating a neural network. We have collected some ideas to give you an inspiration of what COULD be done.

### - build a fully-connected and or convolutional classifier
For a fully-connected classifier, you have already seen some examples in the introduction to PyTorch and in the first exercise. Maybe start with something simple like this, try out training and set up some evaluation and feel free to come back to more advanced architectures later.

### - optimize hyperparameters of your model and choose the best one based on the validation performance
These could be the number of hidden layers, the width of the hidden layers (if fully-connected), stride and kernel size (if convolutional), batch size, learning rate and so on.
Tip: For the sake of efficiency, it can be helpful to do this on a subset of the training set.

### - train your selected classifier and evaluate it on the heldout test set
We usually (and ideally) have a training set from which the model parameters are estimated. In order to select the best architectures and other hyperparameters, we need to evaluate the trained models. For this we use the validation set. Afterwards, we would like to evaluate the model (maybe in comparison to other approaches) based on some unseen data from the same distribution. We have an extra so-called test set for that, because we have to assume that the model may be biased towards the validation set.

### - find suitable performance metrics for evaluating your model
You might want to consider the applications of such a model and what kind of trade-off you are willing to make in terms of diagnosis. I thought [this website](https://neptune.ai/blog/evaluation-metrics-binary-classification) was very handy.

### - set up a baseline for comparison to see whether it makes sense to use NNs for this classification task
A suitable baseline would for example be logistic regression.

### - Can you improve model performance through data augmentation?
So far your models have been trained and tested on this benchmark dataset in which the metastatic tissues are found in a certain centered window. Now what happens if new data is at a different resolution or does not center the tumor tissue? There is sadly no ground-truth test set in this benchmark for this, but we can at least check out the test performance when trained on augmented data. What does augmented mean? Data augmentation refers to performing transformations on the data. If we think about the cat example in our lecture of day 2, we can think of these being for example shifting the image around, cropping or flipping it. You can check out the [documentation](https://pytorch.org/vision/stable/transforms.html) on this and see if you find some useful transformations to try out.

### Very advanced options for the future (if you are still interested in ML)

There are some really interesting things we can do that have been made pretty easy. Hyperparameter optimization for example can now basically be automated. If you are interested in this, you might want to check out optimization frameworks such as [optuna](https://optuna.readthedocs.io/en/stable/index.html).

Another thing that is really interesting and extremely valuable is a field called explainable AI, which is especially important in applications to medical decision making. We will most likely only trust algorithms to help in our decision making if we understand how they make their decisions. If you are interested in this, I have some code implementing [RISE](https://arxiv.org/abs/1806.07421) for pcam if you want to see what information your model uses in its predictions [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Center-for-Health-Data-Science/IntroToML/blob/HEAD/projects/histopathology_images/pcam_rise_explainable_ai.ipynb).