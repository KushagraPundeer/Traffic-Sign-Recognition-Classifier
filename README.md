# **Traffic Sign Recognition** 

## Writeup

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

[image1]: visualization1.jpg "Visualization"
[image2]: grayscale.jpg "Grayscaling"
[image3]: random_noise.jpg "Random Noise"
[image4]: 1.jpg "Traffic Sign 1"
[image5]: 2.jpg "Traffic Sign 2"
[image6]: 3.jpg "Traffic Sign 3"
[image7]: 4.jpg "Traffic Sign 4"
[image8]: 5.jpg "Traffic Sign 5"
[image2]: visualization2.jpg "Visualization"
[image3]: visualization3.jpg "Visualization"


---
### Writeup / README

### Data Set Summary & Exploration

I began by downloading the dataset into the project folder. The pickled loaded data is then used to form training, testing and validation data. Next I calculated the no. of training examples, no. of testing examples, Image datashape and the no. of classes. This gives the basic summary of the dataset.

Twenty images were randomly chosen from the dataset and plotted using matlabplotlib. To visulaize the dataset I used Histograms to show distribution over training, testing and validation data. Now that the data is preprocessed, Image is converted to grayscale and normalized. Grayscale conversions make the model faster over the large datasets.

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is  (34799, 32, 32, 3)
* The size of the validation set is (4410, 32, 32, 3)
* The size of test set is (12630, 32, 32, 32, 3)
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data is distributed for training, testing and validation.

![alt text][image1]

### Design and Test a Model Architecture

1. Preprocessing Data

As a first step, I decided to convert the images to grayscale as it helps the model run faster when trained with grayscale conversion.

Here is an example of a traffic sign image before and after grayscaling.

![alt text][image2]

As a last step, I normalized grayscale image between probabilites 0.1 and 0.9


#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

Modified LeNet architecture

| Layer         		    |     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		    | 32x32x3 Grayscale image   							
| Convolution         	| Output =  10 x 10 x 16	
| Fully connected		    | Input = 400, Output = 120     
| Fully connected		    | Input = 120, Output = 84 (Used Dropout)
| Fully connected		    | Input = 84, Output = 43 
 

#### 3. Hyperparamenters, 

To train the model, I used Adam Optimizer with learning rate of 0.04

Hyperparameters - 

Epochs = 22 (Approximate epochs neeeded)
BATCH_SIZE = 128 (Chosen based on sytem)

#### 4. Results

My final model results were:
* validation set accuracy of 0.934
* test set accuracy of 0.89
 

### Test a Model on New Images

#### 1. 

Here are five German traffic signs that I found on the web:

![alt text | 500x300, 20%][image4] ![alt text][image5] ![alt text][image6] 
![alt text][image7] ![alt text][image8]

Image 1 might be difficult to classify because it looks old. Color of the ambulance has poor contrast to the white on the sign. Image 2 is slightly blurred, with some small scuff showing wear. Image 5 has both construction and child crossing. This is an interesting example as the image has two traffic signs. It recognizes the child crossing correctly. I reran the network a few times to check if it was a random selection, but the classifier picks child every time. The contruction sign appears to have some shadow and bright areas and hence not as uniform in contrast.

#### 2. Discuss the model's predictions on these new traffic signs.

Accuracy was 100%, but it was only on 5 new test images. With larger new test set accuracy can be established more accurately.

Here are the results of the prediction:

| Image			            |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| No Entry     	      	| 		No Entry							
| General Caution     	|     General Caution							
| Roundabout mandatory	|     Roundabout Mandatory				
| Turn Right Ahead 		  |     Turn Right Ahead				 			
| Children Crossing			|     Children Crossing   		| Correct for the bottom sign. Pretty Good considering two signs




The model was able to correctly guess 5 of the 5 traffic signs, which gives an accuracy of 100%. This compares favorably to the accuracy on the test set of 0.89

#### 3 Top 5 softmax probabilities for each image along with the sign type of each probability. 

The top five soft max probabilities were

Image - 1

| Probability         	|     Prediction  Class    					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00e0         			  | 17 - No Entry   									
| 8.64e-22   				    | 40							
| 3.59e-22					    | 1									
| 2.14e-22	      			| 21 			
| 5.34e-30				      | 12   						


Image - 2

| Probability         	|     Prediction	Class      				| 
|:---------------------:|:---------------------------------------------:| 
| 1.00e0         			  | 18 General Caution								
| 5.79e-21   				    | 27							
| 8.71e-28					    | 11										
| 5.80e-28	      			| 12
| 2.32e-28				      | 1

Image - 3


| Probability         	|     Prediction	Class      	  		| 
|:---------------------:|:-------------------------------------------:| 
| 9.99e-01         			| 40 Roundabout Mandatory							
| 3.88e-04   				    | 11
| 4.60e-05					    | 7									
| 2.34e-05	      			| 28
| 7.85e-07				      | 16

Image - 4

| Probability         	|     Prediction	Class        			| 
|:---------------------:|:---------------------------------------------:| 
| 9.98e-01         			| 33 Turn Right ahead								
| 1.42e-04   				    | 3							
| 2.80e-05					    | 5										
| 9.23e-05	      			| 1
| 2.43e-07				      | 2


Image - 5

| Probability         	|     Prediction	Class      				| 
|:---------------------:|:---------------------------------------------:| 
| 0.25        			    | 28	Children Crossing					
| 0.12   				        | 12						
| 0.09					        | 11									
| 0.07	      			    | 40
| 0.06      			      | 32
