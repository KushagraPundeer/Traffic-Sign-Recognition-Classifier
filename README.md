# Traffic-Sign-Recognition-Classifier

# Goals / Steps for this Project
1. Load the dataset (link)
2. Explore, Summarize, and visualize the dataset
3. Design, Train, and test a model architecture
4. Use the model to make predictions on new images
5. Analyze the softmax probabilities of the new image

# Model Architecture

1. Preprocessing Data

As a first step, I decided to convert the images to grayscale as it helps the model run faster when trained with grayscale conversion.

2. Final Model Architecture

My final model consisted of the following layers.

Modified LeNet architecture

Layer               Description

Input               32 x 32 x 1 Grayscale image
Convolutional       Output = 10 x 10 x 16
Fully Connected     Input = 400, Output = 120
Fully Connected     Input = 120, Output = 84 (Used Dropout)

3. Model Parameters
To train the model, I used Adam Optimizer with learning rate of 0.04

Hyperparameters - 

Epochs = 22 (Approximate epochs neeeded)
BATCH_SIZE = 128 (Chosen based on sytem)

4. Final Results

Validation set accuracy of 0.93
Test set accuracy of 0.89
