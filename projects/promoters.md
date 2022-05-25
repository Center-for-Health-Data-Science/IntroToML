
* Prediction of transcription start sites

Use the data set and some of the code from the notebook TSSprediction.ipynb from day 2 of the course.

Try to make a better neural network by varying the architecture. For instance
* Vary the input window size
* Use one more convolution layer
* Use more hidden layers and vary their sizes
* Use softplus activation instead of ReLU
* Try variyng the weight decay and learning rate in Adam

Each group member can try different ideas.

Evaluate the best model by for instance:
* Predict TSS along complete sequences in a test set and plot the number (or fraction) of predictions at each position (-1000 to + 1000) -- are the predicted sites clustered around the true TSS or are they randomly scattered?
* Visualize predictions on some sequences of the test set
* Test model in other genomic regions (requires you to get additional data).



