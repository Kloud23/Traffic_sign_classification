#**Traffic Sign Recognition** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/OriginalAug.jpg "Random Noise"
[image9]: ./examples/CNN_Architechture.jpg "Model Architecture"


###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my [project code](https://github.com/Kloud23/Traffic_sign_classfication/blob/master/Traffic_Sign_Classifier.ipynb)

###Data Set Summary & Exploration

####1. Provide a basic summary of the data set and identify where in your code the summary was done. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

The code for this step is contained in the second code cell of the IPython notebook.  

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

####2. Include an exploratory visualization of the dataset and identify where the code is in your code file.

The code for this step is contained in the third code cell of the IPython notebook.  

Here is an exploratory visualization of the data set. It is a bar chart showing how the data is distributed across classes.

![alt text][image1]

###Design and Test a Model Architecture

####1. Describe how, and identify where in your code, you preprocessed the image data. What tecniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc.

The code for this step is contained in the fourth code cell of the IPython notebook.

As a first step, I decided to convert the images to grayscale because of the following:
1. To get rid of the illumination effects on images
2. To make the CNN not learn color as a decisive factor for sign classifier
3. To optimize the resource requirements for training and running the algorithm

Here is an example of a traffic sign image before and after grayscaling. No other pre-processing was used.

![alt text][image2]

After that, I generated more training images by using opencv functions. 

I warped the images and then added rotated images. I randomly picked up degrees of rotation from -20 to 20 degrees for directional signs. I used smaller degree rotations for directional signs as rotating these images more would have changed their meaning. For all other images, I picked up degrees of rotation randomly from -35 to 35 degrees. This way, I augmented the data and also balanced the data across classes. I augmented the data for each class so that at the end of augmentation process, I had approximately 2500 images for each class. The final count of training examples after augmentation was 107499.

I included rotation and warping for augmenting the images so as to improve the generalization on the CNN that was trained.

####2. Describe how, and identify where in your code, you set up training, validation and testing data. How much data was in each set? Explain what techniques were used to split the data into these sets. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, identify where in your code, and provide example images of the additional data)

The code for splitting the data into training and validation sets is contained in the fifth code cell of the IPython notebook.  

To cross validate my model, I randomly split the training data into a training set and validation set.

My final training set had 34799 number of images. My validation set and test set had 4410 and 12630 number of images.

The sixth code cell of the IPython notebook contains the code for augmenting the data set. I decided to generate additional data because the dataset was not balanced across all the unique classes. To add more data to the the data set, I used the following techniques because in real life these conditions would have come up for a real-life traffic classifier algorithm.


Here is an example of an original image and an augmented image:

![alt text][image3]


####3. Describe, and identify where in your code, what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

The code for my final model is located in the twentieth cell of the ipython notebook. 

My final model architecture looked like following:

![alt text][image9]