# **Project 1 - Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./writeup_images/1-grayscale.jpg "Step 1 - Convert to Grayscale"
[image2]: ./writeup_images/2-blur.jpg "Step 2 - Apply a Gaussian Blur"
[image3]: ./writeup_images/3-edges.jpg "Step 3 - Find edges"
[image4]: ./writeup_images/4-roi.jpg "Step 4 - ROI"
[image5]: ./writeup_images/5-hough.jpg "Step 5 - Hough"
[image6]: ./writeup_images/6-weighted.jpg "Step 6 - Weighted"
[image7]: ./writeup_images/7-hough.jpg "Step 5 - Hough single line"
[image8]: ./writeup_images/8-weighted.jpg "Step 6 - Weighted single line"
[image-before]: ./writeup_images/challenge_before.png "Challenge Video Before"
[image-after]: ./writeup_images/challenge_after.png "Challenge Video After"

---

## 1. Pipeline

My pipeline consists of the following 6 steps:

Step 1 - The image is converted to grayscale
![Step 1 - The image is converted to grayscale][image1]

Step 2 - A Gaussian blur is applied
![Step 2 - A Gaussian blur is applied][image2]

Step 3 - Canny edge detection is used to find the edges
![Step 3 - Canny edge detection is used to find the edges][image3]

Step 4 - A mask is applied to focus on the region of interest
![Step 4 - A mask is applied to focus on the region of interest][image4]

Step 5 - Hough transform is applied and the lines are drawn
![Step 5 - Hough transform is applied and the lines are drawn][image5]

Step 6 - The output of the previous step is overlaid over the original image
![Step 6 - The output of the previous step is overlaid over the original image][image6]


### Drawing Single Solid lane Lines

The `draw_lines` function was replaced with an updated function `draw_lane_lines` that averages all the lines returned from the Hough transform and draws a single line for each side of the lane.

![Single Solid Lane Lines][image8]

## 2. Shortcomings

One of the main issues I had was the averaged lines occasionally changing direction (gradient) drastically between frames making them jitter in the video.

Another issue experienced with the challenge video was all the noise picked up from the hood being in frame and the shadows cast on the road. 

Some other things that could cause issues are:

* corners or curved lines
* other vehicles on the road could obstruct the lines or add noise to the detected lines
* construction on the road
* missing or faded lines

## 3. Improvements

To fix the issue of shadows on the road and the hood being in frame on the challenge video the `draw_lane_lines` function was updated. The gradient of the lane lines is about 45 degrees most of the time so any lines that are closer to being horizontal are filtered out. 

Challenge video with the original function
![Challenge video with the original function][image-before]

Challenge video with the modified function
![Challenge video with the modified function][image-after]

In order to reduce the jitter of the averaged lines the function could be modified to favor longer lines so if there are lots of short lines they will have less impact on the gradient of the averaged line.
