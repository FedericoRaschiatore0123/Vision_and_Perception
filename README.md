# Emotion Recognition Project
## Description
This project focuses on the recognition of emotions in images implementing the PAtt-Lite(https://arxiv.org/pdf/2306.09626v1.pdf). The main goal is to develop a model capable of identifying human emotions, such as happiness, sadness, anger, etc., from input images.

## Project Structure
The project is organized into the following modules:

## Dataset:

We used the Dataset FER2013 that was built for emotion recognition tasks, this dataset is composed by 7 classe (1 for eadh emotion) labeled from 0 to 6, and another class that is used for testing. It also contain some tricky images for example some empty images.
## Preprocessing:

We apply som transformation to the dataset in particular a resize, a normalization and we also apply a orizontal roation and a random rotation in order to  teach to model to handle rotaion of the features.

## Model:

The model is composed by:
- A feature extraction that use MobileNetV2 to extract the feature from the input images, we truncated it in order to remove the fully connected layers
- A Patch extraction layer that reduce the dimensionlaity and split the feature maps into patches
- A ViT that use a MultiHead attention layer and a Fully Connected layer to classify the images in the corresponding emotion
  
## Implementation choices:
We decided to use PytorchLightning framework to simplify the code and make it more readable
For the Loss function we decided to use a CrossEntropy function
For the optimizer we used an Adam optimizer with a learning rate of 1e-4
For the Batch size we decided to use 128 because after a lot of tests seems to be the one with the best performance
We decided to use 8 heads for our ViT

## Test:

To Test the model you have to:

Install all the dependencies (pytorch_lightning, einops, ...)
Import the Dataset from the zip files on our github

## Results:

We trained the model for 15 epochs and obtain the following result:
Accuracy on validation: 72%
Accuracy on test: 64%

Due to the limitations of google Colab we couldn't train it for more epochs but probably the model will achive the performance of the SOTA.
