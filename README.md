# Gesture-Recognition

## Problem Statement
Imagine you are working as a data scientist at a home electronics company which manufactures state of the art smart televisions. You want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote.

The gestures are continuously monitored by the webcam mounted on the TV. Each video is a sequence of 30 frames (or images). Each gesture corresponds to a specific command:
<ol>
<li>Thumbs up:  Increase the volume
<li>Thumbs down: Decrease the volume
<li>Left swipe: 'Jump' backwards 10 seconds
<li>Right swipe: 'Jump' forward 10 seconds  
<li>Stop: Pause the movie
</ol>

## Solution

For analysing videos using neural networks, two types of architectures are used commonly. One is the standard CNN + RNN architecture in which you pass the images of a video through a CNN which extracts a feature vector for each image, and then pass the sequence of these feature vectors through an RNN.

The other popular architecture used to process videos is a natural extension of CNNs - a 3D convolutional network. In this project, we will try both these architectures.

Code: https://github.com/mrm1404/Gesture-Recognition/blob/main/Gesture_Recognition.ipynb

## Expriment Details:
### 1. Conv 3D without BN
#### Details: 
<ul>
<li> 1 Conv3D 3 x 3 kernel filter with Dropout and without Batch Normalization
<li> 1 Fully Connected Dense Layer 
<li> No of Image Indexes Used: 5
<li> Image Dimensions: 120 x 160
<li> Batch Size: 10
<li> Epochs : 20	
</ul>

#### Result: 
Validation Accuracy drops significantly compared to Training Accuracy

#### Explanation: 
Best Training Accuracy is 0.9969 and Validation Accuracy is 0.7800	There is overfitting.

### 2. Conv 3D with BN
#### Details:
<ul>
<li> 2 Conv3D 3x3 kernel filter with Batch Normalization
<li> 1 Fully Connected Dense Layer
<li> No of Image Indexes Used: 10 
<li> Image Dimensions: 120 x 160
<li> Epochs: 20
</ul>

#### Result: 
Training Accuracy: 0.9834 Validation Accuracy:0.8600

#### Explanation: 
Model is having good training accuracy and validation accuracy.

### 3. Conv 2D with GRU
#### Details:
<ul>
<li> 2 Conv 2D TimeDistributed layer with Batch Normalization
<li> 1 GRU layer
<li> Image Dimensions: 120 x 160
<li> No of Image Indexes Used: 10 
<li> Epochs: 20
</ul>

#### Result: 
Training Accuracy: 0.4555 Validation Accuracy: 0.2800

#### Explanation: 
The loss function of this images is not getting minimized using the GRU layer.

### 4. Conv 3D with Conv LSTM 2D
#### Details:
<ul>
<li> 1 Conv3D 3x 3 kernel filter with Batch Normalization
<li> 1 Conv LSTM2D 3 x 3 kernel filter
<li> 1 Fully Connected Dense Layer
<li> Image Dimensions: 120 x 160
<li> No of Image Indexes Used: 10 
<li> Epochs: 20
<ul>

#### Result: 
Training Accuracy: 0.9532 Validation Accuracy: 0.8000

#### Explanation: 
This Model has good accuracy on train and test images. 

### Decision
Experiment 2 Conv 3D layers with Batch Normalization has the best training and validation accuracy. Hence this model seems the best fit
