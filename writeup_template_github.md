#**Traffic Sign Recognition** 

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/OriginalAug.jpg "Random Noise"
[image9]: ./examples/CNN_Architechture.jpg "Model Architecture"


###Writeup / README

####1. Project code: here is a link to my [project code](https://github.com/Kloud23/Traffic_sign_classification/blob/master/Traffic_Sign_Classifier.ipynb)

###Data Set Summary & Exploration

####1. Providing basic summary of the data set.

I used the numpy library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

####2. Exploratory visualization of the dataset.

Following is a bar chart showing how the data is distributed across classes.

![alt text][image1]

###Designing and Testing a Model Architecture

####1. The pre-processing steps and methods used.

As a first step, I decided to convert the images to grayscale because of the following:
1. To get rid of the illumination effects on images
2. To make the CNN not learn color as a decisive factor for sign classifier
3. To optimize the resource requirements for training and running the algorithm

Here is an example of a traffic sign image before and after grayscaling. No other pre-processing was used.

![alt text][image2]

After that, I generated more training images by using opencv functions. 

I warped the images and then added rotated images. I randomly picked up degrees of rotation from -20 to 20 degrees for directional signs. I used smaller degree rotations for directional signs as rotating these images more would have changed their meaning. For all other images, I picked up degrees of rotation randomly from -35 to 35 degrees. This way, I augmented the data and also balanced the data across classes. I augmented the data for each class so that at the end of augmentation process, I had approximately 2500 images for each class. The final count of training examples after augmentation was 107499.

I included rotation and warping for augmenting the images so as to improve the generalization on the CNN that was trained.

####2. Train, test and cross-validation data sets.

To cross validate my model, I randomly split the training data into a training set and validation set.

My final training set had 34799 number of images. My validation set and test set had 4410 and 12630 number of images.

The sixth code cell of the IPython notebook contains the code for augmenting the data set. I decided to generate additional data because the dataset was not balanced across all the unique classes. To add more data to the the data set, I used the following techniques because in real life these conditions would have come up for a real-life traffic classifier algorithm.


Here is an example of an original image and an augmented image:

![alt text][image3]


####3.Model architecture design 

My final model architecture, which appears in the code as a function names TrafficNet, looked like following:

![alt text][image9]
