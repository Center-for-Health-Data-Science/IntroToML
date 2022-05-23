# Day 2

## 09-10 

## 10-11 Pytorch Intro
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Center-for-Health-Data-Science/IntroToML/blob/HEAD/Day2/pytorch_intro.ipynb)

The notebook is in support of a presentation, not the replacement (so I do not write out everything)

- Torch seen as numpy: `Ndarray` -> `Tensor`
	- Why: Tensor itself has backprop information
- Key Concepts and associated Classes: 
    - brief recap of python concepts needed: `tuple`, `[ ]` implementation, `len`
    - `DataSet` -> `__getitem__`, `__len__`
    - `DataLoader` -> Loop over `Dataset` in certain ways
    - Model formulation -> `Module`
    - Optimizers -> `SGD`
    - loss functions 

- plan:
    * Start by makig dataloaders for validaiton + training. Simple exercise
    * Define a simple linear regression, then a feed-forward network
    * Do one step with `Dataloder` + model and see what comes out
    * Do it a loop

- options: How to formulate a Logistic Regression?


### Further material
The Colab I found before: Primer on NNs, (or this one?), cheat-cheets (and as a notebook)

- pytorch.org Cheat Sheet on tensor, or examples from some blog (lost source) in [tensor_cheatsheet.ipynb](tensor_cheatsheet.ipynb)


- notebook on [classes](https://github.com/Center-for-Health-Data-Science/PythonTsunami/tree/fall2021/Classes)

- a [primer tutorial](https://github.com/sweetpand/PyTorch_fun/blob/master/pytorch_primer.ipynb) for PyTorch
- simple [toy example](https://github.com/deep-learning-with-pytorch/dlwpt-code/blob/master/p1ch6/1_neural_networks.ipynb) for a Linear Regression from Deep Learning with Pytorch book