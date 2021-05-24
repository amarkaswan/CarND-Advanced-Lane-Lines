# Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


#### <div style="text-align: justify">  This project aims to write a software pipeline to identify the lane boundaries in a video with distortions, curves, shadows, and different road pavements. The following section briefly describes the steps followed to implement the desired software pipeline. </div>


## Solution Approach

I have implemented the desired software pipeline with the help of the following eight steps. 

* First, I have computed the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Next, I have applied a distortion correction to the raw image.
* Then, I have used color transforms and gradients to create a thresholded binary image of the undistorted image.
* Next, I have applied a perspective transform to rectify binary image or obtain the <strong>birds-eye view</strong>. Let's call it a warped image.
* <div style="text-align: justify">  After that, I have detected lane pixels in the warped image using the sliding window and search around methods and then obtained the lane lines by fitting second-order polynomials with these pixels. </div>
* Next, I have calculated the curvature of the lane and position of the vehicle from the lane center.
* Then, I have warped the detected lane lines back onto the original image (i.e., raw image). Let's call it an unwarped image.
* Finally, I have printed the lane curvature and position of the vehicle on the unwarped image.

Now, I will describe the steps mentioned above along with related terms as follows. 

### Camera Calibration Matrix and Distortion Coefficeints

<div style="text-align: justify">  <strong>Image Distortion</strong>: Camera captures the 3D objects and transforms them into 2D images. However, when this transform is not perfect, shapes, sizes, orientations, and positions of some objects are changed. This phenomenon is known as image distortion. </div>
<p></p>

<div style="text-align: justify">  <strong>Camera Calibration</strong>: It is the process of finding the parameters to estimate the position of the camera in 3D environment and position of lens and image sensor. These parameters are used to measure and correct the distortion in the captured images. </div>
<p></p>

First, I have extracted corners pixels in a set of chessboard images using `cv2.findChessboardCorners()` function and then passed these cornernrs points to `cv2.calibrateCamera()` function for calculating the camera calibration matrix and distortion coefficients. 

### Distortion Correction
In this step, I have used the camera calibration matrix and distortion coefficients to undistort the images. To correct the distortions, I have used 'cv2.undistort()' function. Belowe is an example of a distorted and undistorted image.

### Perspective Transform

The images for camera calibration are stored in the folder called `camera_cal`.  The images in `test_images` are for testing your pipeline on single frames.  


If you want to extract more test images from the videos, you can simply use an image writing method like `cv2.imwrite()`, i.e., you can read the video in frame by frame as usual, and for frames you want to save for later you can write to an image file.  

To help the reviewer examine your work, please save examples of the output from each stage of your pipeline in the folder called `output_images`, and include a description in your writeup for the project of what each image shows.    The video called `project_video.mp4` is the video your pipeline should work well on.  

The `challenge_video.mp4` video is an extra (and optional) challenge for you if you want to test your pipeline under somewhat trickier conditions.  The `harder_challenge.mp4` video is another optional challenge and is brutal!

If you're feeling ambitious (again, totally optional though), don't stop there!  We encourage you to go out and take video of your own, calibrate your camera and show us how you would implement this project from scratch!
