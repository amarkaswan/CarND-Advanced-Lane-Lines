# Advanced Lane Finding
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


#### <div style="text-align: justify">  This project aims to write a software pipeline to identify the lane boundaries in a video with distortions, curves, shadows, and different road pavements. The following section briefly describes the steps followed to implement the desired software pipeline. </div>


## Project Steps

The steps of this project are as follows.

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

Now, I will describe the process that I followed for each of the above mentioned objective.

### Camera Calibration Matrix and Distortion Coefficeints

First, I have extracted corners pixels in a set of chessboard images using `cv2.findChessboardCorners()` function and then passed these cornernrs points to `cv2.calibrateCamera()` function for calculating the camera calibration matrix and distortion coefficients. 

### Distortion Correction
In this step, I have used the camera calibration matrix and distortion coefficients to undistort the images. To correct the distortions, I have used 'cv2.undistort()' function. Belowe is an example of a distorted and undistorted image.

### Perspective Transform

The images for camera calibration are stored in the folder called `camera_cal`.  The images in `test_images` are for testing your pipeline on single frames.  


If you want to extract more test images from the videos, you can simply use an image writing method like `cv2.imwrite()`, i.e., you can read the video in frame by frame as usual, and for frames you want to save for later you can write to an image file.  

To help the reviewer examine your work, please save examples of the output from each stage of your pipeline in the folder called `output_images`, and include a description in your writeup for the project of what each image shows.    The video called `project_video.mp4` is the video your pipeline should work well on.  

The `challenge_video.mp4` video is an extra (and optional) challenge for you if you want to test your pipeline under somewhat trickier conditions.  The `harder_challenge.mp4` video is another optional challenge and is brutal!

If you're feeling ambitious (again, totally optional though), don't stop there!  We encourage you to go out and take video of your own, calibrate your camera and show us how you would implement this project from scratch!
