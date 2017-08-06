#**Traffic Sign Recognition** 

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report



###Data Set Summary & Exploration

####1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used two simple visualization mechanism, firstly displaying each image per category, to learn the data.
Second - I create an histogram of how many images per class do we get in the training, validation and test data set.
Few things to learn from it - we have only 43 categories of classes, they are not represented evenly in the data set, and it's evident some images are rather dark. The good side - the distribution of classes is the same in the training, validating and test data sets.

Design and Test a Model Architecture

####1. 

PreProcessing:
  Firstly I preproccessed the data into grayscale images, using min_max scaling and normalized to have a mean of 0, this should help the   optimizer to converge better.
  The suggested normalization in the notebook didn't work well for me.


Architecture:
  Built upon the LeNet architecture, added 2 more FC layers to make the layer deeper.
  Added filters to try and capture more information and generalize better. 
  Added dropout layers inbetween exisiting layers to avoid overfitting.


HyperParameters:
  Increased the number of epochs to allow for better converngence 
  Use different dropoutrate for the Conv layers and the FC layers, with the belief the FC layers can have lower keep rate.

####2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 GrayScale image   							| 
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 28x28x16 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x16 				|
| Dropout	      	| keep_rate 0.9				|
| Convolution 5x5	    |  1x1 stride, valid padding, outputs 10x10x25      									|
| RELU		|         									|
| Max pooling					| 2x2 stride,  outputs 5x5x25         									|
| Dropout	      	| keep_rate 0.9				|
|		FC				|					Input = 625. Output = 360							|
|		RELU			|												|
| Dropout	      	| keep_rate 0.85				|
|		FC				|					Input = 360. Output = 240							|
|		RELU			|												|
| Dropout	      	| keep_rate 0.85				|
|		FC				|					Input = 240. Output = 120							|
|		RELU			|												|
| Dropout	      	| keep_rate 0.85				|
|		FC				|					Input = 120. Output = 43							|
|		RELU			|												|
| Dropout	      	| keep_rate 0.85				|
| Softmax	      	|			|
 


####3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

I used the same training and optimizer as the LetNet lab. Decreased the batch size by half and increase the epochs to 35. 

####4.
Getting to more the 0.93 is an iterative process.
Started with preprocessing, going deeper in layer depth and increasing the number of filters.
The first simpler preprocessing didn't work for me, so I've chose to convert the rgb to grayscale.
Adding dropout and changing the hyperparameters to more epochs seems to have made it better.

Few future things that can help - is increase conv layers depth and going perhaps to a 3x3 filter. Also generating more data, and in more angles and intensities should help significantly. 

####5.
The model was tested on 5 new images.


