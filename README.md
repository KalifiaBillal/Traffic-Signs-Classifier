# **Traffic Sign Classifier** 

## Writeup report


---

**Build a Traffic Sign Recognition Project**

The goals/steps of this project are the following:
* Load the data set (see below for links to the project dataset)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./report_images/classes_images1.JPG 
[image2]: ./report_images/classes_images2.JPG "Classes visualization"
[image3]: ./report_images/data_analysis.JPG "Number of samples per class"
[image4]: ./report_images/processed_image.JPG "Processed image"
[image5]: ./report_images/network_architecture.jpg "Network architecture"
[image6]: ./report_images/30-sign.jpg "Traffic Sign 1"
[image7]: ./report_images/yield_sign.jpg "Traffic Sign 2"
[image8]: ./report_images/STOP_sign.jpg "Traffic Sign 3"
[image9]: ./report_images/bumpy_road_sign.jpg "Traffic Sign 4"
[image10]: ./report_images/no_entry.jpg "Traffic Sign 5"
[image11]: ./report_images/results.JPG "Predictions"


---
## Writeup / README

You're reading it! and here is a link to my [project code](https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)

### Data Set Summary & Exploration

#### 1. Data analysis:

I used the pandas library to calculate summary statistics of the traffic signs dataset:

* The size of the training set is 43799
* The size of the validation set is 4410
* The size of the test set is 12630
* The shape of a traffic sign image is 32x32x3
* The number of unique classes/labels in the data set is 43

#### 2. Exploratory visualization of the dataset:

Here is an exploratory visualization of the data set. First, I visualized all the classes of the German traffic signs by plotting a random
image from the training set for each class with its label. The image below shows some
of them : 

![alt text][image1]
![alt text][image2]

Then, I plotted a horizontal bar chart showing the number of counts of each sign in
the training set:

![alt text][image3]


### Design and Test a Model Architecture

#### 1. Image processing:

As a first step, I decided to apply a histogram equalization to the images to enhance
the contrast.
Here is an example of a traffic sign image before and after histogram equalization:

![alt text][image4]

Then, I normalized the image data because it enhances the performance of
the training.



#### 2. Model architecture:

My final model consisted of the following layers (each convolution is followed by a RELU activation):

 ![alt text][image5]


#### 3. Model training:

To train the model, I used an Adam Optimizer, with a learning rate equal to 0.001 on
a batch of 128 samples and repeated the training for 15 epochs. 

I also enhanced the performance by dividing the learning rate by 5 each time the accuracy decreased between two consecutive epochs. 

#### 4. Description the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93:

My final model results were:
* training set accuracy not computed
* validation set accuracy of 98.6% 
* test set accuracy of 96.7%

The first architecture used was Lenet5. The accuracy was about 89%. I modified the
network by first trying with grayscale images as input and with tanh activation
functions but the accuracy did not reach the 93%. 

After that, I changed the depths and sizes of the layers. It was a trial and error method. Then I added a dropout before the last layer and divided the learning rate by half each time the accuracy decreased to
achieve the desired accuracy. 

The most important design choice that enhanced the accuracy was the dropout, but it
can be enhanced more by also augmenting the data. 
 

### Testing the Model on New Images

#### 1. Choosing five German traffic signs found on the web :

Here are five German traffic signs that I found on the web:

![alt text][image6] ![alt text][image7] ![alt text][image8] 
![alt text][image9] ![alt text][image10]

I cropped the images, resized and preprocessed them in the same way I did for the
training, validation and test sets.

#### 2. Discussion of the model's predictions on these new traffic signs and comparison of the results to predicting on the test set:

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Speed Limit 30 Km/h 	| Speed Limit 30 Km/h 							| 
| Yield     			| Yield 										|
| STOP sign				| STOP sign										|
| Bumpy Road      		| Bumpy Road					 				|
| No entry				| No entry		      							|

![alt text][image11]

The model was able to correctly guess all the traffic signs, which gives an accuracy of
100%. This compares favorably to the accuracy of the test set of 96.7%.

