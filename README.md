# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  


The Project Initial Requirements
---

## If you have already installed the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) you should be good to go!   If not, you should install the starter kit to get started on this project. ##

**Step 1:** Set up the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) if you haven't already.

**Step 2:** Open the code in a Jupyter Notebook

Jupyter is an Ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, use terminal to navigate to your project directory and then run the following command at the terminal prompt (be sure you've activated your Python 3 carnd-term1 environment as described in the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) installation instructions!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook. The file contains the code for the pipeline.

*Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

Let's take this test image as an example.

<img src="/test_images_outputs/test images 1.jpg" alt="Test Image">

My pipeline consisted of 6 steps. 

#### 1. First, I converted the images to grayscale.

<img src="/test_images_outputs/grayscale images 1.jpg" alt="Grayscale Image">

#### 2. Then, I applied a Gaussian Blur Filter with the Kernel size of 5 to smooth the noises in the image.

<img src="/test_images_outputs/gaussian blurred iamges 1.jpg" alt="Gaussian Image">

#### 3. After that, I applied Canny Edge Detectetion Technique with the lowest threshold set at 150 and highest at 250 to detect egdes present in the images.

<img src="/test_images_outputs/canny images 1.jpg" alt="Canny Image">

#### 4. Next, I selected a region of interest which is supposed to be a triangle which will focus on finding the lanes only in a specific region of the images.

<img src="/test_images_outputs/selected region images1.jpg" alt="Selected Region Image">

#### 5. Then, I applied Hough Transformation to highlight and draw lines where the lanes are present.

<img src="/test_images_outputs/hough images 1.jpg" alt="Hough Image">

#### 6. At last, I finally superimposed the drawn lines over the original images to detect the lane lines.

<img src="/test_images_outputs/final images 1.jpg" alt="Final Image">


In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I compute all the slope and bias about left and right lines, then I delete some unreasonal results. At last I get the mean of the slopes and bias and I draw a line according to the mean slope and bias.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be robustious, it can only detect the line in the center of the screen.

Another shortcoming could be that it will fail when entering into curve or circumstance becoming complex, it could not detect any line.

Also, it is extremly slow to work on real self-driving cars. C++ can be used to construct one.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change sone hyperparameters to fit with more variety of cases.

Another potential improvement could be to use other Computer Vision and Deep Learning Techniques to further improve its accuracy.

