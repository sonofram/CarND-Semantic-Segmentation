# Semantic Segmentation
### Introduction

## Architecture: 

In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

Semantic segmentation was implemented using FCN architecture provided in https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf. This model takes pre-trained VGG16
model and fully connected layer is discarded and replaced with 1x1 convolution layer. Entire architect can be categorized two section "encoder" and "decoders"

1x1 layer is followed by decoder section with Upsampling and skip layers. Upsampling retains size back to original image using bilinear interpolation. However, due to pooling layers loosing some spacial information upsampling will return coarse image. Therefore, by merging previous layers(encoders) with upsample layers provides image very close to original image.
Now, every pixel is classified as "identified object"(Road in this case) and "background". This classified information overlayed on the actual image and ROAD is marked in green.


## Training

The hyperparameters used for training are:
* keep_prob: 0.5 (in training) and 1.0 in prediction
* learning_rate: 0.0005
* epochs: 50
* batch_size: 10




Predicted images:

[//]: # (Image References)

[image1]: ./umm_000041.png "image1"
[image2]: ./um_000005.png "image2"
[image3]: ./um_000018.png "image3"
[image4]: ./um_000063.png "image4"
[image5]: ./uu_000093.png "image5"
[image6]: ./umm_000046.png "image6"


![image1][image1]	![image2][image2]

![image3][image3]	![image4][image4]

![image5][image5]	![image6][image6]


## What can be done better

1. There are two class of networks that are used in semantic segmentations. This project uses FCN(Fully convolution network) was introduced in 2014. Second class is called dilated/atrous convolutions. 
   FCN scored 59.9 in leader board(http://host.robots.ox.ac.uk:8080/leaderboard/displaylb.php?challengeid=11&compid=6#KEY_SegNet). There are new algorithms available that can be tested in autonomous driving domain. Eg.
	1. RefineNet (leader board score: 84.2)
	2. Deeplab V3 (leader board score: 85.7)
	
## Future work in this project(comming soon...)

1. Implement Deeplab v3 and Refinenet.
2. Test for multiple classes using (https://www.cityscapes-dataset.com/).





### Setup
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Implement
Implement the code in the `main.py` module indicated by the "TODO" comments.
The comments indicated with "OPTIONAL" tag are not required to complete.
##### Run
Run the following command to run the project:
```
python main.py
```
**Note** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.

### Submission
1. Ensure you've passed all the unit tests.
2. Ensure you pass all points on [the rubric](https://review.udacity.com/#!/rubrics/989/view).
3. Submit the following in a zip file.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference images from `runs` folder  (**all images from the most recent run**)
 
 ## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).
