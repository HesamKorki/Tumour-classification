# Tumour-classification
Training a neural network to classify tumours based on medical pictures using semantic segmentation and U-net network model.

## Semantic Segmentation

So far, we evaluated different segmentation methods based on detecting similarities such as region growing and thresholding.
In this section, I want to challenge myself by implementing a Convolutional Neural Network (CNN) algorithm to segment brain tumors using a deep learning method.

## Dataset

The dataset I will be using contains brain MR images together with manual FLAIR abnormality segmentation masks obtained from The Cancer Imaging Archive (TCIA).
Images correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR)
sequence and genomic cluster data available.
Data source: [The Cancer Imagin Archrive](https://wiki.cancerimagingarchive.net/display/Public/TCGA-LGG#6abaca285cee4c9cac59b0bcff944658)

## Dependencies

In this project, I will be using the following libraries implemented by python:

- Tensorflow
- Keras
- Pillow
- tqdm
- Numpy
- scikit-learn
- Matplotlib

## Network Structure (CNN)

The general structure of the network is a U-net that consists of an encoder and a decoder. There are 9 main layer each of which include 2 3-by-3 convolution with same padding separated by a relu layer in between and a max pooling filter at the end.
There are 2-by-2 and 1-by-1 convolution layers in the second half of the network.

## Loading Data

The dataset has images with masks in different folders. Masks have the same name as images plus a "_mask" string.
First, I remove the useless files and save images and masks in 2 different directories. We have images and masks in 2 different directories temp_image_path, and temp_mask_path.
In this part, we will check that if there are images without masks, and if there are, delete them. we shuffle images and masks with the same seed value to have them parallel to each other in two directories, then split them into three groups.
I will rotate, scale, crop and augment images using modifiable functions to both create more data and account for diversity in data. 

## Train and Predict

Next, I compile the model and see the summary of parameters in each layer. I used dice coefficient as the loss function which evaluates the semantic segmentation accuracy.
Then, using our data and the model we would train our system to identify the faulty tumours in brain images. Pictures of predictions of our system on test data are available in the notebook.
