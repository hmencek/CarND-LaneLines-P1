# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Description of the Pipeline

My pipeline has 5 consecutive steps. The first step is to convert the images to grayscale. The next step is applying Gaussian blur to reduce the noise in the image with a pre-selected kernel size. The third step is to apply Canny Edge Detection algorithm to the image to identify the edges  within the image with sharp color changes. The fourth step of the pipeline is to apply an image mask to crop unnecessary information outside of the region interest. The final step is to apply Hough transform algorithm to the masked image to detect the related line segments for lane lines.

Detected lane line segments are drawn on top of the original image by using "draw_lines()" function. To combine these line segments to have a single solid left & right lanes, I modified the draw_lines() function by firstly calculating the slopes and center points of each line segment. Then I applied a line filter to extract the line segments (slope and center point) with slopes within -25 and -75 degrees for left solid line and +25 and +75 degrees for right solid line.  Then I calculated average slope and center points for left & right respectively to have a single line for each side. The final step is to extrapolate the line so that the lines are starting from the bottom of the image and extend out to the top of the region of interest. Please note that the solid lines are indicated with correct lengths for the test images; however, there is a bug for the videos which shortens the solid line segments.

An example output for these calculations are given below. Please check the "test_images_output" folder to see the outputs of the other example images.

![alt text][./test_images_output/solidWhiteCurve_output.jpg.jpg "Solid White Curve Output"]

I kept "draw_lines()" function as the original and created a new function, namely "draw_lines_modified()". This function also takes input to provide different outputs such that output = 1 generates lines segments and output =2 generates solid lines on the original image.

### 2. Shortcomings with your current pipeline

This pipeline seems to be working correctly for "solidWhiteRight" and "solidYellowLeft" test videos. Please check the output video files to see the performance. Potential problem with this pipeline occurs when there is no sufficient data as in the case of challenge video at 5s. Due to there is no line segments which 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
